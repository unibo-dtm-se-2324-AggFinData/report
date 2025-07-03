---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment

This section is for what operations which are needed to make the software work on the users' machine.

---

## User Installation

Application can be run locally by cloning the GitHub repository or installing directly from PyPI.
Two installation options supported:
- **From source (GitHub)**: for development and contribution
- **From PyPI**: for production usage



- app can be installed as Python package from PyPI using `pip install aggfindata` (after public deployment)

### Requirements

- Python 3.10 or higher
- pip (Python package manager)
- Git (optional, for cloning the repository)
- `make` (optional but recommended for automation)
- `coverage.py` (for code coverage during tests)


### Installation Steps
Users can install the app either by cloning the repository or by installing the PyPI package (if published).

#### Option 1: Install from GitHub (development)

1. Clone the repo:
   ```bash
   git clone https://github.com/unibo-dtm-se-2324-AggFinData/artifact.git
   cd artifact
   ``` 
2. Install dependencies with `pip install -r requirements.txt`
3. Set environment variables and run with `flask run`

#### Option 2: From PyPI (production install)
1. Run:
   ```bash
   pip install aggfindata
   ```
2. Set environment variables (NEWS_API_KEY, etc.)

3. Run app using:
    ```bash
    python -m AggFin
    ```

### Server-Side Installation
This app can also be deployed on a server or cloud platform(like: Render, Heroku, etc.).
- You can automate setup through:
  - `Makefile` for Linux/macOS (includes install, test, check, run commands)
  - `setup.ps1` for Windows PowerShell users

**Requirements on the Server:**

Python 3.x
pip
Gunicorn or similar WSGI server
Optional: nginx as reverse proxy(HTTPS)

## Developer Automation

To faster development and testing, the project includes automation scripts:

- `Makefile` — defines commands:
  - `make install` → install dependencies
  - `make test` → run tests
  - `make run` → run the app
  - `make check` → check for syntax errors

- `setup.ps1` — a Windows PowerShell script with same purpose

It allows developers to set up and test project with single command, improving onboarding and DevOps flow.





