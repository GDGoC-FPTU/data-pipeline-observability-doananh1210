[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23573971&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** thuanhdoan1210@gmail.com
**Name:** Đoàn Thư Ánh

---

## Mo ta

Bài lab này xây dựng một ETL Pipeline đơn giản để xử lý dữ liệu sản phẩm và kiểm tra ảnh hưởng của chất lượng dữ liệu đến kết quả của Agent.

Pipeline thực hiện các bước:

- **Extract**: Đọc dữ liệu đầu vào.
- **Transform**: Làm sạch dữ liệu.
- **Load**: Lưu dữ liệu đã xử lý vào `processed_data.csv`

Sau đó, tiến hành Agent Simulation (Stress Test) với 2 loại dữ liệu:

- **Dữ liệu sạch (clean data)**
- **Dữ liệu nhiễu (garbage data)**

Mục tiêu là quan sát sự khác biệt trong kết quả của Agent khi dữ liệu đầu vào thay đổi.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Bước 1: Tạo dữ liệu nhiễu
python generate_garbage.py

# Bước 2: Chạy agent với cả clean và garbage data
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

### ETL Pipeline:
- Tổng số records xử lý: 5
- Records hợp lệ (kept): 3
- Records bị loại (dropped): 2
- **Lý do loại:**
  - ID 3: Price <= 0
  - ID 4: Missing Category
- **Output**: `processed_data.csv` chứa 3 records sạch

### Agent Simulation:
- Với clean data → Agent chọn Laptop ($1200) → hợp lý
- Với garbage data → Agent chọn Nuclear Reactor ($999999) → phi thực tế

**Kết quả cho thấy chất lượng dữ liệu ảnh hưởng trực tiếp đến quyết định của Agent.**
