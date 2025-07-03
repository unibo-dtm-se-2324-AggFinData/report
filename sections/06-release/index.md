---
title: Release
has_children: false
nav_order: 7
---

# Release

This section documents the artefacts of AggFin production process, how deployed, and licensing and versioning strategies used.

---

## What to Release

The typical release process of AggFin platform includes:

- **Backend Application**: PFlask application code (routes, models, forms, main, auth, errors, users)application logic.
- **Templates and Static Files**: HTML templates rendered via Jinja2, and static assets(CSS, JS),
- **Requirements**: All dependencies listed in `requirements.txt`.
- **Configuration**: Environment variables such as `NEWS_API_KEY`, which is handled securely using a `.env` file.
- **Database Schema**: The structure defined by SQLAlchemy and managed via Flask-Migrate.
- **Version Metadata**: Stored in `version.py`, injected in Flask config (`app.config['VERSION']`), rendered in frontend ( footer).
- **Dev Scripts**: `Makefile` and `setup.ps1` for local install, tests, and run automation.
- **Advanced Tests**: `test_adv.py` for validating user flows like register, login, and stock search.
- **Packaging Metadata**: Defined in `setup.py` using `setuptools`, includes name, version, and all required dependencies.


---

## Deployment Target

AggFin platform is suitable for deployment on any Python-compatible platform, including:

- **Render**
- **Heroku**
- **Replit**
- **Local server with Gunicorn + Nginx**

### Notes:
- SQLite used for development and for production use, a PostgreSQL or MySQL backend is recommended.
- HTTPS support configured on any public-facing deployment.
- + Project is now published to **PyPI** under name of `aggfindata`, allowing installation via `pip install aggfindata`.

---

## How Are They Released?

Releases are now semi-automated using a GitHub Action CI/CD pipeline. When new version tag is pushed, project will be packaged using `setup.py` and automatically published to PyPI via `twine`.
Version info is embedded in Flask app at runtime and shown in frontend.


### Deployment & Packaging Strategy:

- Application is versioned using `version.py`
- Version defined in `version.py`, loaded in Flask using `app.config['VERSION']`,and accessible in templates via Jinja2.
- Accessible within templates and rendered in the UI (`AggFin v{{ version }}`)
- GitHub & Release workflow located in `.github/workflows/pypi-deploy.yml`
- Displayed dynamically on the frontend for future development (footer `home.html`)
- Each release is tagged using **Semantic Versioning (SemVer)** format
- Packaged using `setup.py`, then published to **PyPI** using GitHub Actions
- Footer in `home.html` displays version dynamically (`AggFin v1.0.0`)
- Local automation uses `Makefile` and `setup.ps1`
- `setup.py` uses `find_packages()`, `install_requires`, and `classifiers` to build a standard-compliant Python package


### Configuration Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/unibo-dtm-se-2324-AggFinData/artifact.git
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set environment variables** (manually or via `.env`):
   ```bash
   FLASK_APP=run.py
   FLASK_ENV=production
   NEWS_API_KEY=your_api_key_here
   ```

4. **Run the app:**
   ```bash
   flask run
   ```

5. **Browser access explanation:**
    ```bash
    Once the server is running, open your browser and go to:
    http://localhost:5000/
    ```

6. **How to stop the server:**
    ```bash
    Press `CTRL+C` in the terminal to stop the Flask server.
    ```
7. **How to deactivate the virtualenv:**
    ```bash
    deactivate
    ```

## Choice of the License


No binary or container artefacts (e.g., Docker images or compiled packages) released separately, so no additional license isadded for artefacts. All artefacts are based on project main license.


code is licensed under **MIT License**, specified in `LICENSE.txt`.

**Why this license:**

- short and simple
- allows anyone to use, modify, and distribute code
- proper for academic and open-source projects
- perfect for reuse while protecting author

---

## Choice of the Versioning Schema

 Project now follows Semantic Versioning (SemVer) with real version tags and PyPI packaging. Current version defined in `version.py` and used consistently across packaging, app config, and UI display.

Under this versioning scheme, each release will be identified using three numbers:
```
MAJOR.MINOR.PATCH
```
- Example: Release `v1.0.0` marked first published version on PyPI.
- **MAJOR** increased when big changes that break compatibility is adopted, for instance, replacing database system or changing authentication process
- **MINOR** is for new features, like a stock chart, which does not affect what already works.
- **PATCH** is for smaller updates, bug fixes, UI adjustments, or minor backend changes that don’t change how users interact with app.