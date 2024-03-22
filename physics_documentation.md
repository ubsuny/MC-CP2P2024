## Time Evolution and Quantum System Dynamics: Monte Carlo Solver with QuTip
Rather than a experimental practice, this project is solely based on theoretical arguments.` Monte Carlo` simulations are frequently used in quantum mechanics to investigate the dynamics of quantum systems with numerical approach, particularly in situations when obtaining precise analytical answers is challenging or impossible. `QuTiP` (Quantum Toolbox in Python) is a robust Python package which is used to simulate open quantum systems. It offers a range of functions for Monte Carlo simulations of quantum dynamics.

## "A two-level atom coupled to a leaky cavity"
A two-level atom coupled to a leaky cavity usually refers to a system in which an energy-leveled atom interacts with an electromagnetic field contained in a cavity that permits energy leakage. This situation is frequently examined within the framework of cavity quantum electrodynamics (QED), which examines the interaction between photons and atoms in cavities.

- The atom is basically described by a two-level quantum system.
- It has a ground state, let's say $\left| g \right\rangle$ and an excited state $\left| e \right\rangle$.
- While photons can be contained within the cavity, energy can also escape from it.

### Description:
Generally, Atoms have discrete energy levels, and a two-level atom refers to an atom with two relevant energy states: a ground state $\left| g \right\rangle$ and an excited state $\left| e \right\rangle$. Photons, usually in the optical or microwave frequency range, can be absorbed or emitted to trigger the transition between these two states[^1]. The system can absorb energy and change from the ground state to the "excited" state if the energy levels are not degenerate, or have unequal energies. An atom will periodically absorb photons from a coherent beam of light and reemit them through stimulated emission. A Rabi cycle is one such cycle, and the system's Rabi frequency is the inverse of its duration[^2]. The probability of finding the atom in the excited state is found from the Bloch equations to be:
 
 $(|c_{b}(t)|^{2} = \sin^{2}(\frac{\omega t}{2}))$,

 where ${\displaystyle \omega }$ is the Rabi frequency.

A cavity, is a confined space between two mirrors that can trap electromagnetic fields, such as photons, within it. These modes are quantized, meaning they can only have certain discrete frequencies and energies. A two-level atom's assymetric charge distribution inside its structure gives it an electric dipole moment.  The two-level atom interacts with the cavity mode via its electric dipole moment. There is a photon-based electromagnetic field inside the cavity. Because of the mirrors at either end, these photons are contained within the cavity and are able to oscillate. The atom gains energy and changes to its excited state as it receives a photon from the electromagnetic field. On the other hand, the atom loses energy and returns to its ground state when it emits a photon. Photons from the electromagnetic field are either absorbed or emitted by the atom as it moves between its excited and ground states. **The energies of the cavity mode (photons), atoms and the interactions, all are governed by the Hamiltonian describing the system.**
The Hamiltonian that describes the full system,

$H=H_{\text{field}}+H_{\text{atom}}+H_{\text{int}}$

consists of the cavity field Hamiltonian, the atomic excitation Hamiltonian, and the Jaynes–Cummings interaction Hamiltonian respectively[^3].


A cavity that is not completely sealed off from its surroundings is referred to as a **leaky cavity**. It causes dissipation and energy loss by allowing photons to leave the cavity. There are a number of ways that photons can leak into the surrounding area, including connection to external waveguides or faulty mirrors. The Hamiltonian of the Jaynes-Cummings interaction represents the coupling term. Their coupling strength determines the strength of the interaction between the cavity mode and the atom. This term plays a role in the energy exchange between two level systems (atoms) and bosonic (cavity mode photons)[^3].

### Observations:
**1. Decoherence:**
As a result of interactions with its surroundings, the quantum system loses its coherence, or capacity to retain superposition states(decoherence). In the case of an atom coupled to a leaky cavity, decoherence might result from the interaction of the atom-cavity system with external influences such as thermal fluctuations, photon leakage, or coupling to other degrees of freedom. Photons that leak out of the cavity or interact with external modes contain information about the atom-cavity system's quantum state. This causes a loss of phase information and coherence in the system[^4].

