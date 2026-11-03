## What's New in VQkit v1.3

VQkit v1.3 introduces improvements to phonon post-processing, with a focus on **Grüneisen parameter analysis, numerical stability, and working-directory management** for VASP and Quantum ESPRESSO workflows.

### 1. Acoustic Grüneisen Parameter Averaging

- Calculates and reports RMS Grüneisen parameters for the TA, TA′, and LA acoustic branches.
- **New:** Automatically calculates the arithmetic average of the three acoustic RMS values.
- Displays the average immediately after the individual branch results.
- Saves the results to `VQkit_GRUNEISEN_ACOUSTIC_RMS.txt`.

Example output:

```text
Phonon branches: 24

TA     6.017555045  (N=357)
TA'    4.728381344  (N=357)
LA    19.150508066  (N=357)

Average acoustic Gruneisen = 9.965481485
```

### 2. Improved Grüneisen Parameter Numerical Stability

- Excludes numerically unstable acoustic modes at the Γ point.
- Filters near-zero-frequency and invalid modes.
- Applies a configurable extreme-value threshold, with a default of |γ| > 20.
- Preserves original input files.
- Generates filtered results and reports excluded data points with their corresponding reasons.

### 3. Working-Directory Improvements

- Supports absolute and relative paths.
- Accepts Windows paths with or without quotation marks.
- Handles directory names containing spaces.
- Improves file-location error messages during phonon analysis.

### 4. Scientific Considerations

The reported acoustic average is the arithmetic mean of the three branch-resolved RMS Grüneisen parameters, not the signed thermodynamic Grüneisen parameter.

The numerical filtering threshold is intended to reduce artifacts caused by near-zero phonon frequencies. Genuine soft phonon modes and unusually large Grüneisen parameters require additional physical validation.

### Installation

Install the VQkit v1.3 universal Python wheel:

```bash
python -m pip install --upgrade --force-reinstall vqkit-1.3-py3-none-any.whl
```

Verify the installation:

```bash
vqkit version
```

Expected output:

```text
VQkit 1.3
```

### Compatibility

- VASP and Quantum ESPRESSO post-processing workflows
- Windows and Linux, subject to Python dependency compatibility
- Universal Python wheel (`py3-none-any`)

**Note:** The universal wheel contains Python source code and is not a source-protected distribution.



## What's new in v1.2

**Orbital Occupancy Analysis** is available as **Post-processing → Electronic Structure → [7] Orbital occupancy**.

- Atom-by-atom projected occupancy output for available `s`, `px`, `py`, `pz`, `ptot`, `dz2`, `dx2-y2`, `dxy`, `dyz`, `dxz`, and `dtot` channels.
- Spin-resolved projected occupancies when the corresponding DOS data are available.
- CSV output with one row per atom and `NA` for unavailable projections.
- VASP: use the Fermi energy recorded in the **original DOSCAR** and align the raw DOS energy axis exactly once.
- Quantum ESPRESSO: read the Fermi energy from `scf.out` and align compatible `projwfc.x` PDOS energies before integration.

The integration is performed over occupied orbital-projected DOS up to the Fermi level. These values are *projected occupancies*, not unique atomic electron counts; they depend on projection conventions and calculation settings.

## Installation from a locally downloaded wheel

Use a **wheel built for your platform**. The universal Python wheel includes Python source files. Compiled Linux wheels are not compatible with native Windows PowerShell.

### Windows PowerShell — universal Python wheel

```powershell
py -m venv vqkit_env
.\vqkit_env\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install .\vqkit-1.2-py3-none-any.whl
vqkit version
vqkit
```

### Linux — universal Python wheel

```bash
python3 -m venv vqkit_env
source vqkit_env/bin/activate
python -m pip install --upgrade pip
python -m pip install ./vqkit-1.2-py3-none-any.whl
vqkit version
vqkit
```

The example assumes the wheel is in the current directory.
## Orbital occupancy: Fermi reference

For raw VASP DOSCAR energies, `E_aligned = E_DOSCAR - E_F(DOSCAR)`. 
For QE, the SCF Fermi energy must be referenced consistently with the PDOS-generating calculation. 

## Development and source protection

The source-code developer package is intended for private storage. The `py3-none-any` wheel contains readable Python modules; distributing it does not hide the source. The compiled Linux wheel is a separate, platform-specific build.

Project website: https://vqkit.com
