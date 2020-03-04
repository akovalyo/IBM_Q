# Hello World!

1. Import library
```python
from qiskit import *
```
2. Build 2 quantum cirquit
```python
qr = QuantumRegister(2)
```
3. Build 2 classical bit
```python
cr = ClassicalRegister(2)
```
4. Build circuit of both
```python
circuit = QuantumCircuit(qr, cr)
```
5. Draw the cirquit
```python
%matplotlib inline
circuit.draw()
```
6. Build up the gates to the cirquit (entanglement)
  * Apply a Hadamard gate onto the first quibit
  ```python
  circuit.h(qr[0])
  ```
  * Draw (to show how it looks like)
  ```python
  circuit.draw(output="mpl")
  ```
7. 2 quibit operation = logical "if"
```python
circuit.cx(qr[0], qr[1])
```
8. Measure quibit and store result into the classical bits
```python
circuit.measure(qr, cr)
```
9. Run circuit
  * Simulate localy on the computer
    * Use error component and execute circuit and get result
    ```python
    simulator = Aer.get_backend('qasm_simulator')
    result = execute(circuit, backend = simulator).result()
    ```
    * Import visualization tool
    ```python
    from qiskit.tools.visualization import plot_histogram
    ```
    * Take result
    ```python
    plot_histogram(result.get_counts(circuit))
    ```
  
  * Send to the quantum computer
