# 📤 PUSH CODE LÊN GITHUB

## Các lệnh Git để submit Lab 04:

```bash
# ========================================
# Bước 1: Kiểm tra status
# ========================================
git status

# ========================================
# Bước 2: Add tất cả files
# ========================================
git add .

# ========================================
# Bước 3: Commit với message rõ ràng
# ========================================
git commit -m "Lab 04: Docker packaging with passing tests

- Fixed HTTPStatus import bug in exception handler
- All tests passing: 11/11 requests, 19/19 assertions
- Dockerfile with multi-stage build, non-root user, HEALTHCHECK
- .dockerignore and .env.example for secure deployment
- RUN_LOCAL.md with 3-step reproducible setup
- Newman reports: XML and HTML
- Container health endpoint responding in <8ms average"

# ========================================
# Bước 4: Push lên GitHub
# ========================================
git push origin main

# ========================================
# Bước 5: Verify push thành công
# ========================================
git log --oneline -5

```

## 📝 Chi tiết từng lệnh:

### 1️⃣ **Add files:**
```bash
git add .
```
- Thêm tất cả modified và untracked files
- Hoặc add individual files: `git add src/iot_app/main.py LAB04_EVIDENCE.md SUBMISSION_CODE.md`

### 2️⃣ **Commit:**
```bash
git commit -m "Lab 04: Docker packaging - All tests passing

- Fixed HTTPStatus import (http module)
- 11/11 requests, 19/19 assertions passed
- Container health check: 200 OK
- Multi-stage Dockerfile with non-root appuser
- HEALTHCHECK configured"
```

### 3️⃣ **Push:**
```bash
git push origin main
```

---

## ✅ Full workflow:

```bash
cd c:\Users\gumba\lab4-DuongVanViet

git add .

git commit -m "Lab 04: Docker packaging - All tests passing (11/11)"

git push origin main

# Verify
git log -1
```

---

## 🔍 Files being pushed:

✅ Modified:
- `src/iot_app/main.py` (HTTPStatus import fix)

✅ New files:
- `LAB04_EVIDENCE.md` (test results + evidence)
- `SUBMISSION_CODE.md` (code reference for submission)
- `package-lock.json` (npm dependency lock)

✅ Unchanged (already in repo):
- Dockerfile
- .dockerignore
- .env.example
- RUN_LOCAL.md
- contracts/iot-ingestion.openapi.yaml
- postman/collections/FIT4110_lab04_iot_docker.postman_collection.json
- postman/environments/FIT4110_lab04_local.postman_environment.json
- reports/newman-lab04-local.xml
- reports/newman-lab04-local.html

---

## 🚀 After push, verify on GitHub:

1. Go to: https://github.com/your-username/FIT4110_lab04_docker_packaging
2. Check the "main" branch
3. Verify commit shows all files
4. Check Actions tab for any CI/CD workflows
