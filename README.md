# VQkit v1.1
> Build carefully. Analyze clearly. Discover confidently.

**About VQkit**

**VQkit** is a unified command-line toolkit for **VASP** and **Quantum ESPRESSO**, designed to streamline computational materials science workflows by automating input preparation, structure conversion, electronic-structure and charge-density analysis, ab initio molecular dynamics (AIMD), nudged elastic band (NEB) calculations, and specialized analyses for batteries, catalysis, mechanical properties, and phonon-related descriptors.


**Lead Developer:** RAJKAMAL Anand, PhD [1]

**Contributors:** Dr. Prakash Govindaraj [2], Seunghwan kwon [1], Prof. Gun Jin Yun [1], Prof. Hern Kim [2]

**Affiliation:** [1] Seoul National University, Gwanak-gu. [2] Myongji University, Yongin-si. 



## Installation

VQkit requires Python 3.9 or newer.

```bash
cd VQkit_v1.1_Software_Package
python3 -m venv vqkit_env
source vqkit_env/bin/activate
python -m pip install --upgrade pip setuptools wheel
python -m pip install --upgrade installable/vqkit-1.1-py3-none-any.whl
hash -r
vqkit version
vqkit
```

Expected version:

```text
VQkit 1.1

## Windows PowerShell installation

On Windows, use `python` or the Windows Python launcher `py`. The command `python3` is not always
registered on Windows.

First check which command is available:

```powershell
python --version
```

If that is not recognized, try:

```powershell
py --version
```

Create and activate a virtual environment with one of these forms:

```powershell
python -m venv vqkit_env
.\vqkit_env\Scripts\Activate.ps1
```

or:

```powershell
py -m venv vqkit_env
.\vqkit_env\Scripts\Activate.ps1
```

Then install VQkit:

```powershell
python -m pip install --upgrade pip setuptools wheel
python -m pip install --upgrade .\installable\vqkit-1.1-py3-none-any.whl
vqkit version
vqkit
```

Expected version:

```text
VQkit 1.1 For more information https://vqkit.com
```
```Main Interface text
========================================================================================
                                        V Q k i t
                         UNIFIED VASP + QUANTUM ESPRESSO TOOLKIT
----------------------------------------------------------------------------------------
                           Lead Developer : RAJKAMAL Anand, PhD
                                   Version        : 1.1
----------------------------------------------------------------------------------------
                     Build carefully. Analyze clearly. Discover confidently.


 What would you like to do?

   [1] Pre-processing
       Prepare a DFT calculation

   [2] Post-processing
       Analyze a DFT calculation

   [3] Change working directory
       Switch the active folder for this VQkit session

   [0] Exit


## Smart Command Interface

VQkit 1.1 adds an offline Smart Command Interface. The numbered menus remain available, but users
can jump directly to common workflows by typing requests such as eg., generate kpoints,
convert cif, freeze, neb, gruneisen, aimd ect.

The parser is deterministic and local: no internet connection, API key, or external AI service
is required. Smart commands dispatch to the existing tested VQkit workflows rather than generating
scientific inputs independently.
At the main menu, choose `[4] Smart command`, or type a recognized command directly instead of a menu number.


## Current preprocessing menu

===== CALCULATION SETUP =====
[1]  Create a new calculation
[2]  Convert CIF to input file
[3]  Convert output file to input

===== STRUCTURE EDITING =====
[4]  Freeze / fix atoms
[5]  Delete atoms

===== VALIDATION =====
[6]  Pre-flight calculation check

===== PSEUDOPOTENTIALS =====
[7]  Create POTCAR from POSCAR
[8]  Pseudopotential library setup

===== RECIPROCAL SPACE / CONVERGENCE =====
[9]  Generate band-structure K-path
[10] K-points
[11] Convergence tests

===== REACTION-PATH PREPARATION =====
[12] Generate NEB intermediate images


For more information www.vqkit.com
