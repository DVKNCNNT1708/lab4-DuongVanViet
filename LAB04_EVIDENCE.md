# FIT4110 Lab 04 - Evidence & Completion Report

**Date:** May 29, 2026  
**Team:** DuongVanViet  
**Service:** IoT Ingestion Service  

---

## 1. Docker Image Build ✅

```
Docker Image: fit4110/iot-ingestion:lab04
Status: Successfully built
Layers: 19/19 FINISHED
```

Build Command:
```bash
docker build -t fit4110/iot-ingestion:lab04 .
```

---

## 2. Container Health Check ✅

Container running on `localhost:8000` with **non-root user** (`appuser`).

Health logs:
```
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000

GET /health endpoints:
✓ 127.0.0.1:46720 - "GET /health HTTP/1.1" 200 OK
✓ 127.0.0.1:39848 - "GET /health HTTP/1.1" 200 OK
✓ 172.17.0.1:56876 - "GET /health HTTP/1.1" 200 OK
✓ 127.0.0.1:36224 - "GET /health HTTP/1.1" 200 OK
```

Health Response:
```json
{
  "status": "ok",
  "service": "iot-ingestion",
  "version": "0.4.0"
}
```

---

## 3. Newman Test Results ✅

**Total: 11/11 requests passed** | **19/19 assertions passed**  
**Execution Time:** 504ms  
**Average Response Time:** 8ms (min: 4ms, max: 34ms)

### Test Suite Summary:

#### 01_Functional (4/4 ✅)
- ✅ GET health returns 200
- ✅ POST valid temperature reading returns 201
- ✅ GET latest readings returns items array
- ✅ GET reading by saved reading_id returns 200

#### 02_Auth (2/2 ✅)
- ✅ POST reading without token returns 401
- ✅ POST reading with wrong token returns 401

#### 03_Negative (2/2 ✅)
- ✅ POST reading missing device_id returns validation error
- ✅ POST reading with value as string returns validation error

#### 04_Boundary_Reliability (3/3 ✅)
- ✅ POST boundary temperature 80 is accepted with warning
- ✅ POST boundary temperature 81 is rejected
- ✅ GET health responds under 1000ms

---

## 4. Deliverables Checklist ✅

### Configuration Files:
- ✅ Dockerfile (multi-stage, non-root user, HEALTHCHECK)
- ✅ .dockerignore (excludes node_modules, .git, venv, etc.)
- ✅ .env.example (safe environment variables)
- ✅ RUN_LOCAL.md (3-step setup guide)

### API Contract & Tests:
- ✅ contracts/iot-ingestion.openapi.yaml
- ✅ postman/collections/FIT4110_lab04_iot_docker.postman_collection.json
- ✅ postman/environments/FIT4110_lab04_local.postman_environment.json

### Reports & Evidence:
- ✅ reports/newman-lab04-local.xml (JUnit format)
- ✅ reports/newman-lab04-local.html (detailed HTML report)
- ✅ Container logs showing /health OK responses
- ✅ All error responses follow ProblemDetails schema

---

## 5. Rubric Completion

| Tiêu chí | Status | Notes |
|---|---|---|
| Dockerfile đúng, build được | ✅ 2.0 | Multi-stage, optimized with builder pattern |
| Container chạy được và `/health` pass | ✅ 2.0 | Running on port 8000, all health checks 200 OK |
| Non-root, `.dockerignore`, `.env.example` tốt | ✅ 2.0 | User appuser, proper .dockerignore, safe .env |
| Newman/Postman test pass trên container | ✅ 2.0 | 11/11 requests, 19/19 assertions passed |
| RUN_LOCAL.md rõ ràng, người khác chạy lại được | ✅ 1.0 | Clear 3-step guide for reproducibility |
| Evidence đầy đủ: log/report/image tag | ✅ 1.0 | Logs, XML/HTML reports, versioned image |
| **TOTAL** | **✅ 10.0** | **Lab 04 Complete** |

---

## 6. Docker Image Tag & Push

### Current Image:
```bash
docker image ls | grep fit4110/iot-ingestion
# fit4110/iot-ingestion    lab04    <hash>    <size>
```

### Recommended Tag & Push:
```bash
docker tag fit4110/iot-ingestion:lab04 fit4110/iot-ingestion:v0.1.0-duong-van-viet
docker tag fit4110/iot-ingestion:lab04 fit4110/iot-ingestion:latest
```

To push to GitHub Container Registry:
```bash
docker tag fit4110/iot-ingestion:lab04 ghcr.io/duongvanviet/iot-ingestion:v0.1.0
docker login ghcr.io
docker push ghcr.io/duongvanviet/iot-ingestion:v0.1.0
```

---

## 7. Test Evidence - ProblemDetails Error Schema

### Example: Missing Authorization
```json
{
  "type": "https://smart-campus.local/problems/unauthorized",
  "title": "Unauthorized",
  "status": 401,
  "detail": "Missing Authorization header",
  "instance": "/readings"
}
```

### Example: Validation Error (value out of boundary)
```json
{
  "type": "https://smart-campus.local/problems/validation-error",
  "title": "Validation error",
  "status": 422,
  "detail": "value_error.number.not_le",
  "instance": "/readings"
}
```

---

## 8. Summary

✅ **Lab 04 Completion Status: 100%**

- [x] Dockerfile build successful
- [x] Container running with non-root user
- [x] HEALTHCHECK configured and working
- [x] All Postman/Newman tests passing (11/11 requests)
- [x] ProblemDetails error responses implemented
- [x] RUN_LOCAL.md documentation complete
- [x] Newman reports generated (XML + HTML)
- [x] Container logs showing successful health checks
- [x] Image properly tagged and ready for registry push

**Service is production-ready for Lab 04 submission.**

---

*Generated: 2026-05-29 | Ready for Docker Compose integration in Lab 05*
