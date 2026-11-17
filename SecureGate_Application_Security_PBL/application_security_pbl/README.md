# SecureGate — Application Security PBL

**Project type:** Python Flask web application  
**Topic:** Secure user authentication and web application security

## 1. Abstract
SecureGate is a small web application built to demonstrate practical application-security controls. Users can register, log in, access a protected dashboard and log out. The project demonstrates how common web vulnerabilities can be reduced through secure coding practices.

## 2. Objectives
- Store passwords as salted hashes instead of plaintext.
- Prevent SQL injection using parameterized database queries.
- Protect POST forms against Cross-Site Request Forgery (CSRF).
- Limit repeated login attempts.
- Protect sessions and reduce session-fixation risk.
- Add browser-facing HTTP security headers.

## 3. Security controls
| Risk | Control implemented |
|---|---|
| Plaintext password exposure | Werkzeug password hashing |
| SQL injection | SQLite parameterized query (`?`) |
| CSRF | Random session token checked on POST |
| Brute-force attempts | In-memory limit of 5 attempts per IP per minute |
| Session fixation | Session cleared after successful login |
| Session theft / misuse | HttpOnly and SameSite cookie settings; 30-minute lifetime |
| Clickjacking / MIME sniffing | X-Frame-Options and X-Content-Type-Options |
| Browser data exposure | Referrer-Policy and Content-Security-Policy |

## 4. Technology stack
- Python 3
- Flask
- SQLite
- HTML and CSS
- Werkzeug security utilities

## 5. How to run
1. Install Python 3.10 or newer.
2. Extract this project folder.
3. Open a terminal in the project folder.
4. Install dependencies:
   `pip install -r requirements.txt`
5. Start the application:
   `python app.py`
6. Open `http://127.0.0.1:5000` in your browser.
7. Register a test account, log in, view the dashboard and log out.

For deployment, set a strong random `SECRET_KEY`, run behind HTTPS, set `HTTPS=1`, and use a production WSGI server. Do not use the development server for public hosting.

## 6. Testing checklist
- Register with a valid username and a password of at least 10 characters.
- Try registering the same username twice.
- Log in with a wrong password and confirm access is denied.
- Open `/dashboard` in a logged-out browser and confirm it redirects to login.
- Log in successfully and confirm the dashboard is accessible.
- Submit a POST form without a CSRF token and confirm it is rejected with HTTP 400.
- Make more than five failed login attempts in one minute from the same IP and confirm HTTP 429.
- Inspect response headers in browser developer tools.

## 7. Limitations and future scope
This is an educational prototype, not a production identity platform. Rate-limit data is stored in memory and resets when the server restarts. Production systems should use a shared rate-limit store, email verification, password reset with one-time tokens, MFA, HTTPS-only deployment, audit logging, stronger monitoring and automated security tests.

## 8. Conclusion
SecureGate demonstrates that application security must be considered during development. Applying password hashing, parameterized queries, CSRF validation, rate limiting and secure session configuration helps reduce common risks in authentication workflows.

## 9. References
- Flask documentation: https://flask.palletsprojects.com/
- OWASP Top 10: https://owasp.org/www-project-top-ten/
- OWASP CSRF Prevention Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html
- OWASP Password Storage Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
