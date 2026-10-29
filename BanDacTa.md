# GREEN-TECH – KHÔNG GIAN CỘNG TÁC DOANH NGHIỆP

## 1. Giới thiệu dự án

Green-Tech là dự án trang trại thông minh sử dụng cảm biến để theo dõi nhiệt độ, độ ẩm và các thông số môi trường.

Mục tiêu xây dựng không gian cộng tác:
- Lưu trữ và bảo vệ mã nguồn cảm biến.
- Chia sẻ báo cáo an toàn cho nhà đầu tư và đối tác.
- Quản lý trao đổi kỹ thuật, công việc và deadline.
- Hỗ trợ sao lưu và khôi phục dữ liệu khi xảy ra sự cố.

## 2. Cấu trúc Folder

```text
Green-Tech/
├── sensors/
│   ├── temperature.py
│   ├── humidity.py
│   └── README.md
├── reports/
│   ├── investor-report.pdf
│   └── device-feedback/
├── docs/
│   └── project-plan.md
├── backup/
├── .env
├── .env.example
├── .gitignore
└── README.md
```

**Chức năng các thư mục và file:**

- `sensors/`: Chứa mã nguồn xử lý dữ liệu cảm biến.
- `reports/`: Chứa báo cáo dành cho nhà đầu tư và tài liệu góp ý của đối tác.
- `docs/`: Chứa kế hoạch và tài liệu hướng dẫn dự án.
- `backup/`: Lưu các bản sao lưu quan trọng.
- `.env`: Chứa mật khẩu và thông tin bí mật của cảm biến.
- `.env.example`: Chứa tên biến mẫu, không chứa mật khẩu thật.
- `.gitignore`: Ngăn Git theo dõi các file bí mật như `.env`.
- `README.md`: Giới thiệu dự án và hướng dẫn sử dụng.

### Quy định lưu trữ

Dự án sử dụng Hybrid Workflow:
1. Làm việc và kiểm thử code trên máy tính Local.
2. Sử dụng Git để quản lý phiên bản mã nguồn.
3. Đồng bộ hoặc đẩy dữ liệu cần thiết lên Cloud.
4. Sao lưu định kỳ để có thể khôi phục khi xảy ra sự cố.

**Bảo mật:** Không đưa file `.env` lên Git hoặc chia sẻ cho nhà đầu tư, đối tác. Nếu mật khẩu bị lộ, cần thay đổi mật khẩu ngay.

## 3. Cấu trúc Channel

Workspace sử dụng Lark hoặc Slack để trao đổi công việc.

```text
GREEN-TECH WORKSPACE
├── #announcements
├── #general
├── #sensor-iot
├── #development
├── #tasks-deadlines
└── #random
```

- `#announcements`: Thông báo chính thức, lịch họp và deadline quan trọng.
- `#general`: Trao đổi chung về dự án.
- `#sensor-iot`: Thảo luận lỗi cảm biến và dữ liệu thiết bị.
- `#development`: Trao đổi code, Git và kiểm thử.
- `#tasks-deadlines`: Giao việc, người phụ trách và hạn hoàn thành.
- `#random`: Trò chuyện giải trí, không làm ảnh hưởng kênh công việc.

### Quy định giao tiếp

- Đăng thông tin đúng Channel.
- Sử dụng Reply in Thread để giữ các phản hồi cùng chủ đề.
- Khi báo lỗi, cần nêu hiện tượng, kết quả mong đợi và cách đã thử.
- Chuyển lỗi đã xác định thành Task có người phụ trách và deadline.
- Không yêu cầu phản hồi ngay đối với công việc thông thường.

## 4. Quy định phân quyền

| Đối tượng | Quyền truy cập | Phạm vi |
|---|---|---|
| Trưởng dự án | Owner/Editor | Quản lý dự án và phân quyền |
| Đội Dev | Editor | Chỉnh sửa mã nguồn trong phạm vi công việc |
| Nhà đầu tư | Viewer | Chỉ xem báo cáo |
| Đối tác cung cấp thiết bị | Commenter | Nhận xét, góp ý báo cáo |
| Người không liên quan | Không cấp quyền | Không được truy cập |

### Nguyên tắc bảo mật

- Chỉ cấp quyền cần thiết cho từng đối tượng.
- Chia sẻ báo cáo bằng tài khoản cụ thể, không bật quyền công khai nếu không cần thiết.
- Không cấp quyền truy cập `.env` cho nhà đầu tư hoặc đối tác.
- Kiểm tra quyền truy cập định kỳ và thu hồi quyền khi thành viên rời dự án.
- Khi kết thúc bài tập nhóm, thực hiện Transfer Ownership cho người tiếp nhận và kiểm tra lại quyền truy cập.

## 5. Sao lưu và khôi phục

Khi xảy ra sự cố xóa nhầm thư mục `sensors/`:

1. Tạm dừng các thay đổi có thể ghi đè dữ liệu cần khôi phục.
2. Kiểm tra thùng rác Cloud; nếu không có, khôi phục từ Git hoặc bản backup.
3. Kiểm tra file, chạy thử code và thông báo cho nhóm.

## 6. Tổng kết cuối bài

Không gian cộng tác Green-Tech kết hợp lưu trữ Local, Git, Cloud và Backup để bảo vệ mã nguồn. Cấu trúc Channel rõ ràng giúp quản lý trao đổi hiệu quả, trong khi phân quyền phù hợp và bảo vệ `.env` giúp giảm nguy cơ rò rỉ dữ liệu.
