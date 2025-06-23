---
title: Design
has_children: false
nav_order: 4
---

# Design

This section is for the strategies for requirements necessary for analysis. In this design, there is a clean separation of responsibilities. It is guided by layered architectural and Domain-Driven Design (DDD) for structure and scalability.

---

## Architecture

### Style

- **Architectural Style**: Layered Architecture
- **Why**: The application separates presentation (UI), logic (Flask routes), and data (ORM), making the system easy for more modification and improvments.
- **Why not others**: Event-driven or shared-dataspace architectures are unnecessary here as the application is not distributed(no need for asynchronous messaging)

### Actual Architecture

- **Three-Tier (N-tier) Model**:
  - **Presentation Layer**: HTML templates rendered via Jinja2
  - **Application Layer**: Flask route functions
  - **Data Access Layer**: SQLAlchemy ORM, connected to SQLite

- **Modularized via Flask Blueprints**:
  - `main`: homepage, search, autocomplete
  - `users`: user registration, login
  - `auth`: logout(logout in auth because it deals with session/authentication behavior, not user identity. for cleaner structure)
  - `errors`: error handling (404, 500)

### Responsibilities by Component

| Component      | Responsibility                                     |
|----------------|----------------------------------------------------|
| `routes.py`    | Handles `/`, `/home`, `/about`, `/suggest`         |
| `auth.py`      | Manages logout                                      |
| `forms.py`     | Manages user registration/login forms              |
| `models.py`    | Contains the `User` model (SQLAlchemy ORM)         |
| `handlers.py`  | Custom error pages                                 |
| `templates/`   | Jinja2 templates for all views                     |
| `config.py`    | App configuration + NewsAPI key                    |
| `__init__.py`  | App factory and blueprint registration             |

---
## Infrastructure

This project is not a distributed system, so infrastructure is intentionally minimal.

### Components

- **Client**: Any modern web browser
- **Web Server**: Flask server running locally,  or can be usable to a cloud platform.
- **Database**: SQLite data stored locally in same machine as Flask server
- **External APIs**:
  - `yfinance`: fetch stock market data
  - NewsAPI: reclaim financial news

### Deployment Setup

Components (server, application logic, templates, and database) on a **single machine**, typically a developer's laptop. no separate services, load balancers, message queues, or microservices.

### Network Layout

- Components ommunication within the same process or host machine.
- External API calls over HTTPS to public third-party services (Yahoo Finance, NewsAPI).
- No need for internal service discovery, DNS, or load balancing(monolithic app, everything runs on a single server, with a single database, and scaling across multiple services or machines)

### Naming and Addressing

- The app is accessible at `localhost` during development.
- If deployed, DNS configuration point to a single web host (optional, not yet implemented).

---

## Modelling

### Domain-Driven Design (DDD)

- **Bounded Context**: data exploration through user-based access
- **Entities**:
  - `User`: represents an authenticated system
- **Services**:
  - `get_news(stock_name)`: handle integration of news
  - `yf.Ticker().info`: fetches stock info

**Factories/Aggregates**: Not applicable forr this scale.  
**Relevant Events**:
- User registers
- User logs in
- User searches for a stock

### Object-Oriented Modelling

- **Main Class**: `User`
  - Attributes: `id`, `username`, `email`, `password`, `date_created`
  - Methods: `__repr__()` (for debugging)
- SQLAlchemy maps class attributes to database.

---

## Interaction

- **Interaction Pattern**: Synchronous HTTP requests
- Sequence:
  1. User searches for a ticker and submits the form
  2. Flask route receives the req
  3. Info fetched via `yfinance`, news via `NewsAPI`
  4. Jinja2 template renders results

> Suggestion feature (`/suggest`) uses JavaScript to fetch matches via a `GET` API call dynamically.

---

## Behaviour

- **Stateless**: Public routes like `/about`, `/suggest`, and homepage (GET)
- **Stateful**: Authenticated user sessions (Flask-Login)
- Error handling:
  - 404 and 500 errors are rendered with custom HTML
  - Debugging possible during development via logging

---

## Data-Related Aspects

### Stored Data

- **Persistent**: `User` data (username, email, password hash)
- **Transient**: Stock data and news (fetched per request)

### Storage Details

- **Backend**: SQLite using SQLAlchemy ORM
- **Why**: Lightweight, fast, ideal for a demo

### Query Patterns

- CRUD operations on `User`
- No complex joins or relationships
- Autocomplete uses in-memory `STOCK_OPTIONS` list

**No concurrency concerns** — app runs on a single instance.

---

> 💡 *design enables future reshaping toward a more real-time architecture if needed ( Redis for caching, PostgreSQL for scale, background workers for API polling).*
