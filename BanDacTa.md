# BÀI 6: THIẾT LẬP MÔI TRƯỜNG LÀM VIỆC SỐ CHO DOANH NGHIỆP

## 1. Tổng quan dự án

**Tên dự án:** Green-Tech – Trang trại thông minh

**Mục tiêu:**

Xây dựng môi trường làm việc số giúp đội ngũ phát triển quản lý mã nguồn, chia sẻ báo cáo và trao đổi công việc một cách an toàn, hiệu quả.

Dự án sử dụng 3 công cụ chính:

- **GitHub:** Lưu trữ và quản lý mã nguồn cảm biến.
- **Google Drive:** Lưu trữ và chia sẻ báo cáo với nhà đầu tư, đối tác.
- **Lark:** Trao đổi nội bộ, quản lý công việc và giao nhiệm vụ cho đội ngũ kỹ thuật.

---

## 2. Chức năng 1: Thiết lập Hybrid Workflow

### 2.1. Mô hình hoạt động

Áp dụng mô hình Hybrid Workflow kết hợp giữa Local và Cloud:

- **Local:** Mỗi thành viên lập trình trên máy tính cá nhân.
- **Cloud:** Sử dụng GitHub để lưu trữ mã nguồn tập trung.
- **Đồng bộ:** Sau khi hoàn thành công việc, thành viên sử dụng Git để cập nhật mã nguồn lên GitHub.

### 2.2. Quy trình làm việc

1. Thành viên tải mã nguồn từ GitHub về máy tính bằng lệnh `git clone`.
2. Thực hiện lập trình và kiểm tra code trên máy cá nhân.
3. Sử dụng `git add` và `git commit` để lưu lại thay đổi.
4. Sử dụng `git push` để cập nhật code lên GitHub.
5. Trưởng nhóm kiểm tra code trước khi hợp nhất vào nhánh chính (main).

### 2.3. Cấu trúc thư mục lưu trữ

```text
Green-Tech/
│
├── src/
│   └── sensors/
│       ├── temperature.py
│       ├── humidity.py
│       └── soil_moisture.py
│
├── docs/
│   ├── README.md
│   └── technical_report.docx
│
├── reports/
│   └── investor_report.pdf
│
├── config/
│   └── .env.example
│
├── .gitignore
└── requirements.txt
```

**Quy định bảo mật:**

- Không đưa file `.env` chứa mật khẩu cảm biến lên GitHub.
- Thêm `.env` vào file `.gitignore`.
- Chỉ cung cấp `.env.example` chứa tên biến mẫu, không chứa mật khẩu thật.
- Không chia sẻ mật khẩu cảm biến qua kênh chat công khai.
- Bật xác thực hai yếu tố (2FA) cho tài khoản GitHub.

---

## 3. Chức năng 2: Thiết lập phân quyền chia sẻ

Sử dụng Google Drive để quản lý báo cáo và tài liệu dự án.

### 3.1. Cấu trúc thư mục Google Drive

```text
Green-Tech-Shared/
│
├── 01_Bao_Cao_Nha_Dau_Tu/
│   ├── Bao_cao_tien_do.pdf
│   └── Bao_cao_tai_chinh.pdf
│
├── 02_Tai_Lieu_Doi_Tac/
│   ├── Thong_so_thiet_bi.pdf
│   └── De_xuat_thiet_bi.docx
│
└── 03_Tai_Lieu_Noi_Bo/
    ├── Ke_hoach_du_an.docx
    └── Thong_tin_ky_thuat.docx
```

### 3.2. Bảng phân quyền

| Đối tượng | Quyền truy cập | Phạm vi |
|---|---|---|
| Trưởng dự án | Editor | Toàn bộ tài liệu |
| Đội ngũ Dev | Editor | Tài liệu kỹ thuật |
| Nhà đầu tư | Viewer | Chỉ xem báo cáo |
| Đối tác thiết bị | Commenter | Bình luận báo cáo và tài liệu thiết bị |

### 3.3. Quy trình chia sẻ

**Đối với nhà đầu tư:**

- Chọn thư mục `01_Bao_Cao_Nha_Dau_Tu`.
- Nhập email nhà đầu tư.
- Cấp quyền Viewer.
- Không cấp quyền chỉnh sửa hoặc bình luận.

**Đối với đối tác cung cấp thiết bị:**

- Chọn thư mục `02_Tai_Lieu_Doi_Tac`.
- Nhập email đối tác.
- Cấp quyền Commenter.
- Cho phép đối tác nhận xét và góp ý nhưng không được chỉnh sửa nội dung gốc.

**Lưu ý bảo mật:**

- Chỉ chia sẻ cho đúng địa chỉ email.
- Không bật quyền truy cập công khai bằng đường link.
- Không chia sẻ thư mục chứa mã nguồn và file `.env` cho nhà đầu tư hoặc đối tác.
- Kiểm tra quyền truy cập trước khi gửi liên kết.

---

## 4. Chức năng 3: Thiết lập Enterprise Communication

Sử dụng Lark làm không gian giao tiếp và quản lý công việc của đội ngũ Green-Tech.

### 4.1. Cấu trúc Channel

| Channel | Mục đích sử dụng | Thành viên |
|---|---|---|
| #general | Thông báo chung của dự án | Tất cả thành viên |
| #dev-team | Trao đổi về lập trình | Đội Dev |
| #sensor-bugs | Báo lỗi cảm biến | Đội Dev và kiểm thử |
| #technical-support | Hỗ trợ kỹ thuật | Đội kỹ thuật |
| #project-management | Theo dõi tiến độ | Trưởng dự án và các nhóm |

