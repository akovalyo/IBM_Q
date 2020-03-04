# IBM Q

## [Qiskit](https://qiskit.org/)

#### [Installation](https://github.com/Qiskit/qiskit-iqx-tutorials/blob/master/INSTALL.md)

#### Run

* Open notebook
```
jupyter notebook
```

* Menu -> New notebook -> python3

* 
```python
import qiskit
```

* Add credentials to Qiskit
```python
from qiskit import IBMQ
IBMQ.save_account('MY_API_TOKEN')
```

* Load credentials
```python
from qiskit import IBMQ
IBMQ.load_account()
```
