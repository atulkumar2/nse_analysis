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
2. Edit the DATA_ROOT path in the first parameters cell. Default is:
   `C:\\Users\\atulk_0o0fet8\\OneDrive\\Finance\\AnalysisStock\\Data\\Full Bhavcopy and Security deliverable\\202510`
3. Run cells in order. If imports fail, run the commented `%pip install ...` line in the Imports cell.
4. Use the widgets to pick your symbol and date range. Charts will render inline.
5. To export CSV and interactive HTML charts, run the "Export" cell near the end.

## Notes

- The loader is liberal with column names and will attempt to infer dates from filenames.
- Derivatives OI requires FUTSTK files; if none are present, OI charts will be skipped.
- If your files use different naming conventions, adjust the regex and column picks in the loader cells.
