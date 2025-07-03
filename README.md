# 🧪 Restful-Booker API Testing with Postman + Jenkins + Email Reporting

This project automates testing of the [Restful-Booker API](https://restful-booker.herokuapp.com) using **Postman**, **Newman**, and **Jenkins CI**, with email notifications for test reports.

---

## 📌 Project Objectives

- Validate all core endpoints of the API (auth, create, get, update, delete)
- Automate the test suite using Jenkins
- Generate HTML reports after execution
- Automatically send test reports via email after each run

---

## 🧰 Tech Stack

| Tool       | Purpose                              |
|------------|---------------------------------------|
| Postman    | API test collection and assertions    |
| Newman     | CLI runner for Postman collections    |
| Jenkins    | Continuous Integration & automation   |
| HTMLExtra  | Rich HTML report generation           |
| Email Ext  | Jenkins plugin for sending reports    |

---

## 📂 Folder Structure
project-root/
├── collection/ # Postman Collection JSON
│ └── API restful-booker.postman_collection.json
├── tests/ # Optional scripts/logs
├── Jenkinsfile or pipeline scripts # CI configuration
├── report/ # HTML report folder
└── README.md


---

## ✅ Covered Endpoints

| Method | Endpoint                   | Description             |
|--------|----------------------------|-------------------------|
| POST   | `/auth`                    | Generate access token   |
| GET    | `/booking`                 | Get all booking IDs     |
| GET    | `/booking/{id}`            | Get single booking      |
| POST   | `/booking`                 | Create new booking      |
| PUT    | `/booking/{id}`            | Full update booking     |
| PATCH  | `/booking/{id}`            | Partial update          |
| DELETE | `/booking/{id}`            | Delete booking          |

Each request includes built-in **tests/assertions** to validate:
- Status code
- Response time
- JSON schema
- Field presence and types
- Business logic checks

---

## 🚀 Running Locally (Newman)

```bash
newman run "collection/API restful-booker.postman_collection.json" \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export report/report.html
```
🔄 CI/CD Pipeline (Jenkins)
- Create a Jenkins pipeline project
- Pull collection from repo
- Run Newman test command (as above)
- Archive generated HTML report
- Send email with report using Email Extension plugin

📧 Email Report Integration
- Plugin: Email Extension Plugin
- SMTP Setup: Configure in Jenkins settings
- Script: Add post-build script or step to send email with HTML report

🧑‍💻 Author
Ahmed ElDamshity
🔗 GitHub — 📧 ahmed.eldamshity25@gmai.com


