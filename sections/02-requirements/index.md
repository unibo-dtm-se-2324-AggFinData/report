---
title: Requirements
has_children: false
nav_order: 3
---

# Requirements

## Functional Requirements

### 1. User Account Management
**Requirement:** Users must be able to register and log in a secure way
**Acceptance Criteria:**
- Users can register with email, username, and password, and can log in and log out
- Passwords securely hashed using Flask-Bcrypt
- Sessions managed using Flask-Login

### 2. Stock Search
**Requirement:** Users must be able to search for real-time stock info 
**Acceptance Criteria:**
- Users can enter a stock name(ticker) in a search form
- Financial data fetched via the `yfinance` API
- Search results display stock price, and some other info.

### 3. News Display
**Requirement:** Users must be able to view related financial news  
**Acceptance Criteria:**
- The system fetches related articles using NewsAPI
- At least 3 relevant articles displayed per stock
- Articles include titles, sources, and links

### 4. Autocomplete Suggestions
**Requirement:** The system must help users find stock tickers in a faster way  
**Acceptance Criteria:**
- The app offers autocomplete suggestions after typing 2 characters
- Suggestions are based on a predefined list of popular stocks
- Suggestions update dynamically with user input

### 5. Homepage Recommendations
**Requirement:** Users should see useful suggestions on the homepage  
**Acceptance Criteria:**
- A list of 5 randomly chosen stock tickers is shown
- Each suggestion includes the stock name(ticker) and a short description

### 6. Error Handling
**Requirement:** The system must handle errors gracefully  
**Acceptance Criteria:**
- 404 error renders a custom "Page Not Found" page
- 500 error renders a custom "Internal Server Error" page


---

## Non-Functional Requirements

### 1. Performance
**Requirement:** The app should respond quickly 
**Acceptance Criteria:**
- Stock and news results appear within 2 seconds based on network speed and API
- Minimal lag for autocomplete search


### 2. Security
**Requirement:** User credentials and sessions must be protected  
**Acceptance Criteria:**
- Passwords are stored using bcrypt hashing
- Login/logout uses secure session cookies
- SQL injection protection via SQLAlchemy ORM

### 3. Usability
**Requirement:** The UI should be responsive 
**Acceptance Criteria:**
- Bootstrap ensures proper display on all screen sizes
- Layout remains usable on both desktop and mobile
- Inputs have clear placeholder text and labels


---

## Implementation Requirements

### 1. Technology Stack
**Requirement:** The project must be built using course-approved technologies  
**Acceptance Criteria:**
- Backend: Flask (Python)
- Frontend: HTML5, CSS3, JavaScript (Jinja2 templating)
- UI Framework: Bootstrap
- Database: SQLite via SQLAlchemy
- External APIs: `yfinance`, NewsAPI
- GPT was used in some parts for debugging errors in coding.

### 2. Development Standards
**Requirement:** Codebase should follow proper structure 
**Acceptance Criteria:**
- Code is modularized using Blueprints (`main`, `users`, `auth`)
- App factory pattern used in `__init__.py`
- Configuration settings separated in `config.py`
- Error handlers and templates stored in dedicated directories

### 3. Deployment Readiness
**Requirement:** The project should be easy to run 
**Acceptance Criteria:**
- Installable via `requirements.txt`
- Launchable via `run.py`
- Jekyll report site can be previewed locally and deployed via GitHub Pages

---

## Glossary

- **Stock Ticker**: A short code representing a publicly traded company (e.g., AAPL, TSLA).
- **yfinance**: Python library fetch real-time stock data from Yahoo Finance.
- **NewsAPI**: API providing access to global news articles based on keywords.
- **Autocomplete**: A feature suggesting text while typing.
- **ORM**: Object-Relational Mapping, translates database tables into Python objects.(SQLAlchemy ORM)
- **Blueprints**: Flask design pattern for structuring routes/modules.
