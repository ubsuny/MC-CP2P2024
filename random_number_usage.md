## "A Two-Level Atom Coupled to a Leaky Cavity"
In quantum mechanics, a two-state system (also known as a two-level system) is a quantum system that can exist in any quantum superposition of two independent (physically distinguishable) quantum states[^1].  The atom is basically described by a two-level quantum system. It has a ground state, let's say $\left| g \right\rangle$ and an excited state $\left| e \right\rangle$. While photons can be contained within the cavity, energy can also escape from it. A limited area with mirrors at either end that permit photons to bounce back and forth is referred to as a `cavity`. Within the cavity, the two-level atom is connected to the electromagnetic field. Energy and data transfer between the atom and the cavity photons is made possible by this interaction.

## About `mcsolve`: Monte Carlo Solver:
Wavefunction simulations from Monte Carlo are utilized to solve quantum systems with `mcsolve`. It can be used to simulate quantum jumps and stochastic processes in open quantum systems with non-deterministic evolution. `Random Numbers` are very crucial parts of this project, but instead of mannual generation, they are being internally developed by `mcsolve`. By selecting stochastic trajectories in accordance with the underlying quantum processes, `mcsolve` offers an approximate solution to the dynamics of the quantum system. Strong system-environment coupling and non-Markovian dynamics are handled by `mcsolve`, in contrast to `mesolve`.
The Monte Carlo (MC) approach, also known as the quantum-jump approach to wave function evolution, allows one to simulate an individual realization of the dynamics of the system, while the density matrix formalism represents the ensemble average over many identical realizations of a quantum system. Here, the environment is continuously observed, causing the system wave function to undergo a sequence of quantum jumps that are dependent on the amount of knowledge the environmental measurements provide about the system's current state[^2]. The Evolution is generally governed by the Schrödinger equation with a non-Hermitian effective Hamiltonian:
<center>

H<sub>eff</sub> = H<sub>sys</sub> - iℏ/2 ∑<sub>i</sub> C<sup>+</sup><sub>n</sub>C<sub>n</sub>

</center>


## Random Numbers Usage in the Project
This project is aimed to simulate `A Two-Level Atom Coupled to a Leaky Cavity`, with `Monte Carlo` approch using `QuTip`. This kind of simulation is stochastic rather than precise, and hence, in quantum Monte Carlo simulations (`mcsolve`), random numbers are utilized to describe the stochastic evolution of a quantum system.

It takes a lot of work to evaluate the MC evolution to the first order of time. Rather, QuTiP simulates a single implementation of a quantum system using the subsequent procedure. Commencing with a pure state |ψ⟩:

1. Select a random value, r<sub>1</sub>, between 0 and 1 to indicate the likelihood that a quantum jump will happen.
2. Pick a random value (r<sub>2</sub>) between 0 and 1 to determine which collapse operator caused the jump.
3. Utilizing the effective Hamiltonian, integrate the Schrödinger equation until a time `τ` is reached when the wave function's norm satisfies ⟨ψ(τ)|ψ(τ)⟩=r<sub>1</sub>, marking the jump's occurrence.
4. The system at time `τ` is projected into one of the renormalized states provided by |ψ(t+δt)⟩ = C<sub>n</sub>|ψ(t)⟩ / √(⟨ψ(t)|C†<sub>n</sub>C<sub>n</sub>|ψ(t)⟩) by the subsequent jump. In order to select the matching collapse operator C<sub>n</sub>,  n must be the lowest integer that satisfies the condition:
$∑_{i=1}^{n}P_{n}(τ) ≥ r_{2}$, whose left hand side is by definition normalized to unity.

Where P<sub>n</sub> can be calculated using: P<sub>i</sub>(t) = ⟨ψ(t)|C<sup>+</sup><sub>i</sub>C<sub>i</sub>|ψ(t)⟩ / δp

5. By selecting a new random number, repeat the above process until the final simulation time is achieved, using the renormalized state from the previous step as the new initial condition at time τ . 

