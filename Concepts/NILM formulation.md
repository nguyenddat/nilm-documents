---
type: problem
status: reviewed
aliases:
  - NILM formulation
  - Công thức hóa NILM
tags:
  - nilm/formulation
  - nilm/foundations
sources:
  - "[[Papers/contents/zoha-2012-nilm-survey-general-framework-of-nilm|Zoha et al. (2012) – General Framework of NILM]]"
related:
  - "[[NILM là gì]]"
  - "[[Load Disaggregation]]"
---
# NILM formulation

## Notation

| Ký hiệu | Tên gọi | Ý nghĩa |
| --- | --- | --- |
| $t$ | Thời điểm lấy mẫu | Chỉ số thời gian; $t=1,\ldots,T$ là toàn bộ khoảng quan sát. |
| $N$ | Số thiết bị mô hình hóa | Số thiết bị được đưa vào bài toán NILM. |
| $P(t)$ | Công suất tổng | Công suất quan sát tại công tơ chung ở thời điểm $t$. |
| $p_i(t)$ | Công suất thiết bị | Công suất riêng của thiết bị $i$ tại thời điểm $t$. |
| $\varepsilon(t)$ | Nhiễu và phần chưa giải thích | Nhiễu đo, sai số mô hình và công suất của tải chưa được mô hình hóa. |
| $s_i(t)$ | Trạng thái thiết bị | Trạng thái tắt/bật của thiết bị $i$ trong mô hình đơn giản, với $s_i(t) \in \{0,1\}$. |
| $w_i$ | Công suất đặc trưng | Công suất của thiết bị $i$ khi thiết bị bật. |
| $S$ | Tập thiết bị mục tiêu | Tập thiết bị được phân tách khi hệ thống chỉ theo dõi một phần tải. |
| $r(t)$ | Phần công suất còn lại | Công suất của các thiết bị ngoài $S$, tải chưa biết và sai số. |
| $\Delta t$ | Khoảng lấy mẫu | Khoảng thời gian giữa hai mẫu liên tiếp. |
| $\mathbf{P}$ | Vector công suất tổng | Chuỗi công suất tổng theo thời gian. |
| $\mathbf{X}$ | Ma trận tín hiệu thiết bị | Ma trận có cột thứ $i$ chứa chuỗi công suất $p_i(t)$. |

## Formulation

### Mô hình tổng hợp

Theo nghiên cứu, công suất đo tại một điểm là tổng đóng góp của các thiết bị:

$$
P(t) = \sum_{i=1}^{N} p_i(t)
$$

Khi xét nhiễu và tải chưa được mô hình hóa:

$$
P(t) = \sum_{i=1}^{N} p_i(t) + \varepsilon(t)
$$

### Bài toán suy luận ngược

NILM chỉ quan sát $P(t)$ nhưng cần ước lượng các tín hiệu riêng:

$$
\widehat{p}_1(t),\widehat{p}_2(t),\ldots,\widehat{p}_N(t)
$$

Hay viết ngắn gọn:

$$
\text{Từ } P(t) \text{, ước lượng } \{p_i(t)\}_{i=1}^{N}
$$

Đây là bài toán ngược vì nhiều tổ hợp thiết bị có thể tạo ra cùng một công suất tổng. NILM cần dùng thêm dấu vết tải, sự kiện chuyển trạng thái, đặc tính thời gian và các giả định về thiết bị.

### Mô hình trạng thái bật/tắt

Với thiết bị Type-I, có thể xấp xỉ:

$$
p_i(t) \approx w_i s_i(t)
$$

Suy ra:

$$
P(t) \approx \sum_{i=1}^{N} w_i s_i(t) + \varepsilon(t)
$$

Thiết bị nhiều trạng thái hoặc có công suất biến thiên liên tục cần mô hình $p_i(t)$ phức tạp hơn.

### Dạng vector và năng lượng

Với $t=1,\ldots,T$:

$$
\mathbf{P} = \mathbf{X}\mathbf{1} + \boldsymbol{\varepsilon}
$$

Năng lượng của thiết bị $i$ trong khoảng quan sát là:

$$
E_i \approx \sum_{t=1}^{T} p_i(t)\,\Delta t
$$

### Chỉ phân tách một số thiết bị

Nếu chỉ theo dõi tập $S$:

$$
P(t) = \sum_{i \in S} p_i(t) + r(t)
$$

Phần $r(t)$ gộp các thiết bị ngoài mục tiêu, tải chưa biết và sai số. Vì vậy, mô hình có thể dự đoán ít thiết bị hơn số thiết bị thực sự đang hoạt động mà vẫn giữ phần công suất còn lại trong $r(t)$.

### Nguồn

Mô hình tổng và nhiệm vụ phân rã dựa trên [[Papers/contents/zoha-2012-nilm-survey-general-framework-of-nilm|Zoha et al. (2012), General Framework of NILM]]. Các thành phần $\varepsilon(t)$, biến trạng thái, dạng vector và số dư $r(t)$ là phần đại số hóa mở rộng từ mô hình đó.
