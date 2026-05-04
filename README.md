[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/3eVFKb4u)
# FIT 4110 SET-UP MÔI TRƯỜNG

Buổi 1 tập trung vào việc đưa máy cá nhân của sinh viên về trạng thái sẵn sàng để học các buổi tiếp theo:

- Cài và kiểm tra Git, Docker, Docker Compose, Node.js, Python hoặc Miniconda.
- Chạy được container Docker cơ bản.
- Tải trước các Docker image dùng trong học phần.
- Chạy được smoke test môi trường lab.
- Tạo và nộp minh chứng học tập trong thư mục `evidence/buoi-01/`.

> Lưu ý: Repo này được dùng qua **GitHub Classroom**. Sinh viên **không clone repo template gốc** nếu chưa nhận bài qua link GitHub Classroom của giảng viên.

---

## 1. Hướng dẫn sử dụng

Quy trình nộp bài gồm 5 bước:

```text
Bước 1. Mở link GitHub Classroom do giảng viên cung cấp.
Bước 2. Accept assignment để GitHub tạo repo bài làm riêng cho em.
Bước 3. Clone repo bài làm của em về máy.
Bước 4. Chạy script kiểm tra môi trường và sinh minh chứng.
Bước 5. Commit + push thư mục evidence/buoi-01/ lên GitHub.
```

---

## 2. Nhận bài qua GitHub Classroom

### 2.1. Mở link bài tập

Giảng viên sẽ gửi link dạng:

```text
https://classroom.github.com/a/xxxxxxxx
```

Sinh viên mở link này bằng trình duyệt và đăng nhập GitHub.

### 2.2. Chọn đúng danh tính trong danh sách lớp

Nếu GitHub Classroom yêu cầu chọn tên hoặc mã sinh viên trong roster, hãy chọn **đúng thông tin của mình**.

Không chọn hộ bạn khác.

### 2.3. Accept assignment

Sau khi bấm **Accept assignment**, GitHub Classroom sẽ tạo một repo bài làm riêng cho em.

Repo thường có dạng:

```text
s01-environment-setup-<github-username>
```

hoặc theo quy ước do giảng viên đặt.

### 2.4. Copy URL repo cá nhân

Sau khi repo được tạo xong, bấm nút **Code** và copy URL HTTPS, ví dụ:

```text
https://github.com/<class-org>/s01-environment-setup-nguyenvana.git
```

---

## 3. Clone repo bài làm về máy

Mở Terminal, Git Bash hoặc PowerShell:

```bash
git clone <URL_REPO_BAI_LAM_CUA_EM>
cd <TEN_REPO_BAI_LAM_CUA_EM>
```

Ví dụ:

```bash
git clone https://github.com/dnu-smart-campus-2026/s01-environment-setup-nguyenvana.git
cd s01-environment-setup-nguyenvana
```

> Không cần tự tạo repo mới. Repo bài làm đã được GitHub Classroom tạo sẵn.

---

## 4. Chạy bài trên macOS hoặc Linux

### 4.1. Cấp quyền chạy script

```bash
chmod +x scripts/*.sh
```

### 4.2. Tải trước Docker image

```bash
./scripts/pull_all.sh
```

Script này sẽ tải các image cần dùng trong học phần, ví dụ:

```text
registry:2
python:3.11-slim
node:20-alpine
postgres:15-alpine
rabbitmq:3-management
eclipse-mosquitto:2
nginx:alpine
traefik:v3.1
prom/prometheus:v2.54.1
grafana/grafana:11.2.0
redis:7-alpine
swaggerapi/swagger-ui:v5.17.14
hello-world:latest
ultralytics/ultralytics:latest-cpu
```

### 4.3. Chạy smoke test

```bash
./scripts/smoke_test.sh
```

### 4.4. Sinh minh chứng Buổi 1

```bash
./scripts/collect_session01_evidence.sh
```

Sau bước này, kiểm tra thư mục:

```bash
ls evidence/buoi-01
```

---

## 5. Chạy bài trên Windows PowerShell

Mở PowerShell tại thư mục repo bài làm của em.

### 5.1. Cho phép chạy script trong phiên hiện tại

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### 5.2. Tải trước Docker image

```powershell
.\scripts\pull_all.ps1
```

### 5.3. Chạy smoke test

```powershell
.\scripts\smoke_test.ps1
```

### 5.4. Sinh minh chứng Buổi 1

```powershell
.\scripts\collect_session01_evidence.ps1
```

Sau bước này, kiểm tra thư mục:

```powershell
Get-ChildItem evidence\buoi-01
```

---

## 6. Nếu dùng Miniconda

Nếu máy dùng Miniconda, hãy tạo môi trường riêng cho học phần:

```bash
conda env create -f environment.yml
conda activate api-platform
python --version
```

Nếu môi trường đã tồn tại, có thể dùng:

