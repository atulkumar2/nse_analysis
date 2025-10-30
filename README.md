# NSE Options/Equity Analysis

This workspace contains a Jupyter notebook to analyze NSE equity bhavcopy, security deliverable, and derivatives reports from a local folder and plot charts for a chosen symbol.

## Files

- `notebooks/nse_reports.ipynb` — Main analysis notebook.
- `reports/` — Output CSV and HTML charts are saved here when you export.

## Prerequisites

- Python 3.9+
- Recommended packages: pandas, numpy, pyarrow, plotly, ipywidgets, kaleido, jupyter

## Quick start (VS Code)

1. Open the notebook at `notebooks/nse_reports.ipynb`.
2. Data path setup: this repo uses a repo-local link `data/` that points to your OneDrive data folder. The notebook resolves `DATA_ROOT` as `data/Full Bhavcopy and Security deliverable`.
    - A helper cell in the notebook can create/repair this link automatically on Windows.
    - If you prefer to set it manually, create a junction (admin not required for Junctions):
       - PowerShell:
          - `New-Item -ItemType Junction -Path e:\workspace\nseoptions\data -Target "C:\\Users\\atulk_0o0fet8\\OneDrive\\Finance\\AnalysisStock\\Data"`
       - cmd (as fallback):
          - `mklink /J e:\workspace\nseoptions\data "C:\\Users\\atulk_0o0fet8\\OneDrive\\Finance\\AnalysisStock\\Data"`
    - Non-Windows users: use a directory symlink named `data` pointing to your data folder.
    - You can still hard-set `DATA_ROOT` if you don’t want to use the link.
3. Run cells in order. If imports fail, run the commented `%pip install ...` line in the Imports cell.
4. Use the widgets to pick your symbol and date range. Charts will render inline.
5. To export CSV and interactive HTML charts, run the "Export" cell near the end.

## Notes

- The loader is liberal with column names and will attempt to infer dates from filenames.
- Derivatives OI requires FUTSTK files; if none are present, OI charts will be skipped.
- If your files use different naming conventions, adjust the regex and column picks in the loader cells.

## Data link helper (Windows)

Inside the notebook, there is a small helper cell that:

- Detects the repository root and expected `data` link
- Creates or repairs a Windows Junction from `./data` to your OneDrive data folder
- Falls back to `cmd /c mklink /J` when PowerShell is not available

This keeps paths stable across machines while avoiding committing large datasets to the repo. The `.gitignore` already excludes `data/`.
