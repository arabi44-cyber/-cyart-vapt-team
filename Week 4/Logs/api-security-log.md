# API Security Testing Log

| Date  | Tool Used      | Test Performed                                        | Result     | Notes                               |
| ----- | -------------- | ----------------------------------------------------- | ---------- | ----------------------------------- |
| Day 1 | Browser, Burp  | Endpoint discovery `/login.php`, `/vulnerabilities/*` | Success    | API endpoints mapped                |
| Day 1 | Postman        | Login request testing                                 | Success    | Valid credentials accepted normally |
| Day 1 | Postman        | Cookie manipulation                                   | Partial    | Requires session token              |
| Day 2 | Postman        | BOLA Test: `/api/users?id=2` using user1 token        | Vulnerable | Access without authorization        |
| Day 2 | SQLMap         | SQL Injection automated test                          | Success    | DB `dvwa` discovered                |
| Day 2 | SQLMap         | Dump table users                                      | Success    | Credentials extracted               |
| Day 2 | Manual         | SQL payload `OR 1=1--`, UNION test                    | Successful | SQLi confirmed                      |
| Day 3 | Browser        | CSRF Page access `/vulnerabilities/csrf/`             | Vulnerable | No CSRF token validation            |
| Day 3 | Manual         | Password reset via CSRF form                          | Success    | Token not required at low level     |
| Day 3 | Security Audit | Header/Config review                                  | Weak       | Missing security headers            |
| Day 3 | Observation    | Passwords hashed with MD5 only                        | Weak       | No salting                          |
| Day 4 | Review         | Prepared checklists, remediation                      | Completed  | Documentation generated             |

---

### Summary of Findings

- **Critical:** SQL Injection, BOLA, CSRF
- **High Risk:** Broken auth session, weak hashing
- **Medium Risk:** Misconfigurations & missing headers
- **Low:** No monitoring or rate-limit protection

DVWA APIs are intentionally insecure and ideal for exploit training.
