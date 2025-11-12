# PostmanRepo
Postman collection containing automated API tests for user management endpoints (Create, Read, Update, Delete). Includes environment variables, assertions, and Newman-compatible scripts for CI/CD integration.

## ▶️ Run with Newman (locally)

1. Install Newman:
🔹```bash
npm install -g newman
🔹```

2. Run a collection with environment:
🔹```bash
newman run collections/GoREST_API.json -e environment/GoREST_Env.json
newman run collections/Booking_API.json -e environment/Booking_Env.json
🔹```

3. Create a reports folder:
🔹```bash
mkdir -p newman-report
🔹```

4. Run with HTML report:
🔹```bash
newman run collections/GoREST_API.json -e environment/GoREST_Env.json -r cli,html --reporter-html-export newman-report/GoREST_Report.html

newman run collections/Booking_API.json -e environment/Booking_Env.json -r cli,html --reporter-html-export newman-report/Booking_Report.html
🔹```
