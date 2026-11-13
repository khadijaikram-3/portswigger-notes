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

## Security by Obscurity (Unpredictable URLs)
Developers sometimes try to hide sensitive functionality by giving it a less predictable URL (e.g., `https://insecure-website.com/administrator-panel-yb556`). 

They think, *"Nobody will ever guess `yb556`! It's totally safe!"* This is a fatal mistake.

**How Hackers Exploit This:**
If the admin link is hidden using JavaScript (e.g., `if (isAdmin) { show link }`), the browser still has to download that JavaScript file. This means the secret URL is sitting right there in the source code. 

**The Exploit Steps:**
1. Log in as a normal user.
2. Right-click the page and select **"View Page Source"** (or press `Ctrl+U`).
3. Search the code for words like `admin`, `href`, or `panel`.
4. Find the hidden URL in the JavaScript.
5. Paste the URL into the browser to access the admin panel.

**The Lesson:** The server must enforce access control. The client-side browser (JavaScript) cannot be trusted to hide anything.

