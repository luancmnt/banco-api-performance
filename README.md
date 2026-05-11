# Bank API Performance Tests with K6

This repository contains automated performance tests for the banking system API, created using [Grafana K6](https://k6.io/) and written in JavaScript.

🔗 Banking system repository: [github.com/juliodelimas/banco-api](https://github.com/juliodelimas/banco-api)

## 📌 Introduction

The goal of this project is to simulate different loads and usage scenarios for the bank API, check its performance, and find possible bottlenecks. Tests are written to be modular, organized by context, and reusable.

---

## ⚙️ Technologies Used

- [K6](https://k6.io/) – Open-source tool for load and performance testing.
- JavaScript (ES6)
- [GJSON](https://github.com/tidwall/gjson) – For extracting data from JSON responses.
- Environment variables for dynamic configuration (e.g., `BASE_URL`).

---

## 📁 Repository Structure

```
banco-api-performance/
├── fixtures/      # Test input data (e.g., users, payloads)
├── helpers/       # Reusable utility functions for API interaction
├── tests/         # Test cases organized by API module
├── utils /        # Reusable utility functions
├── config/        # Environment variable configuration files
└── README.md      # This file
```

---

## 🗂️ Purpose of Each Folder

- **`fixtures/`**: Input data for tests (e.g., users, payloads)
- **`helpers/`**: Reusable utility functions for API interaction
- **`tests/`**: Test cases organized by API module
- **`utils/`**: Reusable utility functions
- **`config/`**: Environment variable configuration files

---

## 💻 Installation and Running Tests

### 1. Clone the Repository

```bash
git clone https://github.com/luancmnt/banco-api-performance.git
cd banco-api-performance
```

### 2. Set Environment Variables

Edit the config.local.json file and set the base URL of the API to test:

```json
{
    "baseUrl": "http://localhost:3000"
}
```

> 💡 These variables are used in the tests to build requests dynamically.

### 3. Run a Test

```bash
k6 run tests/login.test.js
```

If you are not using config.local.json or automatic loading, pass the BASE_URL variable manually:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

### 4. Live Dashboard + Export Report

You can enable K6’s dashboard mode and export the test report:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
k6 run tests/autenticacao/login.test.js \
-e BASE_URL=http://localhost:3000
```

After the test finishes, the report will be saved as html-report.html.
