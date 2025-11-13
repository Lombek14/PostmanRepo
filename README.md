## 🚀 API Test Automation with Postman, Newman, Jenkins & GitHub Actions

**Repo:** https://github.com/Lombek14/PostmanRepo

### ✅ Build Status

| Platform          | Status |
|-------------------|--------|
| **GitHub Actions** | [![Newman CI](https://github.com/Lombek14/PostmanRepo/actions/workflows/newman.yml/badge.svg)](https://github.com/Lombek14/PostmanRepo/actions/workflows/newman.yml) |
| **Jenkins Pipeline** | ![Jenkins pipeline success](images/jenkins-success.png)<br><sub>Local Jenkins demo (screenshot)</sub> |

---
### 🧪 Technologies Used
- Postman / Newman for API automation  
- Jenkins for CI/CD pipeline orchestration  
- GitHub Actions for cloud-based workflow automation  
- Node.js + npm for dependency management

---

### 🧩 What’s Inside
- **Postman collections** (`collections/`)
- **Environments** (`environment/`)
- **Jenkinsfile** for parallel Newman runs
- **GitHub Actions** workflow: `.github/workflows/newman.yml` (matrix builds run collections in parallel)
- **HTML Extra reports** generated on both CI systems and uploaded as artifacts

---

### 🧪 How CI Works

**GitHub Actions (`newman.yml`)**
- Triggers on push/PR/manual.
- Runs **GoREST** and **Booking** collections **in parallel**.
- Generates **htmlextra** HTML reports and uploads them as artifacts.
- Builds a simple `index.html` that links both reports and uploads a combined artifact.

**Jenkins (`Jenkinsfile`)**
- Checks out the repo.
- Installs Newman + htmlextra.
- Runs **GoREST** and **Booking** stages **in parallel**.
- Publishes the HTML report(s) to the job’s “HTML Reports” view.

---

### 📁 Structure

PostmanRepo/
├─ collections/
│ ├─ GoREST_API.json
│ └─ Booking_API.json
├─ environment/
│ ├─ GoREST_Env.json
│ └─ Booking_Env.json
├─ Jenkinsfile
└─ .github/workflows/newman.yml
