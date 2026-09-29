# price--detector-
a full-stack price-drop tracker with JWT auth, a REST/JSON API, and SQLite storage. Track products, log price checks, and get flagged the moment something hits your target price.
Stack
Backend: Node.js, Express, better-sqlite3, JWT (jsonwebtoken), bcryptjs
Frontend: Vanilla HTML/CSS/JS (no build step)
Data format: JSON over REST

Note: 
the JWT is kept in memory in the browser tab, not in localStorage —
refreshing the page signs you out. That's a deliberate simplification for
this demo; a production build would add refresh tokens or an httpOnly
session cookie instead.

Extending :
it
Add email/push notifications on droppedToTarget
Add a scraper/cron worker per retailer
Add refresh tokens for longer sessions
Add pagination on GET /api/products for large lists

Design notes:
This build tracks prices you (or a script you write) report in — it does not
scrape retailer websites itself, since that depends on each site's terms of
service and page structure. To make it live, you'd add a scheduled job that
fetches a price from each product's url and calls
POST /api/products/:id/prices automatically
