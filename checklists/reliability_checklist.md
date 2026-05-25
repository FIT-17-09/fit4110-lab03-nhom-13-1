# Reliability Checklist - FIT4110 Lab 03

Checklist truoc khi nop Lab 03 cho Nhom 13 - Analytics Service.

## 1. Functional tests

- [x] Co test cho endpoint health: `GET /health`.
- [x] Co test happy path cho endpoint chinh: `GET /dashboard/overview?date=2026-05-02`.
- [x] Co kiem tra status code 2xx.
- [x] Co kiem tra field quan trong trong response: `status`, `service`, `date`, `cards`.
- [x] Co test doc du lieu tong hop/danh sach thong qua `cards`.

## 2. Auth tests

- [x] Co folder `02_Auth` trong Postman collection.
- [x] Endpoint public duoc khai bao ro: `/health` khong yeu cau auth.
- [x] Bien `authToken` da duoc khai bao trong environment de mo rong.
- [x] Auth behavior hien tai duoc ghi chu trong handshake: cac endpoint mock hien tai khong yeu cau auth.
- [ ] Chua co endpoint bat buoc 401/403 trong contract hien tai, nen missing/invalid token test chi dung o muc ghi chu/public endpoint.

## 3. Negative tests

- [x] Co test truong hop thieu query parameter bat buoc `date`.
- [x] Negative test dat trong folder `03_Negative`.
- [x] Expected status cho request loi duoc xac dinh la `400/422`.
- [x] Loi duoc kiem tra bang assertion trong Newman.
- [ ] Chua co request body POST/PUT nen khong co test thieu field body.

## 4. Boundary tests

- [x] Co test gia tri bien cho ngay: `date=2026-01-01`.
- [x] Boundary test dat trong folder `04_Boundary_Reliability`.
- [x] Co ghi chu expected behavior: `200/400/404`.
- [x] Co kiem tra response time duoi 1000ms.
- [ ] Contract hien tai khong co pagination/limit nen khong ap dung test pagination.

## 5. Reliability tests co ban

- [x] Co kiem tra response time.
- [x] Co mock server bang Prism tai `http://localhost:4010`.
- [x] Co consumer-side smoke test trong folder `05_Consumer_side_Smoke`.
- [x] Co local-only non-functional folder `06_Local_only_NonFunctional`.
- [x] Co contract lint bang Spectral.
- [x] Co Newman test chay tren mock environment.
- [ ] Retry/idempotency chua ap dung vi contract hien tai chi co GET endpoint.

## 6. Evidence

- [x] Contract file: `contracts/nhom-13.openapi.yaml`.
- [x] Collection export JSON: `postman/collections/nhom-13.postman_collection.json`.
- [x] Environment mock export JSON: `postman/environments/nhom-13_mock.postman_environment.json`.
- [x] Newman report HTML: `reports/newman-report.html`.
- [x] Newman report XML: `reports/newman-report-mock.xml`.
- [x] Spectral lint report: `reports/contract-lint-report.txt`.
- [x] Test-case matrix da dien: `templates/test-case-matrix.csv`.
- [x] Consumer-provider handshake da dien: `templates/consumer-provider-handshake.md`.

## 7. Final result

- [x] Spectral lint: pass.
- [x] Prism mock server: run successfully.
- [x] Newman collection run: pass, 0 failed assertions.
- [x] Evidence files are stored in `reports/`.