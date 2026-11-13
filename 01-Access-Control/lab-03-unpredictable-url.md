# Lab 03: Unprotected admin functionality with unpredictable URL

**Difficulty:** Apprentice
**Category:** Access Control (Vertical Privilege Escalation)

##  Objective
This lab has an admin panel at an unpredictable location. Solve the lab by finding the URL and deleting the user `carlos`.

##  Reconnaissance
1. Browsed the lab website. There was no admin link in the visible user interface.
2. Because developers often use JavaScript to hide or show UI elements based on user roles, I right-clicked the page and selected **"View Page Source"**.
3. Searched the HTML source code for the word `admin`.
4. Found a JavaScript snippet containing the hidden admin URL:
   ```javascript
   var isAdmin = false;
   if (isAdmin) {
       var adminPanelTag = document.createElement('a');
       adminPanelTag.setAttribute('href', '/admin-tp0r3e');
       // ...
   }
## Exploitation Steps
1. Copied the hidden URL path (/admin-tp0r3e) from the JavaScript source code.
2. Appended it to the lab's base URL in the browser address bar.
3. The admin panel loaded directly.
4. Located the user carlos and clicked "Delete".

## Result
User carlos deleted. Lab solved.

## Key Takeaway
Security by obscurity is not security. Hiding a URL in JavaScript does not protect it. The client-side code (HTML/JS) is visible to anyone who looks at the page source. Access control must be enforced on the server side
