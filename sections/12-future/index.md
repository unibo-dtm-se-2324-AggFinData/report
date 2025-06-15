---
title: Future work
has_children: false
nav_order: 13
---

# Known problems and Future Work

This part of the Aggfin project is about limitations of project and future improvements.

---

## Known Issues & missing Features

- **Background Color Change :** this is a feature for changing background color(currently not working properly). Code is present but not rendering effect correctly.
- **Fetching Delay:** In some parts, financial news related to searched stocks cannot be received and published in website. This can be because of API quota limits.
- **Suggestion List:** autocomplete suggestion list sometimes fails to show relevant list of stock when writing the three first letters of stock's names. It may work not in a continuous way or not affect JavaScript coding part correctly depending on input speed.
- **User Personalization:** User prefeerred stock are not saved beyond login.(no user-specific stock history).  User cannot save or follow specific stocks in his or her personal watchlist.
- **Search History:** It does not record user to recheck his or her recent stock searches.
- **Charting:** No graphical charts for stock trends are designed.
- **Mobile Optimization:** While layout is responsive, some features don’t appeare good on small screens.

---

## Future Work

- Implementing **stock history**, to allow users to track what they’ve searched during a login session and adding a **user watchlist** to let users follow specific stocks.
- Introducing **graphical visualization** using libraries like Chart.
- Adding more analysis tools and features like **dark mode** for better accessibility.
- Improving **error handling for NewsAPI**, including user-friendly fallback messages.

> I will try fixing issues I mentioned here until final presentation day. This document is for current status, final version will be improved in order to fix problems.