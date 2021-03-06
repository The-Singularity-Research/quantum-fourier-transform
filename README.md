# Quantum Fourier Transform

The **Quantum Fourier Transform** along with the **phase estimation algorithm** are the key components to Shor's factoring algorithm and many other quantum algorithms that can be used to solve problems such as factoring numbers. Due to its application to cryptography, Shor's algorithm and the Quantum Fourier Transform have been the subject of extensive research. In particular, it is exponentially faster than any known classical algorithm and therefore poses a potential threat to RSA public key cryptography. A paper published by Google ["How to factor 2048 bit RSA integers in 8 hours using 20 million noisy qubits"](https://arxiv.org/pdf/1905.09749.pdf), shows one way to do this. For a general overview of the method, see the [MIT Technology Review Article](https://www.technologyreview.com/2019/05/30/65724/how-a-quantum-computer-could-break-2048-bit-rsa-encryption-in-8-hours/). 

## "Quantum Supremacy"

With recent advances in quantum computing and Google's claims of ["Quantum Supremecy"](https://www.nature.com/articles/s41586-019-1666-5), such algorithms may be implemented much sooner than originally expected. Another important fact to keep in mind is that finding efficient ways to simulate such algorithms may provide a way to run them using classical computers even before the quantum technology is more wide spread. This interactive notebook covers the Quantum Fourier Transform, the Phase Estimation Algorithm, and Shor's Algorithm. It shows an implementation of these algorithms in IBM's Qiskit, and has exercises and examples for practice. 

## Phase Estimaton

The **Phase Estimation Circuit** on four qubits can be seen below. 

![Phase Estimation Circuit](phase_estimation2.png)

This quantum circuit diagram was rendered using [quantikz](https://ctan.org/pkg/quantikz?lang=en), a TikZ library. If you are a Donald Knuth fan and love LaTeX too, check it out! 

## Quantum Fourier Transform in Qiskit

The basic Qiskit Code to generate a Quantum Fourier Transform on four qubits is:

```python
from qiskit import *
%matplotlib inline

q = QuantumRegister(4)

qc = QuantumCircuit(q)
#-------------------
qc.h(0)
qc.cu1(pi/2,q[1],q[0])
qc.cu1(pi/4,q[2],q[0])
qc.cu1(pi/8,q[3],q[0])
#-------------------
qc.barrier()
qc.h(1)
qc.cu1(pi/2,q[2],q[1])
qc.cu1(pi/4,q[3],q[1])
#-------------------
qc.barrier()
qc.h(2)
qc.cu1(pi/2,q[3],q[2])
#-------------------
qc.barrier()
qc.h(3)
#-------------------
qc.draw(output='mpl')
```

The **Quantum Fourier Transform** implemented in IBM's Qiskit can be seen below. 

![Quantum Fourier Transform Circuit](QFT_circuit.png)

## The Notebook

In the notebook you will find Python functions that have been defined to generate the phase estimation and quantum Fourier transform on an arbitrary number of qubits. 

[Interactive Jupyter Notebook on Binder](https://mybinder.org/v2/gh/The-Singularity-Research/quantum-fourier-transform/8d8c46894fa7b00bf12bd2321cbea4ee31a2a01a?filepath=quantum_fourier.ipynb)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/The-Singularity-Research/quantum-fourier-transform/master?filepath=quantum_fourier.ipynb)

### Interested in contributing to this project? 

- Reach out via email to: thesingularity.research@gmail.com
- Be sure to include "Hacking the Universe" in the subject line, so that the email doesn't get overlooked. 
- Write a paragraph or two about how you would like to contribute.
- Ask to Join the Discord server. 
- Ask to Join the Slack Channel.

This is course material for a course on linear algebra and mathematical prerequisites for quantum computing. It contains Jupyter notebooks that can be downloaded as part of the course or opened in Binder as an online interactive notebook. 

[Become a Sponsor of The Singularity](https://github.com/sponsors/The-Singularity-Research)



