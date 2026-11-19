# Lab 06: User ID controlled by request parameter with password disclosure

**Difficulty:** Apprentice
**Category:** Access Control (Horizontal Privilege Escalation / IDOR)

##  Objective
Retrieve the administrator's password using an IDOR vulnerability and a masked input field, then delete `carlos`.

##  Reconnaissance
1. Logged in as `wiener`. Navigated to the account page and noticed the password was prefilled in a masked input field.
2. Changed the URL parameter from my ID to `carlos`. Successfully viewed Carlos's masked password.
3. Attempted to view the administrator's page by changing the ID to `administrator`. The page loaded.

##  Exploitation Steps
1. On the administrator's account page, the password was masked (shown as dots).
2. Right-clicked the password field and selected **Inspect**. 
3. Changed the HTML attribute `type="password"` to `type="text"`.
4. The password was immediately unmasked in the browser.
5. Copied the administrator's password.
6. Logged out of `wiener`, logged in as `administrator` using the stolen password.
7. Navigated to the `/admin` panel and deleted `carlos`.

##  Result
Lab solved.

##  Key Takeaway
**Client-side masking is not security.** If the server sends the password to the browser, it can be unmasked. The server should never send another user's password to the client, even in a masked field.
