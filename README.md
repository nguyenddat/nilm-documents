# NILM Research Vault

Kho ghi chú nghiên cứu về **Non-Intrusive Load Monitoring (NILM)**, tập trung vào định nghĩa, phát biểu bài toán, giả định, dữ liệu, phương pháp và bằng chứng thực nghiệm.

## Bắt đầu

- Mở thư mục này như một vault trong Obsidian.
- Dùng [[Home]] làm trang điều hướng.
- Thêm ghi chú theo mẫu trong `Templates/` để chúng xuất hiện trong các bảng `.base`.

## Cấu trúc

- `Concepts/`: thuật ngữ và định nghĩa.
- `Problems/`: bài toán, biến đầu vào/đầu ra, giả định và tiêu chí đánh giá.
- `Methods/`: phương pháp, mô hình và thuật toán.
- `Datasets/`: bộ dữ liệu và đặc tính đo lường.
- `Papers/`: ghi chú bài báo.
- `Library/Papers/`: bản paper gốc để agent đọc, giữ nguyên sau khi tải về.
- `Questions/`: câu hỏi nghiên cứu còn mở.
- `Bases/`: bảng tra cứu Obsidian Bases.
- `Templates/`: mẫu ghi chú có frontmatter chuẩn.

## Metadata chuẩn

Mỗi ghi chú nghiên cứu nên có `type`, `status`, `tags`, và liên kết liên quan. Giá trị `type` được dùng bởi các Bases: `concept`, `problem`, `method`, `dataset`, `paper`, `question`.

Các trạng thái gợi ý: `seed`, `developing`, `reviewed`, `stable`. Ghi nguồn và số trang/định danh bài báo khi thêm định nghĩa hoặc kết luận từ tài liệu.

## Paper gốc và agent đọc báo

Lưu PDF và tài liệu nguồn vào `Library/Papers/`. Xem `Library/README.md` và `Library/AGENT_READ_PAPERS.md` để biết quy ước đặt tên, lập chỉ mục và quy trình đọc. Agent chỉ đọc thư mục này; mọi ghi chú, trích xuất hoặc chỉ mục cập nhật phải được ghi ở ngoài thư mục paper gốc.
