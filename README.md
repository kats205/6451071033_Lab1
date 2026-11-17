# 6451071033_Lab1 — Khai phá dữ liệu (Data Mining) — LAB 1

Tổng hợp các bài thực hành **LAB 1** môn **Khai phá dữ liệu (Data Mining)**, bao gồm phần **Khảo sát & Tiền xử lý dữ liệu** (Bài 1–3) và phần **Khai phá tập phổ biến & Luật kết hợp** với thuật toán **Apriori** và **FP-Growth** (Bài 4–6).

## Thông tin sinh viên

- **Họ và tên:** Nguyễn Phạm Bảo Khanh
- **MSSV:** `6451071033`
- **Môn học:** Khai phá dữ liệu (Data Mining)
- **Repository:** [https://github.com/kats205/6451071033_Lab1](https://github.com/kats205/6451071033_Lab1)

---

## Danh sách bài thực hành

### Phần 1: Khảo sát & Tiền xử lý dữ liệu

| Bài | Notebook | Tài liệu tham chiếu | Tập dữ liệu | Nội dung & Kết quả chính |
|---|---|---|---|---|
| **Bài 1** | [`6451071033_LAB1_Bai1.ipynb`](./6451071033_LAB1_Bai1.ipynb) | Phần 1 — Trang 15–17 | `titanic.csv` (`1.309 × 14`) | Thống kê mô tả, trực quan hóa mối liên hệ với `survived` (`sex`, `age`, `embarked`, `pclass`, `relatives`, `not_alone`); trích xuất `deck` và `title`; xử lý giá trị thiếu (`age`, `embarked`, `fare`), xóa cột nhiễu; rời rạc hóa `fare`/`age` và tạo thuộc tính mới (`age_class`, `fare_per_person`). Dữ liệu sạch cuối cùng: `1.309 × 14` (kiểu `int64`, `0` giá trị null). |
| **Bài 2** | [`6451071033_LAB1_Bai2.ipynb`](./6451071033_LAB1_Bai2.ipynb) | Phần 1 — Trang 28–29 | Bảng mẫu 16 dòng (`16 × 8`) & `bank/bank.csv` (`4.521 × 17`) | Thực hiện đầy đủ 6 bước tiền xử lý trên cả bảng mẫu 16 dòng (Phần A) và tập `bank.csv` (Phần B): phân loại thuộc tính; xử lý `NaN`, `'unknown'` và cờ `previously_contacted` (`pdays == -1`); khử nhiễu bằng Binning & Smoothing (Equal-width & Equal-frequency); rời rạc hóa theo khoảng & nhãn (`Youth`/`Adult`/`Middle-aged`/`Senior`, `Short`/`Medium`/`Long`); One-Hot Encoding (`pd.get_dummies`); chuẩn hóa Min-Max về `[0, 1]` và đối chiếu `MinMaxScaler`. |
| **Bài 3** | [`6451071033_LAB1_Bai3.ipynb`](./6451071033_LAB1_Bai3.ipynb) | Phần 1 — Trang 30 | `tb_tracking.xlsx` (`33.340` dòng thô) | Gán tiêu đề 6 cột (`id`, `device_id`, `co_level`, `humidity`, `temperature`, `time`), loại bỏ 1 dòng trống và 3 dòng công thức tổng hợp cuối tệp (`MIN`, `MAX`, `AVERAGE`) còn `33.336` bản ghi; lọc dữ liệu từ mốc `03/01/2018` (`DD/MM/YYYY`) còn `1.917` dòng; quy đổi cột `minutes` trong ngày (`1.50`–`1439.00` phút); vẽ scatter plot theo `device_id` (`99005`, `0`, `1`) và phân tích các điểm bất thường. |

### Phần 2: Khai phá tập phổ biến & Luật kết hợp (Apriori & FP-Growth)

| Bài | Notebook | Tài liệu tham chiếu | Tập dữ liệu | Nội dung & Kết quả chính |
|---|---|---|---|---|
| **Bài 4** | [`6451071033_LAB1_Bai4.ipynb`](./6451071033_LAB1_Bai4.ipynb) | Phần 2 — Trang 37–38 | `Online Retail.xlsx` (lọc `United Kingdom`) | Làm sạch `Description`, loại bỏ `9.288` hóa đơn tín dụng (`'C'`), lọc `United Kingdom` (`487.622` dòng), dựng ma trận giỏ hàng `18.667 × 4.174` (sau khi xóa `'POSTAGE'`). Với `min_support = 0.03` và `min_confidence = 0.5`, **Apriori** (`0.3683s`) và **FP-Growth** (`1.2026s`) đều tìm được **131 tập phổ biến** và **10 luật kết hợp** trùng khớp 100%, kèm scatter plot `support` vs `confidence`. |
| **Bài 5** | [`6451071033_LAB1_Bai5.ipynb`](./6451071033_LAB1_Bai5.ipynb) | Phần 2 — Bài 5a, Trang 45 | `Online Retail.xlsx` (lọc `Germany`) | Thực hiện quy trình 12 bước trên dữ liệu nước Đức (`9.042` dòng → ma trận `457` hóa đơn × `1.694` sản phẩm sau khi xóa `'POSTAGE'`). Với `min_sup = 0.05` và `min_conf = 0.50`, **Apriori** (`0.008393s`) và **FP-Growth** (`0.016185s`) đều tìm ra **59 tập phổ biến** (50 tập bậc 1, 9 tập bậc 2) và **8 luật kết hợp** khớp hoàn toàn, kèm biểu đồ phân tán và benchmark thời gian thực thi. |
| **Bài 6** | [`6451071033_LAB1_Bai6.ipynb`](./6451071033_LAB1_Bai6.ipynb) | Phần 2 — Bài 6, Trang 45 | `groceries.csv` (`9.835 × 169`) | Mã hóa One-Hot bằng `TransactionEncoder` và so sánh hiệu năng **Apriori** vs **FP-Growth** trên 6 ngưỡng `min_support` (`0.01` → `0.10`, cho `333`, `122`, `63`, `31`, `19`, `8` tập phổ biến), kèm kiểm chứng mở rộng tại `0.005` (`1.001` tập) và `0.003` (`2.226` tập). Phân tích vùng giao cắt hiệu năng (`min_support >= 0.02`: Apriori nhanh hơn; `min_support = 0.01`: giao cắt, FP-Growth `71.45 ms` vs Apriori `85.62 ms`; `min_support = 0.003`: FP-Growth nhanh gấp `3.06×`). |

---

## Cấu trúc thư mục

```text
6451071033_Lab1/
├── .gitignore
├── Link truy cập dataset.txt
├── README.md
├── 6451071033_LAB1_Bai1.ipynb
├── 6451071033_LAB1_Bai2.ipynb
├── 6451071033_LAB1_Bai3.ipynb
├── 6451071033_LAB1_Bai4.ipynb
├── 6451071033_LAB1_Bai5.ipynb
├── 6451071033_LAB1_Bai6.ipynb
└── Dataset/                      # Bỏ qua khi push Git (xem .gitignore), tự tải hoặc tải thủ công từ Drive
    ├── titanic.csv
    ├── tb_tracking.xlsx
    ├── Online Retail.xlsx
    ├── groceries.csv
    └── bank/
        ├── bank.csv
        ├── bank-full.csv
        └── bank-names.txt
```

> **Lưu ý về `.gitignore`:** Thư mục `Dataset/`, các tệp nén `Dataset-*.zip`, tài liệu PDF khóa học (`Tàu liệu LAB1.pdf`) và các thư mục tạm (`.ipynb_checkpoints/`, `__pycache__/`, `*.tmp`) được loại trừ khỏi Git để giữ repository gọn nhẹ.

---

## Nguồn dữ liệu (Dataset)

Toàn bộ bộ dữ liệu thực hành của LAB 1 được lưu tại Google Drive (xem thêm trong [`Link truy cập dataset.txt`](./Link%20truy%20c%E1%BA%ADp%20dataset.txt)):

- **Google Drive:** [Thư mục Dataset LAB 1](https://drive.google.com/drive/folders/1rv5SiO5zFlU-cyEXul09OpCvTXrdjG1m?usp=sharing)

Mỗi notebook đều tích hợp sẵn hàm `get_dataset_path(...)` hỗ trợ chạy linh hoạt theo thứ tự ưu tiên:
1. Đọc trực tiếp từ thư mục cục bộ `./Dataset/` nếu đã có sẵn.
2. Nếu chạy trên **Google Colab**, tự động mount Google Drive và tìm trong `/content/drive/MyDrive/Dataset/`.
3. Nếu chưa có ở cả hai nơi trên, tự động tải thư mục `Dataset` từ Google Drive bằng `gdown`.

---

## Yêu cầu môi trường & Hướng dẫn chạy

### Thư viện sử dụng

Các notebook đã được chạy và kiểm chứng trên môi trường **Python 3.15.0** với các thư viện chính:

- `pandas` (`3.1.1`) & `numpy` (`2.5.5`)
- `matplotlib` & `seaborn` (`0.13.2`)
- `scikit-learn` (`MinMaxScaler` ở Bài 2)
- `openpyxl` (`3.1.5`, đọc tệp `.xlsx` ở Bài 3, 4, 5)
- `mlxtend` (`0.25.0`, `apriori`, `fpgrowth`, `association_rules`, `TransactionEncoder` ở Bài 4, 5, 6)
- `gdown` (hỗ trợ tải dataset tự động từ Google Drive)

*(Mã nguồn đã được viết tương thích với `pandas 3.x`, sử dụng `DataFrame.map()` thay cho `applymap()` và `engine="openpyxl"` khi đọc tệp Excel.)*

### Các bước chạy cục bộ

1. **Clone repository:**
   ```bash
   git clone https://github.com/kats205/6451071033_Lab1.git
   cd 6451071033_Lab1
   ```

2. **Cài đặt thư viện cần thiết:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl mlxtend gdown jupyter
   ```
   *(Các notebook Bài 3–6 cũng tự động kiểm tra và cài `mlxtend`, `openpyxl`, `gdown` nếu thiếu khi thực thi cell đầu tiên.)*

3. **Chuẩn bị dữ liệu (tùy chọn):**
   - Tải thư mục `Dataset` từ link Google Drive ở trên và đặt vào thư mục gốc của dự án (`./Dataset/`), **hoặc** chạy trực tiếp các notebook để `gdown` tự động tải về.

4. **Mở và chạy notebook:**
   - Mở bằng VS Code / JupyterLab / Jupyter Notebook, hoặc tải các tệp `.ipynb` lên **Google Colab** để chạy trực tiếp.
