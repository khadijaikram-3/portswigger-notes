# Authentication Vulnerabilities

## Core Concepts
- **Authentication:** Verifying that a user is who they claim to be (Identity).
- **Authorization:** Verifying whether a user is allowed to do something (Permissions).
- **Rule:** You authenticate first, then authorize.

## Brute-Force Attacks
- **Definition:** Using a system of trial and error to guess valid user credentials, often automated using wordlists.
- **Efficiency:** Hackers use logic and publicly available knowledge to fine-tune attacks (e.g., guessing passwords based on the user's interests or common patterns).
- **Impact:** Websites relying solely on password-based login without sufficient brute-force protection are highly vulnerable.

## Username Enumeration
- **Predictable Patterns:** Usernames often follow patterns (`firstname.lastname@company.com`) or use default admin names (`admin`, `administrator`, `root`).
- **Public Profiles:** Viewing profiles without logging in can reveal the login username.
- **HTTP Responses:** Emails of privileged users are sometimes leaked in HTML source code, headers, or error messages.
- **Default Accounts:** High-privilege accounts often have lazy/obvious usernames.
