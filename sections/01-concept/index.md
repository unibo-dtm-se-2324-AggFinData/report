---
title: Concept
has_children: false
nav_order: 2
---

# Concept

## Aggregation Service for Finance Data

AggfinData is a **web application** created using the Flask tools. It features a browser-based graphical user interface (GUI) that allows users to do these tasks:

- Search for real-time stocks data
- review related financial news
- creation of personal account

This project integrates with external data sources such as **Yahoo Finance** (`yfinance`) for stock data and **NewsAPI** for news articles.



### Users

Users can access to this platform from **any location** with internet connection without no geographic restriction. The application is browser-based and hosted on a server.

### Usage Scenarios:
- During market hours in order to become aware of live prices
- educational or research purposes


### Interaction

Interaction methods include:
- **Searching stock tickers** using a form input
- **Viewing stock profiles** and financial indicators
- **Reading related news articles**
- **Registering and logging in** via web forms

## Technical Implementation

- **Frontend**: HTML, CSS, JavaScript; enhanced with Bootstrap for responsive and mobile-friendly design.
- **Backend**: Python using the Flask framework to manage routes, user sessions, and API calls.
- **Database**: SQLite database accessed via SQLAlchemy ORM for storing User credentials and related metadata.
- **External APIs**:
  - **Yahoo Finance API (`yfinance`)** to retrieve real-time stock data
  - **NewsAPI** to fetch related financial news articles
- **Authentication**: Handled via Flask-Login, with password security managed by Flask-Bcrypt.

## Future Scope

- Add portfolio tracking features for saving favorite stocks
- Implement news sentiment analysis for smarter decision making
- Add visual part to enhance data interpretation



AggFinData aims to bring an informative, up-to-date, and user-friendly platform that blends data and news into a single financial dashboard for finance enthusiasts.