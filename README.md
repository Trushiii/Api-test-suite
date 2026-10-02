# Restful-Booker API Test Suite

![API Tests](https://github.com/YOUR_USERNAME/api-test-suite/actions/workflows/api-tests.yml/badge.svg)

A production-grade API test automation suite built with **Postman** and **Newman**, testing the [Restful-Booker](https://restful-booker.herokuapp.com/apidoc/index.html) public API.

## 🎯 What This Project Demonstrates

- **Chained requests** — auth token from one request feeds protected endpoints
- **Schema validation** — asserts required fields, types, and structure
- **Response time assertions** — catches performance regressions (<500ms on GETs)
- **Environment separation** — dev/prod configs via Postman environments
- **Negative & security testing** — SQL injection, XSS, missing fields, 404s, 403s
- **CI/CD integration** — GitHub Actions runs the suite on every push
- **Rich HTML reports** — Newman htmlextra reporter generates per-collection dashboards

## 📊 Test Coverage — 17 Requests / 38 Assertions

| Collection | Requests | Focus |
|---|---|---|
| Authentication | 3 | Token generation, invalid creds, empty body |
| Bookings CRUD | 8 | Create → Get → Update → Patch → Delete → Verify |
| Negative & Security | 6 | Malformed input, SQLi, XSS, unauthorized access |

## 🏗️ Project Structure

```
.
├── .github/workflows/    # CI pipeline
├── collections/          # Postman collections (3)
├── environments/         # Dev + Prod configs
├── reports/              # Generated HTML reports
└── package.json
```

## 🚀 How to Run

```bash
# Install dependencies
npm install

# Run all collections
npm run test:all

# Run individual collections
npm run test:auth
npm run test:bookings
npm run test:negative

# Reports are auto-generated in reports/
```

## 🔄 CI/CD

Every push to `main` triggers:
1. Install dependencies (`npm ci`)
2. Run all 3 collections via Newman
3. Upload HTML reports as artifacts (14-day retention)

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Test Framework | Postman Collections (v2.1.0) |
| CLI Runner | Newman |
| Reporting | newman-reporter-htmlextra |
| CI/CD | GitHub Actions |
| Target API | Restful-Booker (public demo API) |

## 📌 Key Design Decisions

**Why chained requests?**
Real APIs require auth tokens to be passed between requests. Testing them in isolation misses the biggest integration risk — the token actually working on protected endpoints.

**Why assert response times?**
API tests that pass functionally but take 3 seconds each are still broken. Adding response-time assertions catches performance drift before it becomes a production incident.

**Why dedicated security tests?**
Every API should survive SQL injection and XSS attempts. Asserting the server doesn't leak SQL errors or execute scripts is a minimum bar for any public-facing service.

## 👩‍💻 Author

**Tharushi Gandarawaththa** — QA & Automation Engineer

- Portfolio: [your-portfolio-url]
- LinkedIn: [linkedin.com/in/tharushi-gandarawaththa-2144122a9](https://www.linkedin.com/in/tharushi-gandarawaththa-2144122a9/)
- GitHub: [github.com/Trushiii](https://github.com/Trushiii)

---

*Built as part of my QA internship preparation portfolio.*