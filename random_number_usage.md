## "A Two-Level Atom Coupled to a Leaky Cavity"
In quantum mechanics, a two-state system (also known as a two-level system) is a quantum system that can exist in any quantum superposition of two independent (physically distinguishable) quantum states[^1].  The atom is basically described by a two-level quantum system. It has a ground state, let's say $\left| g \right\rangle$ and an excited state $\left| e \right\rangle$. While photons can be contained within the cavity, energy can also escape from it. A limited area with mirrors at either end that permit photons to bounce back and forth is referred to as a `cavity`. Within the cavity, the two-level atom is connected to the electromagnetic field. Energy and data transfer between the atom and the cavity photons is made possible by this interaction.

## About `mcsolve`: Monte Carlo Solver:
Wavefunction simulations from Monte Carlo are utilized to solve quantum systems with `mcsolve`. It can be used to simulate quantum jumps and stochastic processes in open quantum systems with non-deterministic evolution. By selecting stochastic trajectories in accordance with the underlying quantum processes, `mcsolve` offers an approximate solution to the dynamics of the quantum system. Strong system-environment coupling and non-Markovian dynamics are handled by `mcsolve`, in contrast to `mesolve`.
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
4. The system at time `τ` is projected into one of the renormalized states provided by |ψ(t+δt)⟩ = C<sub>n</sub>|ψ(t)⟩ / √(⟨ψ(t)|C†<sub>n</sub>C<sub>n</sub>|ψ(t)⟩) by the subsequent jump. In order to select the matching collapse operator Cn, n must be the lowest integer that satisfies the following conditions:

## References:

[^1]: [Two State Quantum System](https://en.wikipedia.org/wiki/Two-state_quantum_system#:~:text=In%20quantum%20mechanics%2C%20a%20two,a%20system%20is%20two%2Ddimensional.)

[^2]: [Monte Carlo Solver](https://qutip.org/docs/latest/guide/dynamics/dynamics-monte.html)