# Lab 1: Setup Failure & Recovery Log (Homework H1)

- **Student Name**: Phạm Gia Hưng
- **GitHub Username**: `pghung2516-netizen`
- **Course**: CSC10014 — Tư duy tính toán (Practical Track)
- **Date**: 2026-10-10

---

## 1. Mục tiêu bài tập H1
Chủ động thử nghiệm phá vỡ môi trường phát triển cục bộ (*break setup*), sau đó chỉ dùng tài liệu hướng dẫn `README.md` để khôi phục hoàn toàn (*recover*), nhằm đảm bảo tính tái lập (*reproducibility*) của dự án.

---

## 2. Nhật ký sự cố & Quy trình khôi phục

### 💥 Sự cố 1: Xóa hoàn toàn môi trường ảo (`.venv`)
* **Hành động gây lỗi**:
  Thực hiện xóa thư mục môi trường ảo:
  ```bash
  rm -rf .venv
  ```
* **Hiện tượng & Lỗi quan sát được**:
  1. Khi chạy ứng dụng `python -m assistant "where is the training office?"` $\rightarrow$ gặp lỗi:
     ```text
     ModuleNotFoundError: No module named 'assistant'
     ```
  2. Khi chạy kiểm thử `pytest -q` $\rightarrow$ gặp lỗi:
     ```text
     zsh: command not found: pytest
     ```
  3. Khi chạy script kiểm tra `python3 scripts/check_env.py` $\rightarrow$ gặp thông báo:
     ```text
     [FAIL] running inside a virtual environment
            -> activate .venv first (see README)
     ```
* **Nguyên nhân**:
  Môi trường Python cục bộ bị mất thư mục cô lập `.venv`, dẫn đến thiếu các gói thư viện đã cài (`pytest`, `requirements.txt`) và mất liên kết cài đặt gói `assistant` ở chế độ editable (`pip install -e .`).

* **Các bước khôi phục (Theo đúng `README.md`)**:
  ```bash
  # 1. Tạo lại môi trường ảo
  python3 -m venv .venv

  # 2. Kích hoạt môi trường
  source .venv/bin/activate

  # 3. Cập nhật pip và cài đặt lại dependencies đã ghim
  pip install --upgrade pip
  pip install -r requirements.txt

  # 4. Cài đặt package assistant ở chế độ editable
  pip install -e .
  ```

* **Kết quả kiểm chứng (Verification)**:
  * Chạy `python scripts/check_env.py` $\rightarrow$ **Tất cả các mục đều đạt `[ OK ]`**.
  * Chạy `pytest -q` $\rightarrow$ **`4 passed in 0.01s (100%)`**.
  * Chạy `python -m assistant "where is the training office?"` $\rightarrow$ Trả lời chính xác: `Training Office: room I.101, open Mon-Fri 07:30-16:30.`

---

### 💥 Sự cố 2: Xung đột tài khoản GitHub SSH khi làm việc nhóm
* **Hành động**: Đẩy nhánh (`git push`) lên remote repository của nhóm.
* **Hiện tượng & Lỗi**:
  ```text
  ERROR: Permission to 25127029-DBDANH/bootcamp-team07.git denied to phamgiah602-art.
  fatal: Could not read from remote repository.
  ```
* **Nguyên nhân**: Máy tính có sẵn SSH key của tài khoản cá nhân cũ (`phamgiah602-art`), trong khi repo môn học được cấp quyền cho tài khoản sinh viên `pghung2516-netizen`.
* **Cách khắc phục**:
  1. Tạo cặp SSH key riêng `id_ed25519_pghung` cho tài khoản sinh viên.
  2. Cấu hình file `~/.ssh/config` với host `github-pghung`.
  3. Đổi remote url sang host mới và push thành công.

---

## 3. Cải tiến cho `README.md`
* Đã bổ sung mục `## Troubleshooting` vào `README.md` để hướng dẫn chi tiết cách xử lý khi gặp lỗi `No module named assistant` (khi quên chạy `pip install -e .`) và lỗi kích hoạt script trên PowerShell Windows.