### 4.2. Quy trình chuyển thảo luận thành Task

Khi phát hiện lỗi cảm biến, thành viên thực hiện:

1. Gửi thông báo trong channel `#sensor-bugs`.
2. Mô tả tên cảm biến, tình trạng lỗi và ảnh chụp màn hình.
3. Trưởng nhóm xác nhận lỗi.
4. Chuyển nội dung thảo luận thành một Task trong Lark Tasks.
5. Giao nhiệm vụ cho thành viên phụ trách.
6. Thiết lập Deadline cụ thể.
7. Cập nhật trạng thái công việc: To do, In progress, Done.

**Ví dụ Task:**

- Tên Task: Khắc phục lỗi cảm biến độ ẩm đất.
- Người phụ trách: Thành viên đội Dev.
- Mức độ ưu tiên: High.
- Deadline: 02/11/2026.
- Mô tả: Kiểm tra dữ liệu cảm biến độ ẩm đất trả về không chính xác.
- Trạng thái: In progress.

Việc chuyển thảo luận thành Task giúp tránh bỏ sót lỗi và giúp trưởng dự án theo dõi tiến độ dễ dàng hơn.

---

## 5. Ràng buộc: Bàn giao quyền sở hữu dự án

Khi bài tập nhóm kết thúc, trưởng dự án thực hiện Transfer Ownership để bàn giao quyền sở hữu.

### Quy trình thực hiện:

1. Kiểm tra toàn bộ mã nguồn và tài liệu dự án.
2. Đảm bảo các thành viên đã hoàn thành và cập nhật công việc.
3. Chọn người tiếp nhận quyền sở hữu.
4. Thực hiện chuyển quyền sở hữu Repository trên GitHub cho tài khoản hoặc tổ chức tiếp nhận.
5. Bàn giao quyền quản lý Google Drive và không gian Lark theo quy trình của từng nền tảng.
6. Kiểm tra lại quyền truy cập sau khi bàn giao.

**Lưu ý:** Transfer Ownership trên GitHub không tự động chuyển quyền sở hữu Google Drive hoặc Lark. Cần thực hiện bàn giao riêng trên từng nền tảng.

---

## 6. Kiểm thử: Khôi phục khi thành viên xóa thư mục sensors

### 6.1. Tình huống giả định

Một thành viên vô tình xóa toàn bộ thư mục `src/sensors` trên máy tính và đồng bộ thay đổi lên GitHub.

Điều này có thể khiến mã nguồn cảm biến bị mất khỏi phiên bản hiện tại.

### 6.2. Quy trình khôi phục nhanh nhất

**Trường hợp 1: Đã có bản sao trên GitHub**

Nếu thư mục đã được đẩy lên GitHub trước đó, có thể khôi phục bằng Git.

Mở Terminal tại thư mục dự án và nhập:

```bash
git restore src/sensors/
```

Lệnh này khôi phục thư mục từ phiên bản đã được Git theo dõi trong commit hiện tại.

**Trường hợp 2: Đã commit và push việc xóa lên GitHub**

Nếu thay đổi xóa thư mục đã được commit và push, sử dụng:

```bash
git log --oneline
```

Tìm mã commit trước khi thư mục bị xóa, sau đó khôi phục thư mục từ commit đó:

```bash
git restore --source=MA_COMMIT_CU -- src/sensors/
```

Thay `MA_COMMIT_CU` bằng mã commit thực tế.

Sau đó cập nhật lại mã nguồn:

```bash
git add src/sensors/
git commit -m "Restore deleted sensors folder"
git push
```

**Trường hợp 3: Xóa nhầm thư mục trên Google Drive**

- Mở mục Thùng rác (Trash).
- Tìm thư mục bị xóa.
- Chọn Restore để khôi phục.
- Kiểm tra lại nội dung và quyền truy cập.

### 6.3. Kết quả kiểm thử

Sau khi khôi phục:

- Thư mục `sensors` xuất hiện trở lại.
- Các file mã nguồn cảm biến được khôi phục.
- Kiểm tra code hoạt động bình thường.
- Cập nhật lại GitHub để các thành viên đồng bộ phiên bản mới.

**Kết luận:** Việc sử dụng GitHub và Google Drive giúp dự án có khả năng khôi phục dữ liệu khi xảy ra sự cố, hạn chế nguy cơ mất mã nguồn và tài liệu quan trọng.

---

## 7. Kết luận

Thông qua dự án Green-Tech, em đã xây dựng được môi trường làm việc số kết hợp giữa GitHub, Google Drive và Lark.

- GitHub giúp quản lý mã nguồn theo mô hình Hybrid Workflow.
- Google Drive giúp chia sẻ tài liệu theo đúng quyền hạn của từng đối tượng.
- Lark giúp trao đổi thông tin và chuyển các vấn đề kỹ thuật thành Task có Deadline.
- Transfer Ownership đảm bảo dự án được bàn giao khi kết thúc.
- Git và Google Drive Trash hỗ trợ khôi phục dữ liệu khi xảy ra sự cố.

Mô hình này giúp doanh nghiệp làm việc có tổ chức, bảo mật thông tin và phối hợp hiệu quả hơn.
