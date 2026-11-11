
# BETH Risk Triage — Streamlit MVP

This folder contains my contribution to the AIT 670
BETH Risk Triage group project.

## Features

- Interactive Streamlit dashboard
- BETH CSV dataset upload
- Explainable security risk scoring
- High, Medium, and Low risk classification
- Security analyst review queue
- Risk distribution visualization
- CSV results export

## Testing

All 17 automated tests passed during local testing.

## Screenshots

### Interactive Streamlit Dashboard

![Streamlit Dashboard Overview](screenshots/dashboard_overview.jpg)

### Original Security Risk Triage Dashboard

![Original Dashboard](screenshots/original_dashboard.jpg)

## How to Run the Streamlit MVP

Run these commands from the main `log-dashboard` project folder.

### 1. Install Dependencies

```bash
python -m pip install -r requirements.txt
python -m pip install streamlit plotly
```

### 2. Generate the Baseline

The dashboard requires `artifacts/baseline.json`. Generate it using:

```bash
python -m src.triage benchmark --data-dir data/beth --out artifacts --dashboard-dir dashboard
```

Note: The BETH dataset must be available in `data/beth/` before running this command.

### 3. Launch the Dashboard

```bash
python -m streamlit run streamlit-mvp/app.py
```

Open http://localhost:8501 in your browser.

### 4. Analyze Security Events

1. Upload a BETH CSV dataset.
2. Click **Analyze Security Events**.
3. Review the High, Medium, and Low risk classifications.
4. Examine the security analyst review queue and risk score explanations.
5. Download the scored results or analyst review queue as CSV.

### 5. Run Automated Tests

```bash
python -m pytest -q
```

All 17 automated tests passed during local testing.
