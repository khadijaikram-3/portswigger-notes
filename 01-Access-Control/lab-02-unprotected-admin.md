# Lab 02: Unprotected admin functionality

**Difficulty:** Apprentice
**Category:** Access Control (Vertical Privilege Escalation)

##  Objective
This lab has an unprotected admin panel. Solve the lab by deleting the user `carlos`.

##  Reconnaissance
1. Browsed the lab website. There was no admin link in the UI.
2. Appended `/robots.txt` to the URL to check for hidden directories.
3. The `robots.txt` file revealed: `Disallow: /administrator-panel`.

##  Exploitation Steps
1. Replaced `/robots.txt` with `/administrator-panel` in the URL bar.
2. The browser loaded the admin panel directly.
3. Located the user `carlos` and clicked "Delete".

##  Result
User `carlos` deleted. Lab solved.

##  Key Takeaway
Never rely on security through obscurity. Hiding a link in the UI does not protect the backend functionality. Always check `robots.txt` during recon.
