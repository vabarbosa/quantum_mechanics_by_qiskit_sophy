```python
%matplotlib inline
# Importing standard Qiskit libraries and configuring account
from qiskit import QuantumCircuit, execute, Aer, IBMQ
from qiskit.compiler import transpile, assemble
from qiskit.tools.jupyter import *
from qiskit.visualization import *
# Loading your IBM Q account(s)
provider = IBMQ.load_account()
```

    ibmqfactory.load_account:WARNING:2020-08-01 12:30:27,460: Credentials are already in use. The existing account in the session will be replaced.



```python
from qiskit import QuantumCircuit, execute, Aer
import numpy as np
import matplotlib.pyplot as plt


qc = QuantumCircuit(1) # 1큐빗 양자회로를 만듭니다
initial_state = [0.+1.j/sqrt(2),1/sqrt(2)+0.j] #본문에 설명한 대로 큐빗을 초기화할 값을 설정합니다.
qc.initialize(initial_state, 0) #큐빗의 상태벡터를 정해진 값으로 초기화 합니다.
qc.measure_all()

results =[]

for i in range(1,100):
    backend = Aer.get_backend('statevector_simulator')
    state = execute(qc,backend).result().get_counts() # Execute the circuit
    for key, value in state.items() :
        results += key

plt.plot(results)    
plt.show()
```


![png](output_2_1.png)



```python

```
