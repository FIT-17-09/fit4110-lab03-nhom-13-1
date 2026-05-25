# Consumer-Provider Handshake

## Thong tin chung

- Lab: FIT4110 Lab 03
- Ngay: 25/05/2026
- Provider team: Nhom 13
- Consumer team: Dashboard/UI hoac service phu thuoc can doc du lieu analytics
- Provider service: Analytics Service
- Consumer service: Consumer-side smoke test trong Postman/Newman

## Contract

- Contract file: `contracts/nhom-13.openapi.yaml`
- Mock base URL: `http://localhost:4010`
- Auth method: Khong yeu cau auth cho cac endpoint mock hien tai; bien `authToken` van duoc khai bao trong environment de mo rong.
- Postman environment: `postman/environments/nhom-13_mock.postman_environment.json`
- Postman collection: `postman/collections/nhom-13.postman_collection.json`

## Endpoint duoc test

| Endpoint | Method | Muc dich |
|---|---|---|
| `/health` | GET | Kiem tra service con hoat dong |
| `/analytics/daily-summary?date=2026-05-02` | GET | Lay tong hop du lieu analytics theo ngay |
| `/analytics/access/hourly?date=2026-05-02` | GET | Lay du lieu luot truy cap theo gio |
| `/analytics/temperature/average?date=2026-05-02` | GET | Lay nhiet do trung binh |
| `/analytics/alerts/daily?date=2026-05-02` | GET | Lay so luong canh bao theo ngay |
| `/dashboard/overview?date=2026-05-02` | GET | Lay du lieu tong quan cho dashboard |

## Smoke test

Request:

GET /dashboard/overview?date=2026-05-02  
Host: localhost:4010

Expected response includes:

- `date`
- `cards`
- `type`
- `title`
- `value`
- `unit`

## Ket qua

- [x] Consumer goi mock thanh cong.
- [x] Consumer parse duoc field can dung: `date`, `cards`, `type`, `title`, `value`, `unit`.
- [x] Consumer co negative test cho truong hop thieu query parameter `date`.
- [x] Co Newman report: `reports/newman-report.html`.
- [x] Co JUnit XML report: `reports/newman-report-mock.xml`.
- [x] Co contract lint report: `reports/contract-lint-report.txt`.

## Ghi chu thay doi hop dong

| Noi dung | Truoc | Sau | Nguoi xac nhan |
|---|---|---|---|
| Contract source | Lab 02 `openapi.yaml` | Lab 03 `contracts/nhom-13.openapi.yaml` | Nhom 13 |
| Nullable fields | `type: [string, null]` | `type: string` + `nullable: true` | Nhom 13 |
| Constant values | `const` | `enum` | Nhom 13 |
| Mock base URL | Chua cau hinh | `http://localhost:4010` | Nhom 13 |

## Ket luan

Provider contract da duoc kiem tra bang Spectral, mock server da chay bang Prism, va consumer-side smoke test da chay thanh cong bang Newman.