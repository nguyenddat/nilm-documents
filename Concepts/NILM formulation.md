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
  - "[[Papers/contents/zoha-2012-nilm-survey-learning-and-inference-in-nilm-systems|Zoha et al. (2012) – Learning and Inference in NILM Systems]]"
related:
  - "[[NILM là gì]]"
  - "[[Load Disaggregation]]"
---
# NILM formulation

## Notation

| Ký hiệu | Tên gọi | Ý nghĩa |
| --- | --- | --- |
| $t$ | Thời điểm lấy mẫu | $t=1,\ldots,T$ là khoảng quan sát. |
| $i$ | Chỉ số thiết bị | $i=1,\ldots,N$. |
| $N$ | Số thiết bị mô hình hóa | Số thiết bị có trong thư viện dấu vết tải. |
| $P(t)$ | Công suất tổng | Công suất quan sát tại công tơ chung ở thời điểm $t$. |
| $y_{i,t}$ | Phần tử tín hiệu thiết bị | Công suất chưa biết của thiết bị $i$ tại thời điểm $t$. |
| $\mathbf{y}_i$ | Vector tín hiệu thiết bị | Vector công suất của thiết bị $i$ trong toàn bộ khoảng quan sát. |
| $\mathbf{Y}$ | Ma trận biến quyết định | Ma trận tạo bởi các vector $\mathbf{y}_i$, trong đó phần tử hàng $i$, cột $t$ là $y_{i,t}$. |
| $\mathcal{Y}_i$ | Tập vector khả dĩ | Các vector tín hiệu hoặc dấu vết công suất hợp lệ của thiết bị $i$. |
| $\varepsilon(t)$ | Nhiễu và tải chưa giải thích | Phần sai khác giữa tín hiệu tổng và tổng các thiết bị được mô hình hóa. |

## Formulation
### Dữ liệu và biến quyết định
Cho chuỗi công suất tổng đã đo $P(1),\ldots,P(T)$ và thư viện dấu vết tải của $N$ thiết bị. Với mỗi thiết bị $i$, ta có vector tín hiệu:

$$
\mathbf{y}_i = [y_{i,1},y_{i,2},\ldots,y_{i,T}]^\mathsf{T}
\in \mathbb{R}_+^T
$$

Biến cần tìm là ma trận tạo bởi các vector này:

$$
\mathbf{Y} =
\begin{bmatrix}
\mathbf{y}_1^\mathsf{T} \\
\mathbf{y}_2^\mathsf{T} \\
\vdots \\
\mathbf{y}_N^\mathsf{T}
\end{bmatrix}
= [y_{i,t}]_{N\times T}
=
\begin{bmatrix}
y_{1,1} & \cdots & y_{1,T} \\
\vdots & \ddots & \vdots \\
y_{N,1} & \cdots & y_{N,T}
\end{bmatrix}
\in \mathbb{R}_+^{N\times T}.
$$

Trong đó:

- $i$ là chỉ số của thiết bị, với $i=1,\ldots,N$.
- $t$ là chỉ số thời gian, với $t=1,\ldots,T$.
- $\mathbf{y}_i$ là vector công suất của thiết bị $i$ trong toàn bộ khoảng quan sát.
- $\mathbf{Y}_{i,:}=\mathbf{y}_i^\mathsf{T}$ là hàng thứ $i$ của ma trận $\mathbf{Y}$.
- Cột thứ $t$ của $\mathbf{Y}$ chứa đóng góp của tất cả thiết bị tại thời điểm $t$.
- $y_{i,t}$ là công suất mà thiết bị $i$ đóng góp tại thời điểm $t$.

Từ các công suất thiết bị $y_{1,t},y_{2,t},\ldots,y_{N,t}$, công suất tổng tại thời điểm $t$ được viết gộp là:

$$
P(t) = \sum_{i=1}^{N} y_{i,t} + \varepsilon(t)
     = \mathbf{1}_N^\mathsf{T}\mathbf{Y}_{:,t} + \varepsilon(t)
$$

