# IT-209 DevOps - Session 12: Bài 5

## Chẩn đoán và khắc phục 3 sự cố đứt gãy Pipeline CI/CD thực tế

Dự án này thực hiện phân tích và khắc phục 3 sự cố đứt gãy luồng CI/CD phổ biến trên GitHub Actions trong tệp kịch bản `.github/workflows/broken-pipeline.yml`:

1. **Lỗi 1 (Permission Denied)**: Gradle Wrapper thiếu quyền thực thi khi chạy trên Runner.
2. **Lỗi 2 (Authentication Failed)**: Lỗi đăng nhập Docker Registry do truyền sai tên biến Secret.
3. **Lỗi 3 (Build Context Error)**: Lệnh build Docker Image không tìm thấy file Dockerfile do chỉ định sai thư mục làm việc.

---

## Cấu trúc thư mục dự án

```text
├── .github/
│   └── workflows/
│       └── broken-pipeline.yml       # Tệp kịch bản CI/CD đã sửa lỗi hoàn chỉnh
├── homework/
│   └── session_12/
│       └── ex5/
│           ├── broken-pipeline.yml   # Bản sao kịch bản nộp bài
│           ├── troubleshooting.md    # Báo cáo phân tích và chẩn đoán chi tiết 3 sự cố
│           ├── pipeline-success-overview.png
│           ├── job-steps-detail.png
│           └── packages-result.png
├── gradle/
│   └── wrapper/
├── src/
│   ├── main/java/...
│   └── test/java/...
├── Dockerfile                        # Cấu hình container image cho ứng dụng
├── build.gradle                      # Cấu hình build Gradle cho Spring Boot
├── settings.gradle
├── gradlew
├── gradlew.bat
├── .gitignore
└── README.md
```

---

## Hướng dẫn chạy và kiểm tra

1. Đẩy commit lên GitHub:
   ```bash
   git add .
   git commit -m "Fix 3 broken pipeline issues: gradlew permission, registry token typo, docker build context"
   git push origin main
   ```
2. Truy cập tab **Actions** tại repository `https://github.com/ptitvn/IT-209-Devops-session12-bai5`.
3. Kiểm tra workflow **CI/CD Pipeline** thực thi thành công và chuyển trạng thái tích xanh (**Success**).
4. Xem gói image tại mục **Packages** của repository (`ghcr.io/ptitvn/it-209-devops-session12-bai5:latest`).
