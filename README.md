# OpenWeather API Test Automation

This project demonstrates automated API testing using **Postman**, **Newman**, and **GitHub Actions**.
It validates the [OpenWeatherMap API](https://openweathermap.org/api) across positive, negative, and edge scenarios.

---

##  Features

* 30+ API test cases (positive, negative, edge cases, and field validations).
* Automated test execution using **Newman CLI**.
* Continuous validation via **GitHub Actions**.
* HTML test reports generated for every run.
* Collections and environments synced directly from Postman API (always up to date).

---

##  Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

### 2. Postman Setup

* Create a **collection** in Postman with your test cases.
* Create a **Postman environment** containing your variables (e.g. `API_KEY`).
* Copy the **UIDs** for your collection and environment from Postman.

### 3. GitHub Secrets

In your repository:
**Settings → Secrets and variables → Actions → New repository secret**

Add the following secrets:

* `POSTMAN_API_KEY` → Your Postman API key.
* `POSTMAN_COLLECTION_UID` → UID of your Postman collection.
* `POSTMAN_ENV_UID` → UID of your Postman environment.

### 4. CI Workflow

The CI workflow is defined in:

```
.github/workflows/api-tests.yml
```

It performs the following:

1. Fetches the latest collection & environment from Postman API.
2. Runs the collection with Newman.
3. Produces CLI and HTML reports.

---

##  Running Tests Locally

If you want to run Newman locally:

```bash
npm install -g newman
newman run collection.json -e environment.json -r cli,html
```

---

##  Reports

* CLI output is shown directly in GitHub Actions logs.
* HTML reports can be configured as downloadable artifacts for easy review.

---

##  Example Use Cases

* Validate weather data by city name, city ID, and coordinates.
* Handle invalid inputs (wrong city, missing/invalid API key).
* Test edge scenarios such as empty queries and rate-limiting.

---

##  Notes

* Secrets are hidden and never exposed in logs.
* Collection and environment stay synced automatically from Postman.
* This setup can be extended with more advanced workflows (e.g. scheduled runs, matrix testing).
