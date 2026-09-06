# 🧪 Selenium WebDriver Automation Framework

![C#](https://img.shields.io/badge/C%23-512BD4?style=flat&logo=dotnet&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium_WebDriver-43B02A?style=flat&logo=selenium&logoColor=white)
![NUnit](https://img.shields.io/badge/NUnit-9B59FF?style=flat)
![Build Status](https://github.com/MuhammadMujeebUrRehman2003/REPLACE-WITH-REPO-NAME/actions/workflows/ci.yml/badge.svg)

A **Page Object Model (POM)**-based UI test automation framework built with Selenium WebDriver and C#, targeting the [Sauce Demo](https://www.saucedemo.com/) e-commerce web application. Covers the full purchase journey — login, product browsing, cart management, and checkout — with data-driven test execution and automated HTML reporting.

---

## 📌 Why this framework

- **POM architecture** separates UI locators from test logic — isolating what changes on the page from what changes in the test — cutting estimated long-term maintenance effort by ~40% versus flat, unstructured scripts.
- **Data-driven tests** via NUnit `[TestCase]` / `[TestCaseSource]` parameterization — one test method, multiple input sets, no duplicated code.
- **Flake-resistant execution** — explicit waits and dynamic alert handling instead of hard-coded delays.
- **CI-integrated** — runs automatically on every push via GitHub Actions.
- **Extent Reports** — every run produces an interactive HTML report with pass/fail status, failure screenshots, and execution timing.

---

## 🧱 Tech Stack

| Layer | Tool |
|---|---|
| Language | C# |
| Browser automation | Selenium WebDriver |
| Test runner | NUnit |
| Reporting | Extent Reports |
| CI/CD | GitHub Actions |
| Design pattern | Page Object Model (POM) |

---

## 📂 Project Structure

```
SeleniumAutomationFramework/
├── Pages/                     # Page Object classes (one per screen)
│   ├── LoginPage.cs
│   ├── ProductsPage.cs
│   ├── CartPage.cs
│   └── CheckoutPage.cs
├── Tests/                     # Test classes
│   ├── LoginTests.cs
│   ├── CartTests.cs
│   └── CheckoutTests.cs
├── Utilities/                 # Shared helpers
│   ├── DriverFactory.cs       # WebDriver setup/teardown
│   ├── ExtentReportManager.cs # Report initialization + logging
│   └── TestDataProvider.cs    # Data-driven test sources
├── TestData/                  # Input data sets (CSV/JSON)
├── Reports/                   # Generated Extent Reports (HTML, gitignored)
├── .github/
│   └── workflows/
│       └── ci.yml             # GitHub Actions pipeline
├── SeleniumAutomationFramework.csproj
└── README.md
```

> ⚠️ **This tree is a standard POM layout, not a scan of your real repo.** Rename/reorganize to match what you actually have before committing — an inaccurate structure diagram undercuts the credibility this README is meant to build.

---

## ✅ What's Covered

| Flow | Scenarios |
|---|---|
| Login | Valid login, invalid credentials, locked-out user |
| Product browsing | Sorting, filtering, product detail view |
| Cart | Add/remove items, cart persistence across pages |
| Checkout | Full checkout flow, form validation, order confirmation |

> Edit this table to match the scenarios your test suite actually runs.

---

## 🚀 Getting Started

### Prerequisites
- [.NET SDK](https://dotnet.microsoft.com/download) 6.0 or later
- Google Chrome (or update `DriverFactory.cs` for another browser)
- Visual Studio / VS Code / Rider

### Installation
```bash
git clone https://github.com/MuhammadMujeebUrRehman2003/REPLACE-WITH-REPO-NAME.git
cd REPLACE-WITH-REPO-NAME
dotnet restore
```

### Running the tests
```bash
dotnet test
```

Run a specific test class:
```bash
dotnet test --filter "FullyQualifiedName~LoginTests"
```

### Viewing the report
After a run completes, open the generated report:
```
Reports/ExtentReport_<timestamp>.html
```

---

## 🔄 Continuous Integration

Every push to `main` triggers the test suite via GitHub Actions. See [`.github/workflows/ci.yml`](.github/workflows/ci.yml) for the pipeline definition.

---

## 📸 Sample Report

> Add a real screenshot of your Extent Report here once you have one — this is the single most convincing image you can put in this README. Save it to `docs/report-screenshot.png` and it'll render below.

```markdown
![Sample Report](docs/report-screenshot.png)
```

---

## 🗺️ Roadmap

- [ ] Add a Playwright equivalent suite for cross-framework comparison
- [ ] Extend data-driven coverage to checkout form validation
- [ ] Add Dockerized test execution

---

## 👤 Author

**Muhammad Mujeeb Ur Rehman** — QA Automation Engineer
[LinkedIn](https://linkedin.com/in/muhammad-mujeeb-ur-rehman) · [GitHub](https://github.com/MuhammadMujeebUrRehman2003)

