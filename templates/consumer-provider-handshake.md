# Consumer-Provider Handshake

## Thong Tin Chung

- Lab: FIT4110 Lab 03
- Date: 2026-05-26
- Student: Nguyen Thi Thanh Nha
- Group: Nhom 8 (B1)
- Provider team: Nhom 8 - IoT Ingestion
- Consumer team: Core Business / Analytics
- Provider service: IoT Ingestion
- Consumer service: Core Business consumes `sensor.reading.created`; Analytics consumes `telemetry.ingested`

## Contract

- Contract file: `contracts/iot-ingestion.openapi.yaml`
- Mock base URL: `http://localhost:4010`
- Auth method: Bearer token from Postman environment variable `{{authToken}}`
- Endpoint tested: `POST /events/sensor`

## Smoke Test

### Request

```http
POST /events/sensor
Authorization: Bearer {{authToken}}
X-Correlation-Id: fit4110-lab03-group8-0001
Idempotency-Key: iot-dev-001-20260519-0001
Content-Type: application/json
```

```json
{
  "deviceId": "IOT-DEV-001",
  "zoneId": "ZONE-A1",
  "measurement": {
    "sensorType": "TEMPERATURE",
    "value": 31.5,
    "unit": "CELSIUS"
  },
  "timestamp": "2026-05-19T02:59:58Z",
  \"metadata\": {}
}
```

### Expected Response

```json
{
  "eventId": "0196fb3d-4ad7-7d1e-9f49-5d5148d2b101",
  "status": "ACCEPTED",
  "publishedEvents": [
    "sensor.reading.created",
    "telemetry.ingested"
  ],
  "acceptedAt": "2026-05-19T03:00:00Z"
}
```

## Ket Qua

- [x] Consumer goi mock thanh cong.
- [x] Consumer parse duoc `eventId`, `status`, va `publishedEvents`.
- [x] Consumer hieu loi 4xx/5xx provider tra ve qua Problem Details.
- [x] Co Newman report trong `reports/newman-report-mock.xml`.

## Ghi Chu Thay Doi Hop Dong

| Noi dung | Truoc | Sau | Nguoi dong y |
|---|---|---|---|
| Sensor ingestion endpoint | Template dung `/readings` | Dung `/events/sensor` theo Lab 02 IoT Ingestion | Provider va Consumer |
| Payload fields | `device_id`, `metric` | `deviceId`, `zoneId`, `measurement`, `timestamp`, `metadata` | Provider va Consumer |
| Success status | `201 Created` | `202 Accepted` vi day la async event forwarding | Provider va Consumer |

## Xac Nhan

- Provider representative: Nguyen Thi Thanh Nha - Nhom 8/B1 IoT Ingestion
- Consumer representative: Core Business / Analytics representative - agreed for Lab 03 mock contract

