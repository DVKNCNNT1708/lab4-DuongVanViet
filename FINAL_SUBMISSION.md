# FINAL SUBMISSION EVIDENCE

## 1. Required files included

- Dockerfile
- .dockerignore
- .env.example
- RUN_LOCAL.md
- contracts/iot-ingestion.openapi.yaml
- postman/collections/FIT4110_lab04_iot_docker.postman_collection.json
- postman/environments/FIT4110_lab04_local.postman_environment.json
- reports/newman-lab04-local.xml
- reports/newman-lab04-local.html
- HEALTH_EVIDENCE.md
- build_evidence_utf8.txt
- run_evidence_utf8.txt

## 2. Docker image tags

- fit4110/iot-ingestion:lab04
- fit4110/iot-ingestion:v0.1.0-duongvanviet

## 3. Build evidence

See `build_evidence_utf8.txt` for the full Docker build output.

## 4. Run evidence

See `run_evidence_utf8.txt` for the container run output.

## 5. Health endpoint evidence

See `HEALTH_EVIDENCE.md` for container health status and health endpoint JSON response.

## 6. Notes

- The service is running in Docker successfully.
- The `/health` endpoint returns HTTP 200 with correct JSON.
- Newman reports are already generated in `reports/`.
- This file is added as the final submission summary.
