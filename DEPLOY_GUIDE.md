# Hướng dẫn Triển khai & Sử dụng Portfolio Web (React Flowstate Theme)

Dự án này đã được thiết kế và nâng cấp toàn diện dựa trên phong cách giao diện của [React Flowstate](https://react-flowstate.github.io/) và Docusaurus, kết hợp các kiến thức thực chiến từ cuốn sách **Django for Beginners**.

---

## 🌟 1. Những điểm mới đã được nâng cấp

1. **Giao diện chuẩn React Flowstate & Docusaurus**:
   - Tone màu chủ đạo: **Emerald Green** (`#2e8555` / `#25c2a0` trong dark mode).
   - Hỗ trợ nút chuyển đổi **Dark / Light mode** mượt mà trên thanh Navbar, tự động ghi nhớ tùy chọn vào trình duyệt (`localStorage`).
   - **Hero Banner** ấn tượng với lời chào, vai trò chuyên môn, nút CTA khám phá dự án và đọc blog.
   - **3 Cột Năng lực cốt lõi (Features Grid)** đúng theo layout của trang React Flowstate.
   - **Mục Giới thiệu bản thân (About Me)**: Hồ sơ cá nhân (Profile Card), mục tiêu nghề nghiệp, và ma trận kỹ năng (Backend, Frontend, DevOps) sinh động.
   - **Danh mục Dự án tiêu biểu (Projects Grid)**: Trình diễn các sản phẩm thực tế kèm thẻ công nghệ và liên kết mã nguồn.
   - **Blog kỹ thuật (Dynamic Django Feed)**: Tích hợp trực tiếp dữ liệu từ model `Post` của Django, hỗ trợ phân trang/cắt trích dẫn và các nút chỉnh sửa/xóa nhanh khi đăng nhập.

2. **Trải nghiệm khi Đăng nhập (Authentication UI)**:
   - Khi đăng nhập với tài khoản (ví dụ `hiencao` như trong ảnh của bạn):
     - Navbar hiển thị Avatar và Tên tài khoản `hiencao`, nút `+ Viết bài`, và nút `Đăng xuất`.
     - Hero Banner hiển thị Callout cá nhân hoá chúc mừng đăng nhập với toàn quyền quản trị.
     - Các bài viết blog kích hoạt các nút hành động `Sửa` và `Xóa`.
   - Các trang đăng nhập (`/accounts/login/`), đăng ký (`/accounts/signup/`), tạo bài mới (`/post/new/`), sửa bài (`/post/<id>/edit/`), xóa bài (`/post/<id>/delete/`) đều đã được thiết kế lại theo thẻ card bo góc hiện đại.

---

## 🚀 2. Hướng dẫn Deploy lên GitHub Pages

GitHub Pages là dịch vụ lưu trữ web tĩnh (HTML/CSS/JS). Vì vậy, dự án đã được trang bị sẵn thư mục **`docs/`** hoàn chỉnh:
- Có sẵn `docs/index.html` và `docs/css/base.css`.
- Tích hợp **chức năng Đăng nhập mô phỏng trên nền tảng tĩnh (Client-side Auth)**: Người xem trên GitHub Pages có thể nhấn nút "Đăng nhập" để trải nghiệm trạng thái đã đăng nhập của tài khoản `hiencao`, tạo bài viết mới hoặc xóa bài viết (được lưu trực tiếp trong trình duyệt).

### Các bước kích hoạt GitHub Pages trong 2 phút:

1. **Đẩy mã nguồn lên GitHub**:
   Mở terminal trong thư mục `d:\code\blog` và chạy:
   ```bash
   git add .
   git commit -m "Upgrade portfolio with React Flowstate UI and GitHub Pages build"
   git push origin master
   ```

2. **Cấu hình trên GitHub**:
   - Truy cập vào repository của bạn: [https://github.com/caobaohien/blog-app](https://github.com/caobaohien/blog-app)
   - Chọn tab **Settings** (Cài đặt) ở thanh menu trên cùng.
   - Ở cột bên trái, chọn mục **Pages**.
   - Tại phần **Build and deployment**:
     - **Source**: Chọn `Deploy from a branch`.
     - **Branch**: Chọn nhánh `master`, và ở ô thư mục bên cạnh chọn `/docs`.
     - Nhấn nút **Save**.

3. **Truy cập website**:
   - Sau khoảng 1-2 phút, trang web của bạn sẽ chính thức hoạt động tại địa chỉ:
     👉 **`https://caobaohien.github.io/blog-app/`**

---

## 💻 3. Chạy thử nghiệm Django trên máy nội bộ (Local)

Để chạy phiên bản Django backend đầy đủ (kết nối cơ sở dữ liệu `db.sqlite3`):

1. Mở terminal tại thư mục `d:\code\blog`:
   ```bash
   # Nếu có virtualenv:
   .venv\Scripts\activate

   # Chạy server Django:
   python manage.py runserver
   ```
2. Mở trình duyệt và truy cập:
   - Trang chủ Portfolio: [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
   - Trang Giới thiệu độc lập: [http://127.0.0.1:8000/about/](http://127.0.0.1:8000/about/)
   - Đăng nhập: [http://127.0.0.1:8000/accounts/login/](http://127.0.0.1:8000/accounts/login/)

---

## ☁️ 4. Deploy Django Backend lên Render (Render.com)

Nếu bạn muốn trang web Django động (có cơ sở dữ liệu thực, đăng ký/đăng nhập thực) hoạt động online:
1. Đăng ký tài khoản tại [Render.com](https://render.com/).
2. Chọn **New Web Service** -> Kết nối với repo GitHub của bạn (`caobaohien/blog-app` hoặc `caobaohien/caobaohien.github.io`).
3. Cấu hình cơ bản:
   - **Name**: Đặt tên ứng dụng (ví dụ: `hien-portfolio`)
   - **Region**: Singapore (gần Việt Nam nhất)
   - **Branch**: `master`
   - **Environment**: `Python 3`
   - **Build Command**: `pip install -r requirement.txt && python manage.py collectstatic --no-input && python manage.py migrate`
   - **Start Command**: `gunicorn django_project.wsgi:application`
4. **Cấu hình Python Version (RẤT QUAN TRỌNG)**:
   - Dự án sử dụng **Django 4.0.10**. Mặc định hiện tại Render có thể kéo phiên bản Python 3.14+, trong khi Python 3.13+ đã loại bỏ thư viện chuẩn `cgi` dẫn đến lỗi `ModuleNotFoundError: No module named 'cgi'`.
   - Dự án đã được tạo sẵn file [`.python-version`](file:///d:/code/blog/.python-version) và [`runtime.txt`](file:///d:/code/blog/runtime.txt) cố định phiên bản **`3.10.14`**.
   - Tại mục **Environment Variables** trên Render, bạn cũng có thể thêm biến:
     - Key: `PYTHON_VERSION`
     - Value: `3.10.14`
5. Nhấn **Create Web Service** (hoặc nếu đã tạo rồi thì vào mục **Manual Deploy** -> chọn **Clear build cache & deploy**).
6. Ứng dụng sẽ build thành công và chạy ổn định tại domain `https://<ten-app>.onrender.com`.
