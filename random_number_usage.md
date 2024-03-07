## "A Two-Level Atom Coupled to a Leaky Cavity"
In quantum mechanics, a two-state system (also known as a two-level system) is a quantum system that can exist in any quantum superposition of two independent (physically distinguishable) quantum states[^1].  The atom is basically described by a two-level quantum system. It has a ground state, let's say $\left| g \right\rangle$ and an excited state $\left| e \right\rangle$. While photons can be contained within the cavity, energy can also escape from it. A limited area with mirrors at either end that permit photons to bounce back and forth is referred to as a `cavity`. Within the cavity, the two-level atom is connected to the electromagnetic field. Energy and data transfer between the atom and the cavity photons is made possible by this interaction.

## About `mcsolve`: Monte Carlo Solver:
Wavefunction simulations from Monte Carlo are utilized to solve quantum systems with `mcsolve`. It can be used to simulate quantum jumps and stochastic processes in open quantum systems with non-deterministic evolution. By selecting stochastic trajectories in accordance with the underlying quantum processes, `mcsolve` offers an approximate solution to the dynamics of the quantum system. Strong system-environment coupling and non-Markovian dynamics are handled by `mcsolve`, in contrast to `mesolve`.

## Random Numbers Usage in the Project
This project is aimed to simulate `A Two-Level Atom Coupled to a Leaky Cavity`, with `Monte Carlo` approch using `QuTip`. This kind of simulation is stochastic rather than precise, and hence, in quantum Monte Carlo simulations (`mcsolve`), random numbers are utilized to describe the stochastic evolution of a quantum system.


## References:

[^1]: https://en.wikipedia.org/wiki/Two-state_quantum_system#:~:text=In%20quantum%20mechanics%2C%20a%20two,a%20system%20is%20two%2Ddimensional.