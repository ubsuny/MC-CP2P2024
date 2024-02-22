## Data Type Selection

In this computational project, I am doing the Monte Carlo evolution of **"a two-level atom coupled to a leaky cavity"** with `QuTip`. `Integer` and `floats` are going to be the majority of data types. Simulations of quantum mechanics rely on quantum states. `Complex numbers` are commonly used to describe quantum states in computational quantum mechanics, and they are frequently stored as arrays or matrices. For instance, a column vector with complex elements could be used to depict a qubit's quantum state. In this regard, I might have to select `complex numbers` as one of the essential data types. I might be using `python's` library funtion `cmath` which has in-built function named `complex(a,b)`.Moreover, Hamiltonian can be represented with either of matrices, operators, or functions. Hamiltonian as fucnction is preferable. In `QuTiP`, Hamiltonians are often represented using the `Qobj` data type, which means **Quantum Onjects**.

### Qobj:
It is possible for a `Qobj` to represent mixed or pure quantum states. It is adaptable for simulating a variety of quantum systems, including time-dependent quantum objects.

- To represent the time point, numpy array will be used by utilizing `numpy.ndarray` and `np.linspsce`.
- `Qobj`; quantum onjects will be utilized for quantum state with tensor function and annihilation operators for cavity and atom.
- Within `Qobj`, Operators  and Options classes can be used.
- The expectation values use the list of floating point numbers.
