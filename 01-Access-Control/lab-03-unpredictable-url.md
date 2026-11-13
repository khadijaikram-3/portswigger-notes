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
5. Then I put the /admin-tp0r3e at the end of URL and I login as admin and deleted carlos user.
