---
title: Validation
has_children: false
nav_order: 6
---

# Validation

This section is for testing strategy used to validate the AggFin workflow, and making sure the requirements met.

---

## Test Development Process

A  practical testing approach is used. This project did not fully followed test-driven development (TDD). tests were added during and after key functionality steps for checking the correctness.
An advanced test module added (`test_adv.py`) to automate validation of core workflows including registration, login (invalid and valid), and stock data retrieval via POST requests.


### Tools Used

- **Testing Framework:** `pytest`
- 
- **Test Client:** Flask’s built-in test client

- **Code Coverage:** Measured using `coverage.py`, final coverage reported: **67%**


This tool is chosen because of its simplicity and usablity with Flask applications. 

 
---

## Unit Testing

### What Was Tested

- **User Registration/Login Logic:** Verified valid registration, invalid login rejection, password hashing, and session creation.

- **Routing Access:** Ensured that routes such as `/register`, `/login`, and `/logout` return the correct responses.
- **Error Routes:** Confirmed proper response codes and template rendering for 404 and 500 errors.

### Examples

- Test: `POST /register` with valid inputs creates a new user and enter the account (confirms DB insert)
- Test: `POST /login` with invalid email/password fails and shows error0 (status code 200 and error message )
- Test: `POST /home` with `AAPL` returns valid stock results




---

## Integration Testing

Integration testing was applied to routes interacting with both the database and external APIs.

### Components Tested Together

- Registration + Login + Session management
- Stock search + NewsAPI + Yahoo Finance API
- Form submission + page rendering

### Example

- Test: Submitting a stock name via form should return a page with matching financial data and news headlines.
- Test: Stock search form with symbol like `AAPL` returns stock details (checked via POST request)


### Success Rate and Notes

- Tests consistently pass in local environments and advanced test achieved **67% coverage** which can be suitable
- External APIs accessed live (mocking not used), which may introduce test flakiness under network issues

---

## System Testing

System-level tests limited due to project scope and timing constraints.

### Simulated Use Cases

- Register a user → Log in → Search a stock → View results
- Trigger errors (e.g., bad URLs, server exceptions)
- All flows tested manually were replicated in automated tests

The scenario matched **functional requirements**, and helped validate end-to-end flows manually.

### Containers

No containers (e.g., Docker) used for isolated system testing.

---

## Acceptance Tests (Manual)

Manual testing used in validation of critical user flows. These tests mapped acceptance criteria defined in Requirements.

### Test Plan

| Test | Scenario | Expected Outcome |
|------|----------|------------------|
| ✅ Registration/Login | A new user registers, logs in, and logs out | Success & error messages are correctly shown via flash alerts in the UI |
| ✅ Stock Search | Entering a valid stock symbol returns results | Financial info + 3 news articles displayed |
| ✅ Autocomplete | Typing “A” in the search bar triggers suggestions | 4 suggestions shown (max) |
| ✅ Error Pages | Visit unknown URL or force exception | `404.html` or `500.html` is rendered |

### Success Rate

All acceptance tests passed manually in browser. Behavior matched expectations from requirements and error handling worked as intended.

---

## Requirements Validation Summary

| Requirement | Validated Through |
|-------------|-------------------|
| ✅ F1–F2 (User Auth) | Unit + Integration + Manual tests |
| ✅ F3–F6 (Stock Search, News, Autocomplete) | Integration + Manual |
| ✅ F7 (Invalid Inputs / Flash Feedback) | Unit tests + UI feedback |
| ✅ F8 (Error Handling) | Unit + Manual |
| ✅ NFR1–3 (Security, Usability, Performance) | Confirmed via flash messaging, performance testing, and interface behavior |
| ✅ IC1–IC4 (Tech Stack) | Fully reflected in implementation |

---

> Testing strategy, while not TDD-based, included both manual and automated validation of core flows, error handling, and user feedback, ensuring that functional and non-functional requirements were satisfied in real-time usage.
