## Phần 1. Phân tích lỗi và Tư duy kỹ thuật

Dưới đây là phân tích về sai lầm trong cách quản lý tài liệu của Nam đối với dự án nhóm "GreenTech" trên GitHub:

1. **Sai lầm 1: Sử dụng Rich Text (File `.docx`) để lưu trữ và quản lý mã nguồn/tài liệu trên Git**
   * *Phân tích:* File Microsoft Word (`.docx`) thực chất là một tệp nén nhị phân (`binary`) chứa nhiều tệp XML bên trong. Hệ thống kiểm soát phiên bản Git được tối ưu hóa cho **Plain Text** (văn bản thô). Khi dùng file `.docx`:
     * GitHub **không thể render trực tiếp** nội dung lên trình duyệt web cho các thành viên xem nhanh.
     * Git không thể so sánh từng dòng chi tiết (Git Diff) mà chỉ xem file nhị phân đó đã thay đổi toàn bộ hay chưa. Chỉ cần Nam sửa một dấu phẩy nhỏ, Git sẽ báo xung đột (Merge Conflict) toàn bộ tệp, khiến các thành viên khác không thể gộp (merge) code được.

2. **Sai lầm 2: Bẫy dữ liệu hư hại file (Data Corruption)**
   * *Phân tích:* Do định dạng nhị phân, nếu tệp `.docx` của Nam bị lỗi truyền tải mạng làm mất dù chỉ $1\text{ byte}$ dữ liệu, cấu trúc gói nén bên trong sẽ bị hỏng hoàn toàn và phần mềm Microsoft Word sẽ báo lỗi không thể mở được tệp (`File is corrupted`). 
   * *Ưu thế tuyệt đối của Markdown (`.md`):* Markdown sử dụng hoàn toàn định dạng **Plain Text**. Nếu file `.md` bị mất hoặc hỏng một vài ký tự, người dùng vẫn có thể dễ dàng mở bằng bất kỳ trình soạn thảo văn bản nào để đọc hoặc sửa chữa thủ công mà không sợ hỏng toàn bộ tài liệu. Ngoài ra, tệp Markdown cực kỳ nhẹ, giúp Git xử lý so sánh dòng lệnh (`diff`) mượt mà và minh bạch.

---

## Phần 2. Hoàn thiện tài liệu chuẩn (`README.md`)

Đoạn văn bản giới thiệu dự án "GreenTech" của Nam đã được chuyển đổi từ định dạng Word sang mã nguồn **Markdown (`.md`)** chuẩn hóa, trực quan:

```markdown
# Giới thiệu dự án GreenTech

GreenTech là dự án hướng tới việc ứng dụng công nghệ để bảo vệ môi trường, giúp cuộc sống xanh và bền vững.

## 1. Mục tiêu
- Tạo ra giải pháp công nghệ xanh.
- Nâng cao ý thức cộng đồng.
- Phát triển bền vững.

## 2. Kỹ thuật & Vận hành
- Giữ hiệu ứng text $\rightarrow$ So sánh dòng chính xác.
- Dễ review, dễ merge, ít xung đột.
- Hiển thị đẹp trên GitHub, có thể xuất PDF.

## 3. Quy trình làm việc nhóm
- Thường xuyên sync với `main`.
- Thảo luận trước khi đổi lớn.
- Làm việc chuẩn quy trình, nhóm mình sẽ hiệu quả hơn!