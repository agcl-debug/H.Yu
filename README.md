[README.md](https://github.com/user-attachments/files/35132110/README.md)
# Ecological space evolution and ecosystem function assessment in the Yellow River Source Region

Reproduction package for the manuscript *“Ecological Space Evolution and Ecosystem Function Assessment
Based on Landscape Ecological Risk and Ecological Network Analyses in the Yellow River Source Region”*
(submitted to *Remote Sensing*).

The package contains the analysis code, all model parameter tables, the ESCI results used in Section 3.4,
and a manifest of the input data, so that the reported figures and tables can be verified end to end.

## Contents

| Folder | Description |
|---|---|
| `00_docs/` | Reproduction manuals, environment specification and expected-result benchmarks (Chinese) |
| `01_code/` | Python pipeline: `s01_prepare.py` … `s10_report.py`, plus `common.py`, `geo.py`, `stats.py` |
| `02_parameters/` | Carbon pools, ESCI weighting sensitivity, per-year habitat threat and sensitivity tables |
| `03_results/` | ESCI surface, five-class map, break points and county statistics for the analysis year (2019) |
| `04_manifest/` | File list (path, size, date) of the raw and intermediate inputs, which are not redistributed |

## Reproduce

```bash
# 1. environment (ArcGIS 10.8 / Python 2.7 is used for raster operations in the original run)
pip install -r 00_docs/requirements.txt

# 2. run the pipeline in order
python 01_code/s01_prepare.py
python 01_code/s02_rusle.py
python 01_code/s03_invest.py
python 01_code/s04_trend.py
python 01_code/s05_omgd.py
python 01_code/s06_leri.py
python 01_code/s07_network.py
python 01_code/s08_esci.py      # reproduces the results in 03_results
python 01_code/s09_sdg.py
python 01_code/s10_report.py
```

Input paths and expected outputs are documented in `00_docs/Reproduction_Manual.md`; produced tables can be
checked against `00_docs/Expected_Results_Benchmark.md`.

## Data availability

- Code, parameter tables and ESCI results: this repository.
- Raw inputs (~489 GB) and intermediate products (~116 GB) are not redistributed. Their exact paths, sizes
  and dates are listed in `04_manifest/input_and_process_file_list.csv`, and all sources are public
  (CLCD, CNLUCC, ASTER GDEM, HWSD, NTPDC, SoilGrids, RESDC), so the inputs can be re-assembled.
- The full 2000–2020 annual ESCI series is not shipped; `s08_esci.py` regenerates it.

## Citation

If you use this package, please cite the manuscript:

> Qi, W.; Cheng, Q.; Wang, R.; Wang, W.; Yu, H.; Long, Y.; You, H.; Han, X.; Chen, J. Ecological space
> evolution and ecosystem function assessment based on landscape ecological risk and ecological network
> analyses in the Yellow River Source Region. *Remote Sensing* (submitted).

## License

Code: MIT. Data and documents: CC BY 4.0.
