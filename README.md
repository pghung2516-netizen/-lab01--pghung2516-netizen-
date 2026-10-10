# Study Assistant — Starter

A starter repository for the CSC10014 Smart Virtual Assistant project.

## Prerequisites
- Python >= 3.10
- Git

## Setup
Clone the repository and set up the local environment:
```bash
git clone git@github-pghung:pghung2516-netizen/-lab01--pghung2516-netizen-.git
cd -lab01--pghung2516-netizen-
python3 -m venv .venv
source .venv/bin/activate       # On Windows: .venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
pip install -e .
```

## Run
```bash
python -m assistant "where is the training office?"
# Output: Training Office: room I.101, open Mon-Fri 07:30-16:30.
```

## Test
```bash
pytest -q
# Expected output: 4 passed
```

## Project Structure
- `src/assistant/`: Application source code (rule-based assistant backend)
- `tests/`: Automated unit tests (pytest)
- `data/`: Sample data files (e.g., offices.csv)
- `docs/`: Documentation, pair verification worksheets, and logs
- `scripts/`: Helper scripts (check_env.py)
- `ui/`: User interface components (upcoming in Week 7)

## Troubleshooting
- `"No module named assistant"`: Bạn quên chạy `pip install -e .` hoặc môi trường ảo `.venv` chưa được kích hoạt (`source .venv/bin/activate`).
- `PowerShell blocks Activate.ps1` (Windows): Chạy `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` hoặc sử dụng Git Bash.
- `command not found: pytest`: Đảm bảo đã kích hoạt `.venv` và chạy lệnh `pip install -r requirements.txt`.