**2. Dissipation:**
Dissipation is the irreversible loss of energy from a quantum system to its environment. In the case of the atom-cavity system, dissipation is principally caused by photon leakage from the cavity into the surroundings. The leaky cavity allows photons to escape, reducing the energy stored in the cavity mode and increasing the entropy of the surroundings. Dissipation dampens coherent oscillations in the atom-cavity system, such as Rabi oscillations or coherent photon emission, which eventually leads to thermal equilibrium with the environment[^5].

**3. System-Environment Interactions:**
Photon leakage, temperature fluctuations, and coupling to external modes are some of the ways in which the atom-cavity system interacts with its environment.
These interactions can have a significant impact on the dynamics and stability of the system. For example, coupling to external modes can cause energy exchange and entanglement between the atom-cavity system and its surroundings.
System-environment interactions also influence the timeframes and efficiency of quantum processes as photon emission, absorption, and coherent control[^6].







### Applications:
The two-level atom coupled to a leaky cavity is a model system widely used in quantum information processing, quantum communication, and quantum sensing. It serves as a platform for implementing basic quantum operations, such as qubit initialization, gates, and measurement, as well as more advanced protocols like quantum error correction and quantum state transfer.


### NOTE: 
I am keeping references as they are, I will cite properly on the later time. This is just for keeping them safe here, will follow citation formats later on.
### Bibliography:
1. [Monte Carlo Solver](https://qutip.org/docs/latest/guide/dynamics/dynamics-monte.html)
2. [On the simultaneous scattering of two photons by a single two-level atom](https://www.nature.com/articles/s41566-023-01260-7)
3. [An atom in a cavity](https://phys.libretexts.org/Bookshelves/Quantum_Mechanics/Advanced_Quantum_Mechanics_(Kok)/09%3A_New_Page/9.3%3A_An_Atom_in_a_Cavity)
4. [Solving Problems with Time-dependent Hamiltonians](https://qutip.org/docs/latest/guide/dynamics/dynamics-time.html#time)
5. [Cavity Quantum Electrodynamics](https://link.springer.com/chapter/10.1007/978-3-540-34572-5_5)


### References:
[^1]: [Haroche, S., & Raimond, J.-M. (2006). Exploring the Quantum: Atoms, Cavities, and Photons. Oxford University Press. [ISBN: 978-0198509141]](http://math0.bnu.edu.cn/~zhengc/material/macsoft/ebooksclub.org__Exploring_the_Quantum__Atoms__Cavities__and_Photons__Oxford_Graduate_Texts_.pdf)

[^2]: [Rabi cycle/ Oscillation](https://en.wikipedia.org/wiki/Rabi_cycle)

[^3]: [Jaynes-Cummings Model](https://en.wikipedia.org/wiki/Jaynes%E2%80%93Cummings_model)

[^4]: [Zurek, W. H. (2003). Decoherence, einselection, and the quantum origins of the classical. Reviews of Modern Physics, 75(3), 715-775. doi:10.1103/RevModPhys.75.715](https://journals.aps.org/rmp/abstract/10.1103/RevModPhys.75.715)

[^5]: [Gardiner, C. W., & Zoller, P. (2004). Quantum Noise: A Handbook of Markovian and Non-Markovian Quantum Stochastic Methods with Applications to Quantum Optics. Springer. [ISBN: 978-3540223011]](https://books.google.com/books/about/Quantum_Noise.html?id=a_xsT8oGhdgC)

[^6]: [Breuer, H. P., & Petruccione, F. (2002). The Theory of Open Quantum Systems. Oxford University Press. [ISBN: 978-0199213900]](http://info.phys.unm.edu/~ideutsch/Classes/Phys581S23/Reference%20Material%EF%80%A8/Heinz-Peter%20Breuer,%20Francesco%20Petruccione%20-%20The%20Theory%20of%20Open%20Quantum%20Systems.pdf)

