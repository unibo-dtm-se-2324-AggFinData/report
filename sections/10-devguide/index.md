---
title: Developer Guide
has_children: false
nav_order: 11
---

# Developer Guide

This is a guide for knowing how new developers can set up the environment and contribute to AggFin project.

---

## Team Contact & Communication

- Maintainer: **Mohammad Jamshidi**
- GitHub: [@MohammadJamshidi99](https://github.com/MohammadJamshidi99)
- Issues, recommandations and bugs should be reported via **GitHub Issues** tab.

---

## Project Structure Overview

```bash
artifact/
│
├── AggFin/                  # Main Flask app package
│   ├── main/                # Homepage & search logic
│   ├── users/               # Registration and login
│   ├── auth/                # Logout/session handling
│   ├── errors/              # Error handlers (404, 500)
│   ├── templates/           # Jinja2 HTML templates
│   └── static/              # CSS, JS, and images
│
├── migrations/              # Flask-Migrate DB scripts
├── instance/                # SQLite DB lives here
├── tests/                   # Unit and integration tests
├── run.py                   # App entry point
├── requirements.txt         # Dependencies
└── .gitignore               # Files to exclude from Git
```

---

## Development Environment Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/unibo-dtm-se-2324-AggFinData/artifact.git
   cd artifact
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # macOS/Linux
   .venv\Scripts\activate     # Windows
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Create a `.env` file**
   ```env
   FLASK_APP=run.py
   FLASK_ENV=development
   NEWS_API_KEY=your_key_here
   ```

5. **Run the app**
   ```bash
   flask run
   ```

---

## Internal Conventions

- **Language**: Python 3.10+
- **Framework**: Flask
- **Code Style**: Follows [PEP 8](https://peps.python.org/pep-0008/)
- **File naming**: lowercase with underscores (e.g., `error_handler.py`)
- **Branch names**: `feature/<feature-name>`, `fix/<bug-name>`
- **Commit style**: lowercase and clear (e.g., "add register route")

---

## Running Tests

Tests are inside the `tests/` directory.

Run all tests:
```bash
pytest
```


## Development Workflow

1. **Create a new branch**
   ```bash
   git checkout -b feature/<feature-name>
   ```

2. **Make changes and commit**
   ```bash
   git add .
   git commit -m "describe your change"
   ```

3. **Push to GitHub**
   ```bash
   git push origin feature/<feature-name>
   ```

4. **Create a pull request** from the GitHub interface

5. Wait for approval and merge into `main`.

---

## Recommended Tools

- **VS Code** or **PyCharm**
- Extensions for Python, Flask, and Git
- GitHub Desktop (optional for GUI-based workflow)
- Flask CLI for managing the app
- Optional: `black` or `flake8` for code formatting

---

> This guide will help new developers to start quickly, understand project's structure, and contribute in an easy way.
