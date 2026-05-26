# Submission Checklist - Lab 03

Student: Nguyen Thi Thanh Nha  
Group: Nhom 8 (B1)  
Service: IoT Ingestion

## Required Files

- [x] `contracts/iot-ingestion.openapi.yaml`
- [x] `postman/collections/FIT4110_lab03_iot_ingestion.postman_collection.json`
- [x] `postman/environments/FIT4110_lab03_mock.postman_environment.json`
- [x] `postman/environments/FIT4110_lab03_local.postman_environment.json`
- [x] `reports/newman-report-mock.xml`
- [x] `reports/newman-report.html`
- [x] `reports/contract-lint-report.txt`
- [x] `checklists/reliability_checklist.md`
- [x] `templates/test-case-matrix.csv`
- [x] `templates/consumer-provider-handshake.md`

## Notes

- Mock environment is the required runnable evidence for Lab 03.
- Local environment is prepared but depends on a real IoT Ingestion service running at `http://localhost:8000`.
- Auth tests are skipped on mock with explicit assertions because Prism does not enforce real authentication.

## Suggested Final Commit

```bash
git add .
git commit -m "lab03: add IoT ingestion contract tests and newman report"
git push
```
