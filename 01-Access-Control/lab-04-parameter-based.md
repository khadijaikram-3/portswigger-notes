# Lab 04: User role controlled by request parameter

**Difficulty:** Apprentice
**Category:** Access Control (Vertical Privilege Escalation)

##  Objective
This lab has an admin panel at `/admin`, but it's only accessible to users with the `Admin` role. The role is determined by a cookie. Solve the lab by accessing the admin panel and deleting the user `carlos`.

##  Exploitation Steps
1. Logged in as a normal user (`wiener`).
2. Tried to access `/admin`, but was redirected to the login page.
3. Opened Browser Developer Tools (F12) -> **Application** tab -> **Cookies**(expanded it) -> clicked URL.
4. Located the cookie named `Admin` with the value `false`.
5. Changed the value from `false` to `true`.
6. Navigated to the URL `/admin`.
7. The admin panel loaded successfully.
8. Deleted the user `carlos`.

##  Result
Lab solved. The server trusted the client-side cookie to determine the user's role.

##  Key Takeaway
**Never trust the client.** Cookies and hidden fields can be manipulated by the user. Authorization checks must be performed on the server-side using secure session data.
