# VQkit v1.2

> Build carefully. Analyze clearly. Discover confidently.

**VQkit (VASP and Quantum ESPRESSO Interface Kit)** is a command-line pre- and post-processing toolkit for VASP and Quantum ESPRESSO. It supports structure and input preparation, electronic-structure and charge-density analysis, AIMD and NEB workflows, and application-specific materials analysis.

**Lead developer:** RAJKAMAL Anand, PhD

**Contributors:** Prakash Govindaraj, Seunghwan Kwon, Gun Jin Yun, Hern Kim.

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

The example assumes the wheel is in the current directory. These commands do **not** download a wheel from GitHub. See the project distribution channel for release artifacts.

## Orbital occupancy: Fermi reference

For raw VASP DOSCAR energies, `E_aligned = E_DOSCAR - E_F(DOSCAR)`. 
For QE, the SCF Fermi energy must be referenced consistently with the PDOS-generating calculation. 

## Development and source protection

The source-code developer package is intended for private storage. The `py3-none-any` wheel contains readable Python modules; distributing it does not hide the source. The compiled Linux wheel is a separate, platform-specific build.

Project website: https://vqkit.com
