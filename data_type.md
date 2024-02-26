## Data Type Selection

In this computational project, I am doing the Monte Carlo evolution of **"a two-level atom coupled to a leaky cavity"** with `QuTip`. `Integer` and `floats` are going to be the majority of data types. Simulations of quantum mechanics rely on quantum states. `Complex numbers` are commonly used to describe quantum states in computational quantum mechanics, and they are frequently stored as arrays or matrices. For instance, a column vector with complex elements could be used to depict a qubit's quantum state. In this regard, I might have to select `complex numbers` as one of the essential data types. I might be using `python's` library funtion `cmath` which has in-built function named `complex(a,b)`.Moreover, Hamiltonian can be represented with either of matrices, operators, or functions. Hamiltonian as fucnction is preferable. In `QuTiP`, Hamiltonians are often represented using the `Qobj` data type, which means **Quantum Onjects**.

### Qobj:
It is possible for a `Qobj` to represent mixed or pure quantum states. It is adaptable for simulating a variety of quantum systems, including time-dependent quantum objects. Here is the reference to `QuTip Documentation` with `Qobj`:
[Qutip Documentation](https://qutip.org/docs/latest/apidoc/classes.html)

- To represent the time point, numpy array will be used by utilizing `numpy.ndarray` and `np.linspsce`.
- `Qobj`; quantum onjects will be utilized for quantum state with tensor function and annihilation operators for cavity and atom.
- Within `Qobj`, Operators  and Options classes can be used.
- The expectation values use the list of floating point numbers.

### Example Usage: Python annotation:
```python
from typing import List, Union
import numpy as np
import qutip as qt

def evolve_system(time_points: np.ndarray,
                   initial_state: qt.Qobj,
                   hamiltonian: Union[np.ndarray, qt.Qobj, callable]) -> List[float]:
    """
    Evolves the quantum system over time using a given Hamiltonian.

    Parameters:
        time_points (np.ndarray): Array of time points.
        initial_state (qt.Qobj): Initial quantum state of the system.
        hamiltonian (Union[np.ndarray, qt.Qobj, callable]): Hamiltonian of the system,
            represented as a numpy array, Qobj, or a function.

    Returns:
        List[float]: List of expectation values of observables at each time point.
    """
```
