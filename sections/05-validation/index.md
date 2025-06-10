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

### Tools Used

- **Testing Framework:** `pytest`
- 
- **Test Client:** Flask’s built-in test client

This tool is chosen because of its simplicity and usablity with Flask applications. 

 
---

## Unit Testing

### What Was Tested

- **User Registration/Login Logic:** Verified password hashing, database creation, and authentication.
- **Routing Access:** Ensured that routes such as `/register`, `/login`, and `/logout` return the correct responses.
- **Error Routes:** Confirmed proper response codes and template rendering for 404 and 500 errors.

### Examples

- Test: `GET /register` shows status code 200 and render the registration form.
- Test: `POST /login` valid credentials start a session and redirect to home.



---

## Integration Testing

Integration testing was applied to routes interacting with both the database and external APIs.

### Components Tested Together

- Registration + Login + Session management
- Stock search + NewsAPI + Yahoo Finance API
- Form submission + page rendering

### Example

- Test: Submitting a stock name via form should return a page with matching financial data and news headlines.

### Success Rate and Notes

- Tests consistently in local environments.
- External API was a limiting factor during testing. Mocking not implemented.

---

## System Testing

System-level tests limited due to project scope and timing constraints.

### Simulated Use Cases

- Register a user → Log in → Search a stock → View results
- Trigger errors (e.g., bad URLs, server exceptions)

The scenario matched **functional requirements**, and helped validate end-to-end flows manually.

### Containers

No containers (e.g., Docker) used for isolated system testing.

---

## Acceptance Tests (Manual)

Manual testing used in validation of critical user flows. These tests mapped acceptance criteria defined in Requirements.

### Test Plan

| Test | Scenario | Expected Outcome |
|------|----------|------------------|
| ✅ Registration/Login | A new user registers, logs in, and logs out | Success message shown, session maintained |
| ✅ Stock Search | Entering a valid stock symbol returns results | Financial info + 3 news articles displayed |
| ✅ Autocomplete | Typing “A” in the search bar triggers suggestions | 4 suggestions shown (max) |
| ✅ Error Pages | Visit unknown URL or force exception | `404.html` or `500.html` is rendered |

### Success Rate

All acceptance tests passed manually in browser. Behavior matched expectations from requirements and error handling worked as intended.

---

## Requirements Validation Summary

| Requirement | Validated Through |
|-------------|-------------------|
| ✅ F1–F2 (User Auth) | Unit + Manual tests |
| ✅ F3–F6 (Stock Search, News, Autocomplete) | Manual & integration |
| ✅ F8 (Error Handling) | Unit + Manual |
| ✅ NFR1–3 (Security, Usability, Performance) | Observed in behavior |
| ✅ IC1–IC4 (Tech Stack) | Aligned with actual implementation |

---

> testing strategy, while minimal, effectively validated core requirements and ensured a basic robustness of app in real-time usage.
