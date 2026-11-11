
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
## Important Note for Teammates and Reviewers

Both dashboards currently run locally and are not hosted online. The `localhost` links will only work on the laptop where the dashboard servers are running.

To run the dashboards on your own laptop:

1. Clone or download the complete `log-dashboard` GitHub repository, including the `streamlit-mvp` folder. Until the pull request is merged, use the `feature/streamlit-dashboard` branch.
2. Install Python and open a terminal in the main `log-dashboard` project directory.
3. Install the required dependencies:

   ```bash
   python -m pip install -r requirements.txt
   python -m pip install streamlit plotly
   ```

4. Ensure the BETH dataset is available in `data/beth/` and generate the baseline:

   ```bash
   python -m src.triage benchmark --data-dir data/beth --out artifacts --dashboard-dir dashboard
   ```

5. **To run the interactive Streamlit dashboard**, execute:

   ```bash
   python -m streamlit run streamlit-mvp/app.py
   ```

   Open http://localhost:8501.

6. **To run the original BETH Risk Triage dashboard**, open another terminal in the main project directory and execute:

   ```bash
   python -m http.server 8000 --directory dashboard
   ```

   Open http://localhost:8000.

**Important:** Keep the terminal windows open while using the dashboards. Each dashboard runs on its own port, and both can run simultaneously.

These are local development dashboards. The links cannot be opened directly from another laptop unless the project is set up and running on that laptop or configured for network access.


