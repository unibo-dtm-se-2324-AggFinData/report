---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment

This section is for what operations which are needed to make the software work on the users' machine.

---

## User Installation

Application can be run locally by any user who has Python installed.

- app can be installed as Python package from PyPI using `pip install aggfindata` (after public deployment)

### Requirements

- Python 3.10 or higher
- pip (Python package manager)
- Git (optional, for cloning the repository)

### Installation Steps
Users can install the app either by cloning the repository or by installing the PyPI package (if published).

#### Option 1: From GitHub (development install)
1. Clone the repo
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
Thisapp can also be deployed on a server or cloud platform(like: Render, Heroku, etc.).

**Requirements on the Server:**

Python 3.x
pip
Gunicorn or similar WSGI server
Optional: nginx as reverse proxy(HTTPS)




