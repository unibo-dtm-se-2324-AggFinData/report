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
- No releases published to PyPI, Docker Hub, or similar registries, since project is educational.


---

## How Are They Released?

Releases are done **manually**, no CI/CD pipeline currently implemented.

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

At the moment, Project does not yet use formal release tags, but I will use **Semantic Versioning (SemVer)** convention as a guideline for future updates, which helps keeping track of changes in a consistent and predictable way.

Under this versioning scheme, each release will be identified using three numbers:
```
MAJOR.MINOR.PATCH
```

- **MAJOR** increased when big changes that break compatibility is adopted, for instance, replacing database system or changing authentication process
- **MINOR** is for new features, like a stock chart, which does not affect what already works.
- **PATCH** is for smaller updates, bug fixes, UI adjustments, or minor backend changes that don’t change how users interact with app.