# Python & Pandas for Data Validation

Thay vì phụ thuộc vào đội ngũ Kỹ sư dữ liệu để trích xuất báo cáo, một Technical BA hiện đại có thể sử dụng Python & Pandas để tự kiểm chứng các giả định kinh doanh.

---

## 1. Môi Trường & Thư Viện Cốt Lõi

```python
import pandas as pd
import numpy as np

# Đọc dữ liệu từ file trích xuất hệ thống
df_payments = pd.read_csv('payment_logs.csv')
df_subscriptions = pd.read_csv('subscriptions.csv')
```

---

## 2. Phát Hiện Điểm Bất Thường Dữ Liệu (Anomaly Detection)

```python
# 1. Kiểm tra tỷ lệ giá trị thiếu (Missing Values)
print(df_payments.isnull().mean() * 100)

# 2. Phát hiện giao dịch bị nạp trùng (Duplicate charges trong vòng 60 giây)
df_payments['created_at'] = pd.to_datetime(df_payments['created_at'])
df_payments = df_payments.sort_values(by=['user_id', 'created_at'])

df_payments['time_diff'] = df_payments.groupby('user_id')['created_at'].diff().dt.total_seconds()
duplicate_charges = df_payments[(df_payments['time_diff'] < 60) & (df_payments['status'] == 'SUCCESS')]

print(f"Số lượng giao dịch nghi vấn nạp trùng: {len(duplicate_charges)}")
```

---

## 3. Khám Phá Baseline Nghiệp Vụ Thực Tế

Trước khi thiết kế tính năng mới, BA dùng Pandas để đo lường thực tế hiện trạng (AS-IS):
* Đo lường thời gian trung vị (Median Activation Time).
* Phân tích phân vị (Percentile 95th / 99th) của độ trễ hệ thống.
* Trích xuất danh sách khách hàng vượt quota để phục vụ bài toán thiết kế Soft Enforcement.
