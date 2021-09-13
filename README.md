These are the steps to needed to compile the Neutrino Solver using pybind11 in a virtual environment assuming usage on lxplus.


Source a python 3 environment
```
scl enable rh-python38 bash
```

Create the virtual environment first by running
```
python -m venv my_env
source my_env/bin/activate
```

Install pybind (and numpy for checking output)
```
pip install pybind11
pip install numpy
```

Add the virtual environment to the PYTHONPATH
```
export PYTHONPATH="$WORKINGDIR/my_env/lib/python3.8/site-packages:$PYTHONPATH"
```

From within the 'compiled' directory, compile the hpp and cpp files to create the pynusolver.so file
```
bash compile.sh
```

Then test the resulting file with the following inputs
```
python
import numpy as np
import pynusolver
jets = np.array([-38.31093216,   2.88590097, -97.31715393, 104.89573669])
lepton = np.array([-119.2567749 ,  -22.68565369, -136.70018005,  182.82168579])
met = np.array([-232.88529968,  -85.29122162])
nu = np.zeros(4)
pynusolver.run_nu_solver(lepton, jets, met, nu)
```
The resulting nu vector should be
```
array([ -382.65887115,  -119.84833506,  -266.69686505, 23626.31680084])
```
