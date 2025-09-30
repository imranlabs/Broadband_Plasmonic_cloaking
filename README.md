# Broadband Scattering Suppression with Plasmonic Cloaking

## Overview
This repository contains a Jupyter Notebook (`Broadband_Scattering_Suppression.ipynb`) that simulates broadband scattering suppression using a 3D nano-assembled plasmonic meta-structure for plasmonic cloaking. Based on the paper ["Modeling broadband cloaking using 3D nano-assembled plasmonic meta-structures"](https://www.osapublishing.org/oe/fulltext.cfm?uri=oe-28-15-22732&id=433552), the notebook models light interaction with a core-shell structure: a homogeneous dielectric core (e.g., silica) cloaked by a shell of gold nanoparticles (AuNPs).

The simulation combines Foldy-Lax multiple scattering theory with the method of fundamental solutions (MFS) to compute scattering cross-sections and demonstrate up to 50% suppression in the 400-600 nm range for cores up to 900 nm in diameter.

## Features
- Implementation of geometry generation for core and AuNP shell (random nanoparticle placement based on filling fraction).
- Computation of Rayleigh scattering parameters and MFS for dielectric core scattering.
- Simulation of multiple scattering in the AuNP shell using modified Foldy-Lax theory.
- Visualization of normalized scattering cross-sections across the visible spectrum (400-750 nm).
- Support for customizable parameters: core diameter, nanoparticle diameter, shell filling fraction, and number of MFS points.
- Handles high filling fractions (up to ~0.3) for extended suppression up to ~650 nm.

## Repository Structure
```text
├── Broadband_scattering_Suppression.ipynb      # Main Jupyter notebook
├── src/
│   ├── Geometry.py                             # Geometry-related functions
│   └── Mfs.py                                  # Method of Fundamental Solutions
├── data/
│   └── optical_constants/
│       └── 20nm_gold_film_silica.csv           # Refractive index data
├── results/
│   ├── data/                                   # Output CSV files
│   └── figures/                                # Generated plots
└── README.md
```
## Requirements
- Python 3.8 or higher
- Jupyter Notebook
- Dependencies:
  - numpy
  - pandas
  - matplotlib
  - tqdm (for progress bars during computation)

Install dependencies using:
```bash
pip install numpy matplotlib tqdm pandas
```

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/[your-username]/[your-repo-name].git
   ```
2. Navigate to the project directory:
   ```bash
   cd [your-repo-name]
   ```
3. Ensure the data file `data/optical_constants/20nm_gold_film_silica.csv` is present (contains wavelength, refractive index, extinction coefficients for AuNPs and silica).
4. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

## Usage
1. Open `Evaluate_scattering_suppression.ipynb` in Jupyter.
2. Run the cells sequentially:
   - The notebook loads optical constants from CSV.
   - It defines geometry and MFS functions.
   - The `main()` function simulates scattering for a default configuration (690 nm core, 20 nm AuNPs, 20% filling fraction).
3. Customize parameters in the `main()` function (e.g., `CoreDia`, `NPDia`, `Vff`) and re-run for different scenarios.
4. The simulation outputs a plot saved to `figures/scattering_suppression.png` showing bare core vs. core-shell scattering suppression.

**Note:** Simulations with high filling fractions (Vff >= 0.20) may take significant time due to multiple scattering computations.

## Example
```python
# Default parameters in main()
CoreDia = 690.0  # Core diameter (nm)
NPDia = 20.0     # Nanoparticle diameter (nm)
Vff = 0.20       # Shell volume filling fraction
M = 512          # Number of MFS points

# After running, view the generated plot:
# figures/scattering_suppression.png
```

This plots normalized scattering cross-sections (σ_s / σ_g) vs. wavelength, demonstrating broadband suppression.

## Data
- Optical constants: `data/optical_constants/20nm_gold_film_silica.csv` (wavelength, AuNP refractive index, extinction, silica refractive index).
- Source: Experimentally verified values for 20 nm gold film on silica.

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests for improvements, bug fixes, or extensions (e.g., vector wave support or additional materials).

## Citation
If you use this notebook or code, please cite:

Imran Khan *et al.*, “Modeling broadband cloaking using 3D nano-assembled plasmonic meta-structures” *Optics Express*, 28(15), 22732–22749 (2020).  
Link: https://www.osapublishing.org/oe/fulltext.cfm?uri=oe-28-15-22732&id=433552

## License
This project is licensed under the [MIT License](LICENSE).