## Code Snippets:
The visualization of this code can be done in [monte_carlo_qutip.ipynb](https://github.com/ubsuny/MC-CP2P2024/blob/main/monte_carlo_qutip_.ipynb)
```python
import numpy as np
import matplotlib.pyplot as plt
from qutip import *

times = np.linspace(0.0, 10.0, 200)
psi0 = tensor(fock(2, 0), fock(10, 5))
a  = tensor(qeye(2), destroy(10))
sm = tensor(destroy(2), qeye(10))

H = 2*np.pi*a.dag()*a + 2*np.pi*sm.dag()*sm + 2*np.pi*0.25*(sm*a.dag() + sm.dag()*a)
data1 = mcsolve(H, psi0, times, [np.sqrt(0.1) * a], [a.dag() * a, sm.dag() * sm])
psi1 = tensor(fock(2, 0), coherent(10, 2 - 1j))
opts = Options(rhs_reuse=True) # Run a second time, reusing RHS
data2 = mcsolve(H, psi1, times, [np.sqrt(0.1) * a], [a.dag() * a, sm.dag() * sm], options=opts)

plt.figure()
plt.plot(times, data1.expect[0], times, data1.expect[1], lw=2)
plt.plot(times, data2.expect[0], '--', times, data2.expect[1], '--', lw=2)
plt.title('Monte Carlo time evolution')
plt.xlabel('Time', fontsize=14)
plt.ylabel('Expectation values', fontsize=14)
plt.legend(("cavity photon number", "atom excitation probability"))
plt.show()
```
During the Monte Carlo simulations, the `mcsolve` function itself generates the random numbers. The master equation, also known as the stochastic Schrödinger equation, for the quantum system is solved by the `mcsolve` function. A collection of random quantum trajectories represents the quantum system's evolution. Quantum jumps cause the quantum state to evolve stochastically at every time step in the simulation. The `mcsolve` function creates random numbers internally in order to replicate these stochastic quantum jumps. By picking random numbers to mimic quantum jumps and fluctuations in the system, the simulations are made stochastic[^6]. 

 ### Working of State Definitions and Operators (Qobj):
- In the code, `fock(2, 0)` creates a state with no particles (0) in mode 2 and `fock(10, 5)` creates a state with five particles (5) in mode 10[^3]. 
- `coherent(10, 2 - 1j)` creates a coherent state in the atom's mode (mode 10) with a specific amplitude and phase using the coherent operator[^4]. 
- `qeye(2)` creates the identity matrix of size 2, representing the identity operator for the two-level atom in Qutip[^5]. 
- `destroy(10)` creates the lowering operator for the atom (mode 10) using the destroy operator, which can decrease the number of excitations[^5]. 
- `destroy(2)` creates the lowering operator for the cavity mode (mode 2) using the destroy operator[^5]. 
- `sm.dag()` and `a.dag()` are the adjoint (dagger) operators of sm and a, respectively. They represent raising operators, which can increase the number of photons in the cavity and excitations in the atom, respectively[^5].

### Monte Carlo Solver Initialization:
```python
H = 2*np.pi*a.dag()*a + 2*np.pi*sm.dag()*sm + 2*np.pi*0.25*(sm*a.dag() + sm.dag()*a)
```
The Master equation defining the open quantum system (leaky cavity) is numerically solved using the `mcsolve` function from `Qutip` to determine the system's temporal evolution for the supplied Hamiltonian and initial states (`psi0` and `psi1`).
```python
data1 = mcsolve(H, psi0, times, [np.sqrt(0.1) * a], [a.dag() * a, sm.dag() * sm])
```

```python
data2 = mcsolve(H, psi1, times, [np.sqrt(0.1) * a], [a.dag() * a, sm.dag() * sm], options=opts)
```
The `mcsolve` function is invoked twice in these lines to do Monte Carlo simulations. Random numbers are internally used by the `mcsolve` function to sample stochastic processes which are quantum jumps in this case. `np.sqrt(0.1)` represents the strength of the noise, and it is scaled by the annihilation operator to generate random fluctuations in the system.

### Options for Reusing Random Number Generator:
```python
opts = Options(rhs_reuse=True)
```
An `Options` object is created with the `rhs_reuse` parameter set to `True`. With the help of this option, the Monte Carlo solver can reuse the state of the random number generator in between `mcsolve` runs. By reusing the random number generator state, both simulations (`data1` and `data2`) will employ the same random number sequence. This is helpful, for instance, when comparing various initial circumstances or parameter configurations while ensuring that the simulations' random fluctuations remain constant.


## References:

[^1]: [Two State Quantum System](https://en.wikipedia.org/wiki/Two-state_quantum_system#:~:text=In%20quantum%20mechanics%2C%20a%20two,a%20system%20is%20two%2Ddimensional.)

[^2]: [Monte Carlo Solver](https://qutip.org/docs/latest/guide/dynamics/dynamics-monte.html)

[^3]: [Quantum State Functions](https://qutip.org/docs/latest/apidoc/functions.html?highlight=fock)

[^4]: [Qutip Coherent State](https://qutip.org/docs/latest/apidoc/functions.html?highlight=coherent#qutip.states.coherent_dm)

[^5]: [Quantum Objects(Qobj)](https://qutip.org/docs/latest/apidoc/classes.html)

[^6]: [Quantum Monte Carlo Method](http://info.phys.unm.edu/~ideutsch/Classes/Phys581S14/Lectures/Molmer2.pdf)