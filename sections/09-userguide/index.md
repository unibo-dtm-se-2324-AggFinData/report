---
title: User Guide
has_children: false
nav_order: 10
---

# User Guide

This section you can find the details regarding how to use AggFin application from user’s experience.

---

## 1. Accessing the App

- Open your browser and go to `http://localhost:5000`.
- You will see a homepage with a stock search bar and navigation bar.

![Homepage](../../pictures/home.png)

---

## 2. User Registration

- Click on **"Sign Up"** button.
- Fill the form with email and password.
- Submit the form to create an account.


---

## 3. Logging In

- Click **"Login"** in navbar.
- Enter your registered email and password.
- If valid, you'll be redirected to homepage.

![Login](../../pictures/login.png)

---

## 4. Searching for Stock Data

- Type a valid stock symbol (e.g., `AAPL`, `GOOGL`) in the search bar.
- Select a background color (optional).
- Click "Search."
- The app displays:
  - Company info from `yfinance`
  - Top 3 recent news articles

![Stock Search](../../pictures/stocksearch.png)

---

## 5. Responsive UI

- The application layout can be usable to different screen sizes and devices.

![Responsive UI](../../pictures/responding%20for%20all%20devices.png)

---

## 6. Error Handling

- Typing unknown route by **404 error page**.
- API issues or internal errors show **500 error page**.

![Error 500](../../pictures/error.png)

---

## 7. About Page

- “About” page has platform’s mission and purpose.

![About Page](../../pictures/about.png)

---

## 8. Navigation Overview

- navigation bar includes:
  - Home
  - About
  - Suggest (autocomplete)
  - Register / Login / Logout
- After logging in, you'll stay authenticated until you log out.

---

> All screenshots recorded in a safe way to avoid exposing passwords or sensitive API keys. Contents are cropped where needed.

## 9. Behind-the-Scenes & Conceptual Models

While users mostly interact with UI, app also follows certain internal logic and flows. Below are simplified visualizations for better understanding of underlying system:

### Authentication Flow

Illustrates how login credentials flow from user to authentication and back-end:

![Dataflow](../../pictures/diagram/dataflow.png)

---

### User Model Structure

Breakdown of user fields (`id`, `username`, `email`, `password`) and basic transitions (register → login → logout):

![User Model Flow](../../pictures/diagram/user_model.png)

---

### System Class Overview

How different service classes (`AuthService`, `UserRepository`, `FinancialService`) interact with the main `User` and `News` entities:

![Component Roadmap](../../pictures/diagram/comp_roadmap.png)

---

> Diagrams represent simplified conceptual views. I added them to help clarify internal logic of app for documentation and academic reporting purpose of the course.
