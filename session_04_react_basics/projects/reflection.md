### Phần A
Mỗi lần thêm/xóa/toggle 1 todo, bạn phải gọi:
- `setTodos(...)` để cập nhật state của danh sách todos.
- Trong callback xử lý, thường gọi thêm hàm logic để tạo todo mới, loại bỏ todo, hoặc đổi trạng thái todo.
Vậy tổng là 1 hàm set state chính (`setTodos`) và 1 hàm xử lý hành động.

### Phần B
Khi `setTodos(...)` chạy, React sẽ:
- đánh dấu component là cần render lại;
- so sánh state mới với state cũ và thực hiện re-render nếu cần;
- cập nhật DOM ảo rồi đồng bộ với DOM thật.

### Nếu Portfolio của Minh có 50 project
Quản lý danh sách an toàn hơn bằng cách dùng `id` duy nhất cho mỗi project và tránh sửa trực tiếp mảng/đối tượng cũ.
Ví dụ: dùng `projects.map(...)`, `projects.filter(...)` và tạo mảng mới khi thêm/xóa, để giữ tính bất biến và tránh side effect.

### Kết nối Portfolio
Với Portfolio, `useState` lưu mảng project. Khi render, dùng `projects.filter(...)` để lọc theo category, rồi `projects.map(...)` để tạo `ProjectCard` cho mỗi project.
Khi xóa project, gọi `setProjects(projects.filter(p => p.id !== id))`.
Tương tự, thêm project tạo mảng mới `setProjects([...projects, newProject])`.
