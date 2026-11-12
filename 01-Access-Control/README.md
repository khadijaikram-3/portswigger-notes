# Access Control

**Access Control** is the application of constraints on who (or what) is authorized to perform actions or access resources.

Think of a hotel:
- **Authentication:** Showing your ID at the front desk.
- **Session Management:** The keycard given to you.
- **Access Control:** The rules of what your keycard can open (your room, but not the penthouse).

**Broken Access Control** is when the keycard system fails, and a normal user can access the penthouse suite.

## Types of Access Control Vulnerabilities
1. **Vertical Privilege Escalation:** A normal user gains access to admin functionality (e.g., accessing `/admin`).
2. **Horizontal Privilege Escalation (IDOR):** A user accesses another user's resources at the same privilege level (e.g., changing `user_id=1234` to `user_id=1235`).
3. **Force Browsing:** Manually sending requests (via Burp Suite) to endpoints that the UI hides from you.

## Why is it so common?
Developers often rely on "security through obscurity" (hiding buttons with CSS) instead of enforcing server-side permission checks. Hackers bypass the UI using tools like Burp Suite.
