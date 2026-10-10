# ĐIỀU EM MUỐN NÓI - ĐOÀN THANH NIÊN XÃ TRÀ LIÊN

Ứng dụng web tiếp nhận ý kiến, tâm tư, nguyện vọng, đề xuất của trẻ em và thanh thiếu nhi trên địa bàn xã Trà Liên.
- **Khẩu hiệu:** "Lắng nghe em nói – Đồng hành cùng em"
- **Đơn vị quản lý:** ĐOÀN THANH NIÊN XÃ TRÀ LIÊN
- **Phong cách giao diện:** Đồng bộ với hệ thống thông tin xã Trà Liên ([Cẩm nang Một cửa xã Trà Liên](https://camnangmotcuaxatralien.vercel.app/))

---

## 🚀 Tính năng nổi bật

### 1. Dành cho Trẻ em & Thanh thiếu nhi (Trang chủ `/`)
- **Giao diện thân thiện, hiện đại:** Tông màu xanh dương, xanh lá và trắng đặc trưng của tuổi trẻ và thiếu nhi, hiển thị tối ưu trên điện thoại và máy tính.
- **Thẻ chức năng nhanh:**
  - 📩 **Gửi ý kiến:** Mở nhanh biểu mẫu chia sẻ.
  - 🏫 **Góp ý về trường học:** Học tập, thầy cô, bạn bè, cơ sở vật chất lớp học.
  - 🛡️ **An toàn trẻ em:** Phòng chống bạo lực, đuối nước, tai nạn thương tích, an toàn trên mạng xã hội.
  - 🌳 **Môi trường sống:** Khu vui chơi thôn xóm, vệ sinh môi trường, sân sinh hoạt.
  - 👥 **Hoạt động Đoàn – Đội:** Sinh hoạt hè, văn nghệ, thể thao, rèn luyện kỹ năng sống.
  - 📖 **Xem hướng dẫn & Cam kết:** Quy trình 3 bước và 4 cam kết bảo mật quyền trẻ em.
- **Biểu mẫu gửi ý kiến an toàn:**
  - Lựa chọn nhóm tuổi: Dưới 11 tuổi, 11 - 15 tuổi, 16 - 18 tuổi, Trên 18 tuổi.
  - Lựa chọn thôn đang sinh sống: Thôn 1 đến Thôn 6 (xã Trà Liên).
  - Chọn chủ đề và nhập nội dung chia sẻ.
  - **Tùy chọn Ẩn danh (Bảo mật 100%):** Không bắt buộc trẻ em cung cấp họ tên, số điện thoại hay địa chỉ.
  - **Thông báo tiếp nhận thành công:** Cấp mã tra cứu riêng dạng `EM-2026-XXXX`.

### 2. Dành cho Cán bộ Đoàn xã (Trang Quản trị `/admin`)
- **Đăng nhập bảo mật:** Xác thực tài khoản cán bộ Đoàn qua Supabase Auth.
- **Thống kê thời gian thực:**
  - Tổng số ý kiến tiếp nhận.
  - Số ý kiến mới tiếp nhận.
  - Số ý kiến đang xử lý.
  - Số ý kiến đã phản hồi / giải quyết.
- **Bộ lọc & Tìm kiếm thông minh:** Tìm theo từ khóa, lọc theo Chủ đề, lọc theo Trạng thái xử lý, lọc theo Thôn.
- **Xử lý ý kiến:** Xem chi tiết toàn văn, cập nhật trạng thái (Mới tiếp nhận / Đang xử lý / Đã phản hồi), ghi chú xử lý nội bộ và nhập phản hồi chính thức cho các em.

---

## 🔒 Phân quyền & Bảo mật (Row Level Security - RLS)

Hệ thống tuân thủ nghiêm ngặt nguyên tắc bảo mật và quyền riêng tư của trẻ em:
- **Người dùng công khai (Trẻ em/ẩn danh):** Chỉ được phép gửi ý kiến (`INSERT`). Tuyệt đối không thể đọc (`SELECT`), sửa (`UPDATE`) hay xóa (`DELETE`) dữ liệu của nhau.
- **Quản trị viên đã xác thực (Authenticated):** Sau khi đăng nhập bằng tài khoản Supabase Auth, cán bộ Đoàn mới được phép đọc (`SELECT`) và cập nhật (`UPDATE`) dữ liệu.

File cấu hình cơ sở dữ liệu và RLS nằm tại: `supabase/schema.sql`.

---

## 🛠️ Hướng dẫn cài đặt & Thiết lập Supabase

### Bước 1: Tạo dự án trên Supabase
1. Truy cập [https://supabase.com](https://supabase.com) và đăng nhập (hoặc đăng ký miễn phí).
2. Nhấn **New Project**, đặt tên (ví dụ: `dieu-em-muon-noi-tra-lien`), chọn khu vực Singapore (gần Việt Nam nhất) và tạo mật khẩu database.

### Bước 2: Chạy Script khởi tạo CSDL & RLS
1. Vào menu **SQL Editor** trong trang quản trị Supabase.
2. Mở file `supabase/schema.sql` trong dự án này, copy toàn bộ nội dung và dán vào SQL Editor.
3. Nhấn **Run**. Bảng `child_opinions` và các chính sách bảo mật RLS sẽ được tạo tự động.

### Bước 3: Tạo tài khoản cán bộ quản trị
1. Vào menu **Authentication** -> **Users** trên Supabase.
2. Nhấn nút **Add user** -> chọn **Create user**.
3. Nhập Email (ví dụ: `doanxatralien@gmail.com`) và Mật khẩu quản trị.
4. Tích chọn **Auto Confirm User?** để kích hoạt ngay mà không cần gửi email xác nhận.
5. Nhấn **Create user**. Đây chính là tài khoản dùng để đăng nhập vào `/admin`.

### Bước 4: Lấy mã kết nối (API Keys)
1. Vào **Project Settings** (biểu tượng bánh răng) -> chọn mục **API**.
2. Sao chép 2 thông tin:
   - **Project URL** (dạng `https://xxxxxxxx.supabase.co`)
   - **anon / public key** (chuỗi ký tự dài)

### Bước 5: Cấu hình biến môi trường
Tạo file `.env.local` ở thư mục gốc (hoặc sửa file `.env.local` có sẵn):
```env
NEXT_PUBLIC_SUPABASE_URL=https://xxxxxxxx.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key-here
```

---

## 💻 Chạy thử nghiệm trên máy cục bộ (Localhost)

```bash
# Cài đặt thư viện (nếu chưa cài)
npm install

# Khởi động máy chủ phát triển
npm run dev
```

Mở trình duyệt truy cập:
- Trang chủ: [http://localhost:3000](http://localhost:3000)
- Trang quản trị: [http://localhost:3000/admin](http://localhost:3000/admin)

---

## 🌐 Hướng dẫn Triển khai lên Vercel (Miễn phí)

### Cách 1: Triển khai qua Vercel Web Dashboard (Khuyên dùng)
1. Đẩy mã nguồn lên tài khoản GitHub của bạn (tạo repository mới).
2. Truy cập [https://vercel.com](https://vercel.com) và đăng nhập bằng GitHub.
3. Nhấn **Add New...** -> **Project** -> Chọn repository chứa mã nguồn này.
4. Tại phần **Environment Variables**, thêm 2 biến:
   - `NEXT_PUBLIC_SUPABASE_URL`: (Dán Project URL từ Supabase)
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`: (Dán anon key từ Supabase)
5. Nhấn nút **Deploy**.
6. Vercel sẽ tự động build và cấp cho bạn đường link website công khai (dạng `https://dieu-em-muon-noi-tra-lien.vercel.app`).

### Cách 2: Triển khai nhanh bằng Vercel CLI
Trong thư mục dự án, chạy lệnh:
```bash
npx vercel
```
Làm theo các bước hướng dẫn trên màn hình, sau đó thêm biến môi trường trên Vercel Dashboard hoặc bằng lệnh `npx vercel env add`.

---

## 🏛️ Đơn vị chủ quản
**ĐOÀN THANH NIÊN CỘNG SẢN HỒ CHÍ MINH XÃ TRÀ LIÊN**
- Trụ sở: UBND xã Trà Liên, huyện Trà Bồng, tỉnh Quảng Ngãi
- Khẩu hiệu: *“Lắng nghe em nói – Đồng hành cùng em”*
