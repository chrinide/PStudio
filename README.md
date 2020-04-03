![PStudio logo](/notebooks/pstudio-logo.png)

PseudopotentialStudio (PStudio) aims to become a full fledged
Python package to generate atomic *pseudopotentials* for electronic
structure codes like [Quantum-Espresso](www.quantum-espresso.org).

### Motivation (TL;DR)
Why am I coding this package? There exist several pseudopotential generation
code. Their input files are difficult to write and poorly documented. They
implement different pseudization methods and produce pseudopotentials with
different file formats and poorly documented.

All existing codes are *non interactive*. Typically you have to repeat the
following steps: (1) write the input file (2) run the code
(3) extract data from the output (4) plot the results, until you are
satisfied with the result. PStudio can be run in a Jupyter notebook
and will provide utility functions to plot and analyze the results
interactively.

Finally, the mathematics behind pseudopotential generation is seldom
explained in the details, in the original papers. In most codes, the numerics
(fitting, derivative matching, non-linear system, special functions) is
implemented in Fortran. PStudio instead relies on [NumPy](www.numpy.org) and
[SciPy](www.scipy.org) for the numerical part and on [Matplotlib](www.matplotlib.org)
for visualization. Additionally PStudio uses [LibXC](www.libxc.org) for
exchange and correlation and few Fortran routines from the
[ONCVPSP](http://www.mat-simresearch.com/) code.

### Goals
* generate norm-conserving, ultrasoft and PAW pseudopotentials
* generate pseudo wavefunctions, GIPAW reconstruction, two-electron ERIs
* provide a didactic code to atomic/pseudopotential calculations
* provide a Python library to develop quickly new pseudopotential schemes

### Installation and requirements
PStudio require a Fortran compiler like gfortran. After downloading the code,
the Fortran routines can be built in-place:

```
git clone https://github.com/dceresoli/PStudio
cd PStudio
./build.sh
```

### Usage
Create a new Python3 notebook with [Jupyter](www.jupyter.org) or [nteract](www.nteract.io)
and:
```python
from pstudio import AE

ae = AE('Ti', xcname='LDA', relativity='SR')
ae.run(verbose=True)
...
```

See the directory [notebooks](/notebooks) for further examples.

### License
PStudio includes routines from [ONCVPSP](http://www.mat-simresearch.com/)
and from [GPAW](https://wiki.fysik.dtu.dk/gpaw/). The pyxclib module was
slightly modified from [LibXC](www.libxc.org).
PStudio is distributed under the GNU GPL v3 license.