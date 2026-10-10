# Lab 1: Reading Reflection Note (Homework H3)

- **Student Name**: Phạm Gia Hưng
- **GitHub Username**: `pghung2516-netizen`
- **Course**: CSC10014 — Tư duy tính toán (Practical Track)
- **Topics**: MIT Missing Semester (Shell Tools and Scripting) & GitHub Hello World

---

### Reflection Note (3 dòng theo yêu cầu):

1. **Daily command (Lệnh sẽ sử dụng hàng ngày)**:
   `git status` và `grep -rn "pattern" src/` — giúp kiểm tra nhanh chóng trạng thái của nhánh làm việc trước khi commit và tìm kiếm định nghĩa hàm/biến trực tiếp trong mã nguồn từ terminal mà không cần rời bàn phím.

2. **Surprising thing / command (Điều / câu lệnh gây bất ngờ)**:
   Cơ chế kết hợp đường ống (*pipe `|`*) và chuyển hướng (*redirection `>`*) của Unix Shell (như `find . -name "*.py" | wc -l` hoặc dùng `git reflog` để khôi phục commit đã mất) — cho phép kết nối các công cụ nhỏ thành một chuỗi xử lý dữ liệu tự động cực kỳ mạnh mẽ.

3. **Question (Câu hỏi thắc mắc)**:
   Khi làm việc nhóm trong một dự án lớn có nhiều Pull Request mở đồng thời, quy trình chuẩn nhất để đồng bộ các thay đổi mới từ `main` vào nhánh tính năng của mình (giữa `git merge main` và `git rebase main`) để vừa giữ lịch sử commit sạch đẹp vừa tránh rủi ro mất mát code khi giải quyết xung đột (conflict) là gì?
