# PROJECT REPORT
## SECUREGATE: SECURE USER AUTHENTICATION SYSTEM
### Project-Based Learning — Application Security

**Submitted by:** Piyush Jha  
**Programme:** B.Tech — Cybersecurity  
**University:** GD Goenka University  
**Subject:** Application Security

### Introduction
Web applications often process sensitive user information. Weak authentication and insecure input handling can expose users to attacks such as SQL injection, password theft, cross-site request forgery and brute-force login attempts. SecureGate is developed as a practical demonstration of basic application-security controls.

### Problem Statement
A basic login application that stores passwords in plain text, builds SQL queries using string concatenation or accepts unlimited login attempts can be compromised. The project demonstrates safer alternatives for these common weaknesses.

### Proposed Solution
SecureGate provides user registration, login, a protected dashboard and logout. Passwords are hashed before storage. SQL queries are parameterized. POST requests require a CSRF token. Login attempts are rate-limited, sessions are refreshed after authentication, and security headers are added to responses.

### Modules
1. Registration module — validates username and password and stores a password hash.
2. Login module — verifies password hashes and applies attempt limits.
3. Session module — maintains authenticated state and protects the dashboard.
4. CSRF module — checks a random token on state-changing POST requests.
5. Security-header module — adds browser security response headers.

### Expected Outcome
The application should allow valid users to register and sign in, deny invalid credentials, block unauthenticated dashboard access and reject POST requests with missing or invalid CSRF tokens.

### Conclusion
The project provides hands-on understanding of secure authentication design and demonstrates how secure coding practices can reduce common web application risks.

### References
Flask documentation; OWASP Top 10; OWASP CSRF Prevention Cheat Sheet; OWASP Password Storage Cheat Sheet.
