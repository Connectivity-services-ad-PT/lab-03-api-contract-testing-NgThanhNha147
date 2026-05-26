# Reliability Checklist - FIT4110 Lab 03

Student: Nguyen Thi Thanh Nha  
Group: Nhom 8 (B1)  
Service: IoT Ingestion

## 1. Functional Tests

- [x] Co test cho endpoint health.
- [x] Co test happy path cho endpoint chinh `POST /events/sensor`.
- [x] Co kiem tra status code 2xx.
- [x] Co kiem tra field quan trong trong response: `eventId`, `status`, `publishedEvents`, `acceptedAt`.
- [x] Co test doc du lieu chi tiet qua `GET /telemetry/{eventId}` va device status qua `GET /devices/{deviceId}`.

## 2. Auth Tests

- [x] Co test thieu token.
- [x] Co test sai token.
- [x] Endpoint public `/health` duoc khai bao khong can auth.
- [x] Test the hien expected status 401/403 tren local service; tren mock duoc skip co giai thich vi Prism khong enforce auth that.

## 3. Negative Tests

- [x] Co test thieu field bat buoc `deviceId`.
- [x] Co test sai enum `sensorType`.
- [x] Co test gia tri ngoai mien cho boundary AQI.
- [x] Loi tra ve theo Problem Details compatible model.

## 4. Boundary Tests

- [x] Co test gia tri sat nguong: `AIR_QUALITY` value `100000`.
- [x] Co test vuot nguong: `AIR_QUALITY` value `100001`.
- [x] Co test metadata hop le trong payload.
- [x] Co ghi chu ky vong xu ly du lieu bien trong `templates/test-case-matrix.csv`.

## 5. Reliability Tests Co Ban

- [x] Co kiem tra response time cho local service trong folder `06_Local_only_NonFunctional`.
- [x] Co mo ta timeout mong muon trong README/GitHub Actions bang `wait-on`.
- [x] Co test/ghi chu idempotency qua header `Idempotency-Key`.
- [x] Co consumer-side smoke test voi mock provider khac va IoT provider contract.

## 6. Evidence

- [x] Collection export JSON.
- [x] Environment mock export JSON.
- [x] Environment local export JSON.
- [x] Newman report XML/HTML duoc sinh trong `reports/`.
- [x] Test-case matrix da dien.
- [x] Bien ban handshake da dien.
