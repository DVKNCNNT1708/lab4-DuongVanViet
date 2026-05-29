# HEALTH CHECK EVIDENCE

## Container status

```
NAMES               STATUS                    PORTS
fit4110-iot-lab04   Up 17 minutes (healthy)   0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp
```

## Docker image tags

```
REPOSITORY:TAG                              IMAGE ID       SIZE
fit4110/iot-ingestion:lab04                 9b227dd47448   268MB
fit4110/iot-ingestion:v0.1.0-duongvanviet   9b227dd47448   268MB
```

## /health response

```json
{"status":"ok","service":"iot-ingestion","version":"0.4.0"}
```

## Notes

- Container is healthy and listening on port `8000`.
- Image is tagged with both `lab04` and `v0.1.0-duongvanviet`.
- Health endpoint returns the expected JSON response.
