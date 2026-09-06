# 🔬 Manual + API Testing Suite

![Manual Testing](https://img.shields.io/badge/Manual_Testing-1E90FF?style=flat)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat&logo=postman&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?style=flat&logo=jira&logoColor=white)
![RTM](https://img.shields.io/badge/RTM-546E7A?style=flat)

A structured manual and API test suite for the [Sauce Demo](https://www.saucedemo.com/) e-commerce web application — 50+ test cases mapped to a Requirements Traceability Matrix, plus REST API validation via Postman across the core CRUD methods.

Unlike the [Selenium framework repo](REPLACE-WITH-SELENIUM-REPO-LINK), this project isn't meant to be *run* — it's meant to be *reviewed*. The value here is in the documentation artifacts: test case design, traceability, defect reporting, and API contract validation.

---

## 📌 What's in here

- **50+ structured test cases** — positive, negative, boundary value, and equivalence partitioning — covering login, product listing, sorting, cart, and checkout
- **Requirements Traceability Matrix (RTM)** — every test case mapped back to a requirement, so coverage gaps are visible at a glance
- **Postman collection** — REST API checks across GET/POST/PUT/PATCH/DELETE, validating status codes (200, 400, 401, 404) and response data
- **Defect reports** — bugs logged with reproduction steps, expected vs. actual results, severity/priority, and screenshots
- **Gherkin-style scenarios** (Given/When/Then) for the highest-traffic flows, for easier review by non-technical stakeholders

---

## 📂 Repository Structure

```
ManualAPITestingSuite/
├── TestCases/
│   └── TestCases.xlsx              # All 50+ test cases (ID, steps, expected result, status)
├── RTM/
│   └── RequirementsTraceabilityMatrix.xlsx
├── APITests/
│   ├── SauceDemoAPI.postman_collection.json
│   └── SauceDemoAPI.postman_environment.json
├── BugReports/
│   ├── BUG-001-cart-total-mismatch.md
│   └── screenshots/
├── docs/
│   └── test-summary.png            # Coverage/pass-fail snapshot
└── README.md
```

> ⚠️ Same note as the Selenium repo: this is a template structure. Match it to whatever you actually organized — don't commit a tree that doesn't reflect the real folders.

---

## ✅ Test Coverage Summary

| Module | Test Cases | Type Coverage |
|---|---|---|
| Login | 12 | Positive, negative, boundary |
| Product Listing / Sorting | 10 | Positive, equivalence partitioning |
| Cart | 14 | Positive, negative |
| Checkout | 16 | Positive, negative, boundary |

> Replace the numbers with your real counts from the RTM — these are placeholders matching the "50+" total you've cited elsewhere.

---

## 🔌 API Testing

Endpoints validated via Postman, covering standard REST methods and expected status codes:

| Method | Purpose | Status Codes Validated |
|---|---|---|
| GET | Retrieve resource | 200, 404 |
| POST | Create resource | 201, 400 |
| PUT | Full update | 200, 400 |
| PATCH | Partial update | 200, 400 |
| DELETE | Remove resource | 200/204, 401 |

### Running the API checks yourself
1. Import `APITests/SauceDemoAPI.postman_collection.json` and the matching environment file into Postman
2. Select the imported environment
3. Run the collection via the Collection Runner, or individually per request

---

## 🐛 Defect Reporting

Each defect in `BugReports/` follows a consistent format:

```markdown
## BUG-XXX: [Short title]
**Severity:** High / Medium / Low
**Priority:** P1 / P2 / P3

**Steps to Reproduce:**
1. ...
2. ...

**Expected Result:** ...
**Actual Result:** ...

**Screenshot:** ![](screenshots/BUG-XXX.png)
```

> Move your real logged defects into this structure — even 3-4 well-documented ones are more convincing than a claim of "15+ bugs" with none visible.

---

## 🤖 Optional: Automate the API checks in CI

The manual test cases stay manual by nature, but the Postman collection doesn't have to. Running it via [Newman](https://github.com/postmanlabs/newman) (Postman's CLI runner) in GitHub Actions turns this from "I tested the API" into "here's a green checkmark proving the API contract still holds on every push" — genuinely the highest-leverage addition you could make to this specific repo.

```yaml
# .github/workflows/api-tests.yml
name: API Tests
on: [push, pull_request]
jobs:
  run-postman-collection:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install Newman
        run: npm install -g newman
      - name: Run Postman Collection
        run: newman run APITests/SauceDemoAPI.postman_collection.json -e APITests/SauceDemoAPI.postman_environment.json
```

Once this runs successfully at least once, add:
```
![API Tests](https://github.com/MuhammadMujeebUrRehman2003/REPLACE-WITH-REPO-NAME/actions/workflows/api-tests.yml/badge.svg)
```

---

## 👤 Author

**Muhammad Mujeeb Ur Rehman** — QA Automation Engineer
[LinkedIn](https://linkedin.com/in/muhammad-mujeeb-ur-rehman) · [GitHub](https://github.com/MuhammadMujeebUrRehman2003)

