# Lab 05: User ID controlled by request parameter with unpredictable user IDs

**Difficulty:** Apprentice
**Category:** Access Control (Horizontal Privilege Escalation / IDOR)

##  Objective
Retrieve Carlos's API key by exploiting an IDOR vulnerability, even though the user IDs are GUIDs.

##  Reconnaissance
1. Logged in as `wiener`. Noticed the account URL used a long GUID instead of a predictable number.
2. Clicked on a blog post and scrolled to the comments.
3. Found a comment by `carlos` and clicked his name. The URL revealed his GUID.

##  Exploitation Steps
1. Copied Carlos's GUID from the URL.
2. Navigated back to my account page: `/my-account?id=[wiener's GUID]`.
3. Replaced my GUID with Carlos's GUID.
4. The page loaded Carlos's account details, revealing his API key.

##  Result
Lab solved.

##  Key Takeaway
GUIDs are not a security control. They are often leaked in public areas of the application (comments, reviews). The server must verify that the logged-in user has permission to view the requested ID.
