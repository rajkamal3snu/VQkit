# VQkit v1.4 – Automatic Calculation Setup and Advanced DOS/PDOS Plotting

VQkit (VASP and Quantum ESPRESSO Interface Kit) v1.4 introduces automated calculation setup, improved Quantum ESPRESSO structure handling, and customizable DOS/PDOS plotting tools. These enhancements simplify preprocessing and post-processing workflows while providing greater control over electronic-structure analysis and visualization.

## What's New in v1.4

### 1. Automatic Calculation Setup

- Automatically detects VASP or Quantum ESPRESSO from available input and output files.
- Generates input files for self-consistent field (SCF), band-structure, density of states (DOS), and projected density of states (PDOS) calculations.
- Extracts structural information from existing calculation outputs.
- Supports automatic QE output-to-CIF-to-SCF structure recovery when sufficient structural information is available.
- Improves lattice-vector extraction and handling of QE crystal structures.
- Generates high-symmetry k-point paths for band-structure calculations when valid structural and symmetry information is available.
- Organizes generated input files into separate workflow directories.
- Identifies incomplete structural information and avoids generating invalid calculation inputs.

### 2. Manual DOS and PDOS Plot Customization

VQkit v1.4 introduces interactive plotting controls for VASP and Quantum ESPRESSO DOS/PDOS analysis.

Users can customize:

- Energy-axis (X) and DOS/PDOS-axis (Y) limits.
- Figure width and height.
- Line widths and visual presentation.
- Legend positioning, including placement outside the plotting area.
- DOS/PDOS curve visibility and presentation where orbital contributions overlap.
- Figure export in PDF, SVG, and high-resolution PNG (600 dpi).

The plotting tools preserve the original calculated data without artificial smoothing and support energy alignment relative to the Fermi level.

### 3. Additional Improvements

- Improved VASP and QE file detection.
- More consistent handling of QE lattice parameters and atomic coordinates.
- Automatic identification of available structural reference files.
- Improved preprocessing menu organization and working-directory navigation.
- Clearer error messages when structural information is incomplete.
- Improved workflow file generation and output-directory organization.

## Distribution Packages

VQkit v1.4 is available in two distributions:

- **With Source Code:** Includes readable Python source files for development and customization.
- **Without Readable Source Code:** Provides a CPython 3.13 bytecode-only package for distribution.

The bytecode-only package requires CPython 3.13 and does not guarantee protection against reverse engineering.

## Installation

Install the appropriate wheel using pip:

```bash
python -m pip install ./vqkit-1.4-py3-none-any.whl
```


## Documentation and Support

Website: https://www.vqkit.com

## Important Notes

VQkit generates and prepares simulation input files but does not execute VASP or Quantum ESPRESSO calculations automatically.

Users should verify structural optimization, pseudopotential selection, computational parameters, and job-submission settings before running calculations.

The QE structure-recovery workflow has undergone parser and synthetic tests; further validation across different QE output formats is ongoing.
