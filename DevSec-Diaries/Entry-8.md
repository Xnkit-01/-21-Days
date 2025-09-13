### Burp Suite Basics

### Objective

Get comfortable with Burp Suite as a web proxy and the core tools used in manual web application testing (Proxy, Target, Repeater, Intruder, Sequencer, Decoder, Spider/Scanner).

### Setup

1. Install Burp Suite Community or Professional.
2. Configure browser to use Burp as an HTTP/HTTPS proxy (default: `127.0.0.1:8080`).
3. Install Burp CA certificate into the browser to intercept HTTPS traffic.

### Core Workflow

* **Proxy (Intercept):** Capture and inspect requests/responses between browser and server.
* **Target:** View site map, identify pages, parameters, and interesting endpoints.
* **Spider / Crawl:** Discover hidden endpoints (community edition: use manual crawling or Burp’s crawler if available).
* **Repeater:** Manually resend and modify requests to test behavior.
* **Intruder:** Automate payloads for fuzzing and parameter testing (note: Community edition has limitations).
* **Sequencer:** Analyze randomness of tokens (session IDs, CSRF tokens).
* **Decoder:** Convert/inspect encodings (URL, Base64, hex, etc.).

### Practical Exercises 

1. **Capture traffic:** Visit the target application and capture a full login flow.
2. **Inspect requests:** Identify authentication endpoints, form parameters, cookies, and headers.
3. **Send to Repeater:** Modify a POST login request (change username/password fields, tamper with parameters).
4. **Test session cookies:** Logout and replay session cookie in Repeater — does it remain valid?
5. **Use Decoder:** Decode any Base64 or URL-encoded tokens you find.
6. **Document findings:** Note interesting endpoints and any unexpected responses.

### Notes & Tips

* Use a disposable test account or an explicitly approved testing environment.
* Turn off interception when you don’t need it (so pages load normally).
* For HTTPS, ensure the browser trusts Burp’s CA to avoid certificate errors.
* Respect rate limits and avoid DoS-like behaviour during intruder runs.

---

### Capture / Login Test Writeup (Report Template)

Use this template to write a clear, reproducible capture/login test report.

```markdown
# Login Capture & Test Report

**Date:** YYYY-MM-DD  
**Author:** Your Name  
**Target:** https://example.target

---

## 1. 🎯 Objective
Capture the login flow and test for authentication-related weaknesses (insecure transmission, weak session management, missing protections like CSRF, improper login responses).

## 2. 📌 Scope
- **Target host(s):** example.target
- **Pages tested:** /login, /auth, /dashboard
- **Tools used:** Burp Suite (Proxy, Repeater, Intruder, Sequencer), browser (with Burp CA), curl (optional)
- **Account used:** testuser@example.com (test account)

## 3. ⚙️ Environment & Setup
- Burp Suite Community/Pro version: X.X  
- Browser: Firefox / Chrome (configured to proxy through 127.0.0.1:8080)  
- Burp CA certificate installed: ✅/❌  

## 4. 🔍 Test Steps (Reproducible)
1. Start Burp proxy and enable interception.  
2. Visit `https://example.target/login` in the proxied browser.  
3. Enter credentials and submit the form; capture the POST request to `/auth/login`.  
4. Send the captured request to **Repeater**.  
5. Observe and document response codes, set-cookie headers, and any tokens returned.  
6. Modify parameters in Repeater (e.g., change `username` to `admin` or tamper hidden fields) and observe behavior.  
7. Test for missing protections:  
   - Replay the login POST without CSRF token (if present).  
   - Change `Content-Type` or tamper headers to test server validation.  
   - Replay session cookie in a new browser session to check session fixation.  
8. Optionally, use **Intruder** to test rate-limiting or brute force protections (be cautious and allowed).

## 5. 🧾 Findings / Evidence
| # | Issue | Request (snippet) | Evidence (response, header) | Severity | Recommendation |
|---|-------|-------------------|-----------------------------|----------|----------------|
| 1 | Credentials sent over HTTP | `POST /auth` body: `username=...&password=...` | Response shows `Set-Cookie: session=abcd; Path=/` | High | Enforce HTTPS, set Secure flag on cookies |
| 2 | Missing CSRF token on login | Login form has no CSRF hidden input | Replayed POST accepted without token | Medium | Implement CSRF tokens and verify server-side |
| 3 | Session cookie missing HttpOnly | `Set-Cookie: session=abcd` | Cookie accessible by JS (document.cookie) | High | Add `HttpOnly; Secure; SameSite` attributes |

*(Add request/response snippets or screenshots below—redact sensitive data if needed)*

### Example request (captured)
```

POST /auth/login HTTP/1.1
Host: example.target
Content-Type: application/x-www-form-urlencoded
Content-Length: 45

username=testuser\&password=TestPass123

```

### Example response (captured)
```

HTTP/1.1 302 Found
Set-Cookie: session=abcd1234; Path=/
Location: /dashboard

```

## 6. 🛠️ Remediations & Recommendations
- Enforce HTTPS for all authentication endpoints and set `Secure` flag on cookies.  
- Set `HttpOnly` and `SameSite=Lax/Strict` on session cookies.  
- Implement CSRF protections for state-changing requests (and verify server rejects requests without valid tokens).  
- Implement account lockout or rate-limiting on repeated failed logins to stop brute force attempts.  
- Avoid exposing verbose error messages that confirm valid usernames.


