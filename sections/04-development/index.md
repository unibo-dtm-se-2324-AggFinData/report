---
title: Development
has_children: false
nav_order: 5
---

# Development

This section describes  version control practices and technologies used during development of **AggFin**.

---

## Version Control (Git & GitHub)

**GitHub** as remote version control platform. development tracked via Git terminal.

### Branching Strategy

- **main branch** used for most of work.
- different branch used for Login and Error Page.
- Some optional feature testing done in local branches(not pushed).
- For simplicity, **no GitFlow or PR-based branching** strategy enforced.


### Commit Conventions

- Commit messages descriptive 
- Messages referred to the section being worked on.

### .gitignore Usage

- A `.gitignore` file was used to exclude:
  - Python cache files (`__pycache__/`)
  - Environment files (e.g., `.env`)
  - SQLite database files
- prevent unnecessary or sensitive data from entering version control.

---

## Learning Experience: .gitignore Setup

Initially, `.gitignore` not configured before creating the Python virtual environment. As a result, some unnecessary files (e.g., `.pyc` ) tracked. This issue was later corrected by updating `.gitignore` and removing cached files.

---

## Implementation Details

### Network Protocols

- **HTTP/HTTPS** used for all frontend/backend communication.
  - Browser → Flask server
  - Flask server → External APIs (NewsAPI, Yahoo Finance)
- **TCP** served as the transport protocol underneath HTTP.

**Why:** HTTP standard for web apps. HTTPS for encrypted transmission . TCP for reliable communication for API access.

---

### In-Transit Data Representation

- **HTML**: used between server and browser via Jinja2 templates.
- **JSON**: used in:
  - AJAX calls for autocomplete (`/suggest`)
  - Responses from NewsAPI and Yahoo Finance

**Why:** JSON lightweight for both internal and external API communication. HTML suited for rendering views in web apps.

---

### Database Querying

- **SQLAlchemy ORM** utilized to define and query the `User` model.
- Under the hood, queries are translated into **SQL** specific to **SQLite**.

**Why:** SQL standard for relational data. SQLAlchemy easy querying while offering protection against SQL injection.

---

### Component Authentication

- **Flask-Login**  for managing user sessions.
- Authentication via email/password.
- Passwords hashed using **Flask-Bcrypt** before saving.

**Why:** Flask-Login proper for secure handling user sessions. Hashing protects user credentials even if the database is leaked.

---


## Technological Details

### Languages, Frameworks, and Tools

- **Python**: backend language for logic
- **Flask**: lightweight web framework
- **HTML/CSS/JavaScript**: standard frontend stack
- **Jinja2**: template engine for rendering views
- **SQLite**: simple embedded database
- **Bootstrap**: UI framework for responsive design

### Libraries and Dependencies

- `Flask`: web app routing and middleware
- `Flask-Bcrypt`: secure password hashing
- `Flask-Login`: user session management
- `Flask-SQLAlchemy`: ORM for database interactions
- `requests`: HTTP client for external APIs
- `yfinance`: fetches stock financial data
- `python-dotenv`: environment variable management (if used)
- `NewsAPI`: external news integration

### External Services

- **NewsAPI**: financial news based on stock names
- **Yahoo Finance (via `yfinance`)**: real-time financial data

**Why:** Both APIs reliable, accessible with free keys, easy to integrate in Python.

---
