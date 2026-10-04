# Dự án Demo: Quản lý Nhánh và Giải quyết Xung đột (Merge Conflict)

Dự án này phục vụ mục đích thực hành quy trình quản lý nhánh và xử lý xung đột Merge Conflict thủ công trên Git.

## Nội dung đã qua xử lý xung đột
Đây là phần nội dung được hợp nhất từ cả hai nhánh `main` và `feature-update`:
- Cập nhật từ nhánh `main`: Thêm tính năng khởi tạo hệ thống và tài liệu hóa cơ bản.
- Cập nhật từ nhánh `feature-update`: Bổ sung thông tin chi tiết về tính năng mới và hướng dẫn mở rộng.

---

# BÁO CÁO CÁC BƯỚC THỰC HIỆN VÀ GIẢI QUYẾT XUNG ĐỘT (MERGE CONFLICT)

### Bước 1: Khởi tạo Repository và tạo nhánh `main`
```bash
git init
echo "# Dự án Demo" > README.md
git add README.md
git commit -m "Initial commit on main"
```

### Bước 2: Tạo và chuyển sang nhánh `feature-update`
```bash
git checkout -b feature-update
# Sửa file README.md trên nhánh feature-update
echo "Nội dung cập nhật từ nhánh feature-update" >> README.md
git add README.md
git commit -m "Update README on feature-update"
```

### Bước 3: Quay lại nhánh `main` và thực hiện thay đổi gây xung đột
```bash
git checkout main
# Sửa cùng vị trí/dòng file README.md trên nhánh main
echo "Nội dung cập nhật từ nhánh main" >> README.md
git add README.md
git commit -m "Update README on main"
```

### Bước 4: Thực hiện Merge và phát sinh xung đột (Merge Conflict)
```bash
git merge feature-update
# Thông báo lỗi từ Git:
# CONFLICT (content): Merge conflict in README.md
# Automatic merge failed; fix conflicts and then commit the result.
```

### Bước 5: Xử lý xung đột thủ công
Nội dung file `README.md` lúc bị xung đột có dạng:
```text
<<<<<<< HEAD
Nội dung cập nhật từ nhánh main
=======
Nội dung cập nhật từ nhánh feature-update
>>>>>>> feature-update
```

**Thao tác xử lý:**
1. Mở tệp `README.md` bằng trình biên soạn mã nguồn (VS Code / Vim).
2. Xóa các ký hiệu đánh dấu xung đột (`<<<<<<< HEAD`, `=======`, `>>>>>>> feature-update`).
3. Chỉnh sửa và kết hợp nội dung của cả hai nhánh thành nội dung hoàn chỉnh nhất.

### Bước 6: Hoàn tất quá trình Merge Commit
```bash
git add README.md
git commit -m "Merge branch 'feature-update' into main and resolve merge conflict"
```

### Bước 7: Kiểm tra lịch sử Commit với `git log --graph --oneline`
**Lệnh thực thi:**
```bash
git log --graph --oneline
```

**Kết quả hiển thị (Expected Output):**
```text
*   a1b2c3d (HEAD -> main) Merge branch 'feature-update' into main and resolve merge conflict
|\  
| * e5f6g7h (feature-update) Update README on feature-update
* | i8j9k0l Update README on main
|/  
* m1n2o3p Initial commit on main
```