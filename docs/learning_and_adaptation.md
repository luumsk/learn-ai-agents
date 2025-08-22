# Learning and Adaptation

## 1. Khái niệm cốt lõi

**Learning** là quá trình một agent cải thiện hiệu suất của mình bằng cách cập nhật các tham số bên trong, thường là trọng số của mạng học máy, thông qua việc quan sát dữ liệu và phản hồi từ môi trường. Agent càng học nhiều thì càng có khả năng chọn hành động tốt hơn. Điều này giống như con người luyện tập nhiều lần một kỹ năng và dần dần thực hiện hiệu quả hơn. Ngược lại, **Adaptation** là khả năng điều chỉnh hành vi của agent khi môi trường thay đổi mà không cần học lại từ đầu. Nó tận dụng kiến thức đã có và xoay chuyển hành vi để phù hợp với bối cảnh mới, ví dụ như một robot vốn quen đi trên nền phẳng có thể thích nghi khi gặp cát hoặc sỏi.

## 2. Cơ chế

Learning thường diễn ra bằng cách agent chọn hành động, nhận feedback (reward, loss, hoặc preference), sau đó cập nhật policy hoặc value function để tăng xác suất chọn hành động tốt. Ngoài ra, agent có thể học bắt chước (imitation learning), học từ so sánh (preference learning), hoặc xây dựng world model để mô phỏng môi trường và lên kế hoạch trong đó.

Với Adaptation, có nhiều hình thức khác nhau: in-context adaptation: tham số mô hình được giữ nguyên nhưng hành vi thay đổi dựa trên ngữ cảnh; test-time adaptation: agent điều chỉnh nhẹ một số thành phần khi gặp dữ liệu mới; meta-learning: học cách học để chỉ cần vài ví dụ cũng thích nghi được; continual learning: duy trì kiến thức khi phải học nhiều nhiệm vụ nối tiếp nhau; external memory: lưu tri thức ngoài tham số để agent dễ dàng thay đổi khi cần. Ví dụ, một mô hình dịch máy có thể điều chỉnh nhanh cách dùng từ khi chuyển sang văn bản chuyên ngành, dù chưa được huấn luyện trực tiếp trên dữ liệu đó.

## 3. Những cặp dễ nhầm lẫn

- Adaptation dễ bị nhầm với overfitting, nhưng thực ra hai khái niệm trái ngược: thích nghi là sự linh hoạt có kiểm soát, còn overfitting là bị bó hẹp vào dữ liệu cũ. Một agent biết thích nghi có thể hoạt động tốt trong tình huống mới, trong khi mô hình bị overfit sẽ thất bại vì chỉ nhớ dữ liệu cũ.

- Generalization cũng khác với adaptation: generalization nghĩa là mô hình đã được huấn luyện để làm tốt trên dữ liệu mới ngay lập tức, còn adaptation là điều chỉnh thêm khi gặp sự khác biệt.

- Tương tự, fine-tuning thay đổi trực tiếp tham số, trong khi in-context chỉ dùng ngữ cảnh để đổi hành vi.

- Và cuối cùng, cần phân biệt exploration (khám phá để học thêm) với exploitation (tận dụng cái đã biết để tối đa hóa phần thưởng hiện tại).

## 4. Khi nào nên dùng, khi nào nên tránh?

Nên dùng
- Môi trường biến thiên (tool thay đổi API, dữ liệu đa miền, robot gặp địa hình mới).
- Bài toán nhiều task/ít dữ liệu cho mỗi task (meta‑learning, few‑shot).
- Khi có feedback gián tiếp (so sánh A/B, preference) thay vì reward rõ ràng.

Tránh hoặc giảm mức độ
- Môi trường tĩnh, đơn giản, có quy tắc rõ ràng → viết luật hoặc supervised là đủ.
- Hệ thống an toàn nghiêm ngặt, độ trễ thấp (y tế, hàng không) nếu không có cơ chế bảo đảm, sandbox và rollback.
- Khi thiếu tín hiệu feedback (reward mơ hồ, nhiễu, không ổn định) → ưu tiên modeling/supervised trước. Điều này có nghĩa là thay vì để agent tự học từ reward kém chất lượng, ta nên dùng mô hình dự đoán hoặc dữ liệu gán nhãn để tạo nền tảng ổn định hơn.

## 5. Tóm tắt

**Learning loop**

Learning có thể hình dung như một vòng lặp liên tục:  
1. Agent quan sát môi trường.  
2. Agent chọn hành động dựa trên policy.  
3. Agent nhận feedback từ môi trường (reward, loss, hoặc preference).  
4. Agent cập nhật policy, value function hoặc world model.  
5. Quay lại bước 1 và tiếp tục lặp lại.  

```
Quan sát → Hành động (policy) → Feedback → Cập nhật (policy/value/world model) → Lặp
```

**Adaptation loop**

Adaptation diễn ra khi môi trường hoặc dữ liệu thay đổi:  
1. Agent phát hiện sự thay đổi (distribution shift, domain mới).  
2. Agent xác định ngữ cảnh hoặc truy xuất bộ nhớ phù hợp.  
3. Agent điều chỉnh nhanh hành vi bằng các kỹ thuật như in-context hoặc test-time adaptation.  
4. Agent đảm bảo an toàn bằng regularization, rollback hoặc cơ chế bảo vệ khác.  
5. Agent đánh giá lại và quyết định giữ nguyên hay tiếp tục cập nhật.  

```
Phát hiện thay đổi → Tìm ngữ cảnh/bộ nhớ phù hợp → Điều chỉnh nhanh → Đảm bảo an toàn → Đánh giá → Học/giữ nguyên
```

Hai vòng lặp này bổ sung cho nhau: Learning xây dựng kiến thức nền tảng lâu dài, trong khi Adaptation đảm bảo agent phản ứng kịp thời và hiệu quả khi môi trường biến đổi.