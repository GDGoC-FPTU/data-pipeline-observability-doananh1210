# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600364
**Name:** Đoàn Thư Ánh
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 9 | Kết quả hợp lý, phù hợp với dữ liệu thực tế |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Kết quả phi thực tế, bị ảnh hưởng bởi dữ liệu nhiễu |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent trả lời sai khi dùng Garbage Data chủ yếu do chất lượng dữ liệu đầu vào kém. Một số vấn đề phổ biến gồm:

- **Duplicate IDs**: Khi dữ liệu có ID trùng lặp, agent có thể hiểu sai hoặc ghi đè thông tin, dẫn đến lựa chọn không chính xác.
- **Wrong data types**: Ví dụ giá trị giá tiền bị lưu dưới dạng string hoặc sai định dạng sẽ khiến việc so sánh và tính toán bị lỗi.
- **Outliers (giá trị ngoại lai)**: Trường hợp “Nuclear Reactor giá $999999” là một outlier rất lớn so với các sản phẩm khác, khiến agent bị “lệch” trong việc chọn phương án tối ưu.
- **Null values**: Thiếu dữ liệu quan trọng làm giảm khả năng phân tích chính xác.

Những vấn đề này làm cho agent tin rằng lựa chọn tốt nhất là một sản phẩm vô lý, vì nó chỉ dựa vào dữ liệu đầu vào mà không có khả năng tự kiểm chứng tính hợp lý của dữ liệu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** → Đồng ý.

Dữ liệu chất lượng cao quan trọng hơn prompt vì agent luôn dựa vào dữ liệu để đưa ra quyết định. Dù prompt có tốt đến đâu, nếu dữ liệu sai hoặc nhiễu thì kết quả vẫn sẽ sai. Prompt chỉ giúp định hướng, còn dữ liệu mới là nền tảng quyết định độ chính xác của hệ thống.
