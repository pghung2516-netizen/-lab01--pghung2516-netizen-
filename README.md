# Study Assistant — starter

A starter repository for the CSC10014 Smart Virtual Assistant project.

## Setup

Clone the repository and set up the local environment:
```bash
git clone git@github.com:<your-username>/<your-repo-name>.git
cd <your-repo-name>
python3 -m venv .venv
source .venv/bin/activate       # On Windows: .venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
pip install -e .
## Run

python -m assistant "where is the training office?"
# Output: Training Office: room I.101, open Mon-Fri 07:30-16:30.
## Test

pytest -q
# Expected output: 4 passed

## Project structure

- `src/assistant/`: Application source code (rule-based assistant backend)
- `tests/`: Automated unit tests (pytest)
- `data/`: Sample data files (e.g., offices.csv)
- `docs/`: Documentation, pair verification worksheets, and logs
- `scripts/`: Helper scripts (check_env.py)
- `ui/`: User interface components (upcoming in Week 7)
