---
type: problem
status: seed
tags:
  - nilm/problem
  - nilm/foundations
---
# Load Disaggregation

## Phát biểu bài toán (khung)

Cho chuỗi đo tổng hợp tại điểm đo chung, ước lượng chuỗi tiêu thụ hoặc trạng thái của một hay nhiều thiết bị cấu thành tổng tải. Bài toán là một nhánh cốt lõi của [[NILM là gì]].

## Ký hiệu tham khảo

- (y_{1:T}): quan sát tổng hợp trong khoảng thời gian (1..T).
- (x_{i,1:T}): tín hiệu phụ tải của thiết bị (i).
- (z_{i,t}): trạng thái thiết bị (nếu dùng mô hình trạng thái rời rạc).
- (\epsilon_t): nhiễu và phần tải chưa giải thích.

Một giả định cộng thường dùng là (y_t \approx \sum_i x_{i,t}+\epsilon_t), nhưng cần nêu rõ khi áp dụng.

## Những lựa chọn phải ghi trong một nghiên cứu

- **Đầu vào**: đại lượng đo, tần số lấy mẫu, số pha, vị trí đo.
- **Đầu ra**: công suất tức thời, năng lượng theo cửa sổ, trạng thái, hoặc nhãn hoạt động.
- **Danh sách tải**: tập thiết bị đã biết hay tải mở.
- **Thiết lập**: giám sát/không giám sát, cá thể hóa/tổng quát, offline/online.
- **Ràng buộc**: dữ liệu huấn luyện sẵn có, độ trễ, tính riêng tư, tải chưa thấy.
- **Đánh giá**: sai số công suất, sai số năng lượng, F1 trạng thái/sự kiện, và giao thức chia tập.

## Giả định và giới hạn

Tách các giả định vật lý (ví dụ phép đo tổng hợp) khỏi giả định dữ liệu (ví dụ nhãn đầy đủ) và giả định mô hình (ví dụ số trạng thái hữu hạn). Mọi benchmark cần chỉ rõ thiết bị không có trong tập huấn luyện và quy tắc đồng bộ dữ liệu.

## Nguồn và ghi chú

- Chưa gắn nguồn; bổ sung trích dẫn cho từng biến thể phát biểu và giao thức đánh giá.
