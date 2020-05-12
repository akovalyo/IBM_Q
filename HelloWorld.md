# Hello World!
*Simplest program which builds quantum circuit and creates entanglement between 2 qubits*

1. Import library
```python
import qiskit
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
4. Build circuit of quantum and classical bit
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
7. 2 qubit operation = logical "if"
```python
circuit.cx(qr[0], qr[1])
```
8. Measure qubit and store result into the classical bits
```python
circuit.measure(qr, cr)
```
9. Run circuit
  * **First run simulation localy on the computer**
    * Use error component and execute circuit and get result
    ```python
    simulator = Aer.get_backend('qasm_simulator')
    result = execute(circuit, backend = simulator).result()
    ```
    * Import visualization tool and show result
    ```python
    from qiskit.tools.visualization import plot_histogram
    plot_histogram(result.get_counts(circuit))
    ```
  
  * **Send to the quantum computer**
    * Load account
    ```python
    IBMQ.load_account()
    ```
    * Choose the device on which to run code
    ```python
    provider = IBMQ.get_provider('ibm-q')
    qcomp = provider.get_backend('ibmq_16_melbourne')
    ```
    * Create task
    ```python
    job = execute(circuit, backend=qcomp)
    ```
    * Send task to qcomp
    ```python
    from qiskit.tools.monitor import job_monitor
    job_monitor(job)
    ```
    * Get result
    ```python
    result = job.result()
    plot_histogram(result.get_counts(circuit))
    ```