Trong đó:

- $P(t)$ là tổng tải đo được tại thời điểm $t$.
- $\mathbf{Y}_{:,t}=[y_{1,t},y_{2,t},\ldots,y_{N,t}]^\mathsf{T}$ là cột thứ $t$ của ma trận biến quyết định $\mathbf{Y}$.
- $\mathbf{1}_N$ là vector cột gồm $N$ phần tử bằng $1$.
- $\varepsilon(t)$ là nhiễu, sai số mô hình và tải chưa được giải thích.
- Nếu bỏ qua nhiễu và tải chưa biết, đặt $\varepsilon(t)=0$; khi đó $P(t)=\sum_{i=1}^{N}y_{i,t}$.

### Bài toán tối ưu

Cho ma trận đầu vào $\mathbf{X}$ chứa dữ liệu đo tổng hoặc các đặc trưng được trích xuất từ dữ liệu đó. Hàm NILM ánh xạ dữ liệu đầu vào thành ma trận công suất thiết bị dự đoán:

$$
\mathbf{X}=[\mathbf{x}_1,\mathbf{x}_2,\ldots,\mathbf{x}_T]
\in\mathbb{R}^{d_x\times T},
\qquad
\mathbf{x}_t=\begin{bmatrix}P(t)\end{bmatrix}
\text{ nếu chỉ đo công suất tổng}
$$

$$
\mathbf{X}\xrightarrow{\ f\ }\widehat{\mathbf{Y}}=f(\mathbf{X})
$$

Với dữ liệu huấn luyện gồm các cặp $(\mathbf{X}^{(m)},\mathbf{Y}^{(m)})$, ta tìm hàm $f\in\mathcal{F}$ sao cho $\widehat{\mathbf{Y}}$ gần $\mathbf{Y}$ nhất:

$$
\widehat{f}\in\underset{f\in\mathcal{F}}{\arg\min}\;
\frac{1}{M}\sum_{m=1}^{M}
\left\|f(\mathbf{X}^{(m)})-\mathbf{Y}^{(m)}\right\|_F^2
$$

Để đầu ra vẫn phù hợp với phép đo tổng, ta thêm điều kiện tái tạo:
$$
\left\|\mathbf{p}^{(m)}-\mathbf{1}_N^\mathsf{T}f(\mathbf{X}^{(m)})\right\|_2\le\delta
$$

Vì vậy, các điều kiện cơ bản của bài toán là:
1. **Công suất không âm:** $\widehat{y}_{i,t}\ge0$ theo từng phần tử. Dùng $\ge0$ vì thiết bị có thể ở trạng thái tắt và có công suất bằng $0$.
2. **Đầu ra gần đầu ra thật:** tối thiểu hóa $\|\widehat{\mathbf{Y}}-\mathbf{Y}\|_F^2$. Chuẩn Frobenius đo tổng bình phương sai khác của mọi thiết bị và mọi thời điểm.
3. **Khớp công suất tổng:** $\mathbf{1}_N^\mathsf{T}\widehat{\mathbf{Y}}$ phải gần $\mathbf{p}$; $\delta=0$ khi giả định không có nhiễu.
4. **Tín hiệu hợp lệ:** hàng thứ $i$ của $\widehat{\mathbf{Y}}$ thuộc tập dấu vết khả dĩ $\mathcal{Y}_i$.
5. **Hàm thuộc lớp cho phép:** $f\in\mathcal{F}$, chẳng hạn lớp các mô hình học máy hoặc bộ phân loại được chọn.
### Nguồn
Mô hình tổng $P(t)=p_1(t)+\cdots+p_n(t)$ và mô tả phương pháp tối ưu khớp tín hiệu tổng với tổ hợp tín hiệu thiết bị dựa trên [[Papers/contents/zoha-2012-nilm-survey-general-framework-of-nilm|Zoha et al. (2012), General Framework of NILM]] và [[Papers/contents/zoha-2012-nilm-survey-learning-and-inference-in-nilm-systems|Learning and Inference in NILM Systems]].