```bash
conda activate api-platform
pip install -r requirements.txt
```

Yêu cầu khuyến nghị:

```text
Python 3.11.x
pip 24.x hoặc mới hơn
```

---

## 7. Minh chứng cần nộp

Sau khi chạy script, thư mục `evidence/buoi-01/` cần có các file sau:

```text
evidence/buoi-01/
  README.md
  checklist.md
  known-issues.md
  tool-versions.txt
  docker-version.txt
  compose-version.txt
  hello-world.txt
  smoke-test-result.txt
  image-list.txt
  git-log.txt
  service-boundary.md
```

Ý nghĩa của từng file:

| File | Ý nghĩa |
|---|---|
| `tool-versions.txt` | Phiên bản Git, Docker, Node, Python trên máy em |
| `docker-version.txt` | Thông tin Docker CLI/Engine |
| `compose-version.txt` | Thông tin Docker Compose |
| `hello-world.txt` | Minh chứng Docker chạy được container cơ bản |
| `smoke-test-result.txt` | Kết quả kiểm tra môi trường lab |
| `image-list.txt` | Danh sách Docker image đã có trên máy |
| `git-log.txt` | Lịch sử commit gần nhất |
| `checklist.md` | Checklist tự xác nhận của sinh viên |
| `known-issues.md` | Lỗi còn tồn tại, nếu có |
| `service-boundary.md` | Mô tả Actor, Boundary, Service, Input/Output, API dự kiến và phụ thuộc với service khác của nhóm |

---

## 8. Nộp bài bằng commit và push

Sau khi có minh chứng, chạy:

```bash
git status
git add evidence/buoi-01
git commit -m "Add session 01 environment evidence"
git push
```

Nếu Git báo chưa cấu hình tên/email:

```bash
git config --global user.name "Ho Ten Sinh Vien"
git config --global user.email "email-cua-em@example.com"
```

Sau khi push, mở repo bài làm trên GitHub và kiểm tra xem thư mục `evidence/buoi-01/` đã xuất hiện chưa.

---

## 9. Có cần tạo branch không?

Với Buổi 1 trên GitHub Classroom, thông thường sinh viên có thể commit trực tiếp lên nhánh mặc định của repo bài làm.

Không cần tạo branch riêng, trừ khi giảng viên yêu cầu.

Nếu giảng viên yêu cầu tạo branch, dùng mẫu:

```bash
git checkout -b feat/s1-setup-<ma-sinh-vien>
```

Ví dụ:

```bash
git checkout -b feat/s1-setup-21123456
```

---

## 10. Quy định không được commit

Không commit các loại file sau:

```text
*.doc
*.docx
*.ppt
*.pptx
*.pdf dung lượng lớn
.env chứa mật khẩu thật
file model lớn hơn 100 MB
file dữ liệu lớn không được yêu cầu
```

Repo này có GitHub Actions kiểm tra tự động. Nếu em commit file Word `.doc` hoặc `.docx`, workflow sẽ báo lỗi.

---

## 11. Tiêu chí hoàn thành Buổi 1

Sinh viên được xem là hoàn thành Buổi 1 khi:

- Repo bài làm được tạo từ GitHub Classroom.
- Clone được repo bài làm về máy.
- `docker run --rm hello-world` chạy thành công.
- `docker compose version` chạy thành công.
- `scripts/smoke_test` đã chạy và sinh log.
- Thư mục `evidence/buoi-01/` có đầy đủ minh chứng.
- Đã commit và push minh chứng lên repo bài làm.
- Nếu còn lỗi, đã ghi rõ vào `evidence/buoi-01/known-issues.md`.
- Đã nộp `evidence/buoi-01/service-boundary.md` mô tả Service Boundary của nhóm.

---

## 12. Xử lý lỗi nhanh

### Docker chưa chạy

Mở Docker Desktop và chờ biểu tượng Docker chuyển sang trạng thái running, sau đó chạy lại:

```bash
docker info
```

### Thiếu image

Chạy lại:

```bash
./scripts/pull_all.sh
```

Windows:

```powershell
.\scripts\pull_all.ps1
```

### Lỗi Ultralytics trên Mac Apple Silicon

Nếu thấy cảnh báo khác nền tảng `linux/amd64` và `linux/arm64/v8`, có thể chạy thử:

```bash
docker run --rm --platform linux/amd64 ultralytics/ultralytics:latest-cpu yolo version
```

### Port 5000 hoặc 8081 bị chiếm

Dừng container đang chạy:

```bash
docker ps
docker stop <container_id>
```

Hoặc xem thêm hướng dẫn trong:

```text
docs/troubleshooting.md
```

---

## 13. Câu chốt của Buổi 1

> Không nộp “em đã cài xong”, mà nộp **minh chứng có thể kiểm tra lại được**.
