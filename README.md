These are the steps to needed to compile the Neutrino Solver using pybind11 in a virtual environment


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

```
c++ -O3 -Wall -shared -std=c++11 -fPIC $(python -m pybind11 --includes) *.cpp -o pynusolver.so
```
