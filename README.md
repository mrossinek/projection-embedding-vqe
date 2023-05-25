# Quantum Embedding Method for the Simulation of Strongly Correlated Systems on Quantum Computers

This repository holds the data related to the paper:

> "Quantum Embedding Method for the Simulation of Strongly Correlated Systems on Quantum Computers"
> Max Rossmannek, Fabijan Pavošević, Angel Rubio, Ivano Tavernelli
> J. Phys. Chem. Lett. 2023, 14, 14, 3491–3497


It is organized as follows:

## The `geoms` folder

This folder holds the input coordinates at the various bond dissociation lengths (`*.inp`) which
were used to compute the initial HF solutions with PySCF.

Furthermore, it contains the output files for various reference calculations done with:

- an exact diagonalization of the Hamiltonian (`*.numpy`)
- a statevector-simulated VQE with a UCCSD ansatz (`*.uccsd`)
- a statevector-simulated AdaptVQE with a UCCSD excitation operator pool (`*.adapt.uccsd`)
- a statevector-simulated AdaptVQE with a qubit operator pool (`*.adapt.qubit`)

And finally, it contains `base.?.json` files which contain the energy offsets due to the projection
embedding.

The number `4` and `6` in the filenames indicate the 4- and 6-orbitals active space, respectively.

## The `FCIDUMP*` folders

These folders contain the FCIDUMP files at various bond dissociation lengths of the fully completed
projection-embedded Hamiltonian, computed with Psi4Numpy based on initial PBE calculations.

The folders suffixed with `_PM` are the results of using a combined Pipek-Mezey localization and
Mulliken population screening rather than the standard SPADE partitioning procedure used in the
other case.

As before, `4e4o` and `6e6o` indicate the 4- and 6-orbitals active space, respectively.

The various output files alongside the actual FCIDUMPs follow the same convention as the data in the
`geoms` folder.

## The `data` and `data_uccsd` folders

Finally, these two folders contain the cleaned input data for the real-device AdaptVQE
simulations. The `data_uccsd` folder uses the UCCSD excitation operator pool while the `data` one
uses the qubit operator pool.

Every filename indicates the initial low-level method (`HF`, `DFT`, or `DFTPM`), the bond
dissociation distance (`\d.\d`), the active space (`cas4` and `cas6`, resp.), the maximum number of
iterations (`iter\d+`) as well as the eigenvalue convergence threshold of the AdaptVQE
(`thres\d.\d+`).

Each file then has the final ansatz as obtain by a statevector-simulated AdaptVQE with those
parameters as well as meta- and reference data for the respective calculation.
For those calculations which were actually performed on a real device, the file will contain a
`results` section with the error-mitigated data.

Finally, these data folders also contain the results of the full noisy VQE simulation, following the
same naming pattern but with a `.vqe` suffix instead of `.json`.


[modeline]: # ( vim: set tw=100: )
