# Learning and Adaptation

## 1. Khái niệm cốt lõi

Learning (học lâu dài) là quá trình một agent cải thiện hiệu suất của mình bằng cách cập nhật các tham số bên trong, thường là trọng số của mạng học máy, thông qua việc quan sát dữ liệu và phản hồi từ môi trường. Agent càng học nhiều thì càng có khả năng chọn hành động tốt hơn. Ngược lại, Adaptation (thích nghi nhanh) là khả năng điều chỉnh hành vi của agent khi môi trường thay đổi mà không cần học lại từ đầu. Nó tận dụng kiến thức đã có và xoay chuyển hành vi để phù hợp với bối cảnh mới, ví dụ như một robot vốn quen đi trên nền phẳng có thể thích nghi khi gặp cát hoặc sỏi.

## 2. Cơ chế

Learning thường diễn ra bằng cách agent chọn hành động, nhận feedback (reward, loss, hoặc preference), sau đó cập nhật policy hoặc value function để tăng xác suất chọn hành động tốt. Ngoài ra, agent có thể học bắt chước (imitation learning), học từ so sánh (preference learning), hoặc xây dựng world model để mô phỏng môi trường và lên kế hoạch trong đó. Với Adaptation, có nhiều hình thức khác nhau: in-context adaptation, nơi tham số mô hình giữ nguyên nhưng hành vi thay đổi dựa vào ngữ cảnh; test-time adaptation, nơi agent điều chỉnh nhẹ một số thành phần khi gặp dữ liệu mới; meta-learning, học cách học để thích nghi chỉ với vài ví dụ; continual learning, duy trì kiến thức khi học chuỗi nhiệm vụ; và external memory, tức là lưu tri thức ngoài tham số để dễ dàng thay đổi theo môi trường.

## 3. Những cặp dễ nhầm lẫn

Adaptation dễ bị nhầm với overfitting, nhưng thực ra hai khái niệm trái ngược: thích nghi là sự linh hoạt có kiểm soát, còn overfitting là bị bó hẹp vào dữ liệu cũ. Generalization cũng khác với adaptation: generalization nghĩa là mô hình đã được huấn luyện để làm tốt trên dữ liệu mới ngay lập tức, còn adaptation là điều chỉnh thêm khi gặp sự khác biệt. Tương tự, fine-tuning thay đổi trực tiếp tham số, trong khi in-context chỉ dùng ngữ cảnh để đổi hành vi. Và cuối cùng, cần phân biệt exploration (khám phá để học thêm) với exploitation (tận dụng cái đã biết để tối đa hóa phần thưởng hiện tại).

## 4. Khi nào nên dùng, khi nào nên tránh?

Learning và adaptation đặc biệt hữu ích khi môi trường biến đổi liên tục, chẳng hạn công cụ đổi API, robot gặp địa hình khác, hay dữ liệu đến từ nhiều miền. Chúng cũng cần thiết trong bài toán nhiều nhiệm vụ với ít dữ liệu cho mỗi nhiệm vụ, hoặc khi phản hồi không trực tiếp mà đến từ so sánh. Tuy nhiên, chúng không hiệu quả nếu môi trường tĩnh và đơn giản, nơi việc viết luật thủ công là đủ. Ngoài ra, trong các hệ thống yêu cầu an toàn tuyệt đối như y tế hoặc hàng không, việc cho phép agent học hay thích nghi trực tiếp có thể nguy hiểm nếu không có sandbox hoặc cơ chế rollback. Nếu tín hiệu phản hồi quá mơ hồ hoặc nhiễu, tốt hơn nên dùng cách tiếp cận mô hình hóa hoặc giám sát.

## 5. Tóm tắt

- Có thể hình dung Learning như một vòng lặp: agent quan sát môi trường, chọn hành động dựa trên policy, nhận feedback, rồi cập nhật policy/value/world model trước khi lặp lại. - Adaptation cũng có vòng lặp riêng: khi phát hiện môi trường thay đổi hoặc phân phối dữ liệu bị lệch, agent sẽ tìm ngữ cảnh phù hợp, điều chỉnh hành vi nhanh bằng in-context hoặc test-time adaptation, đảm bảo an toàn qua regularization hay rollback, rồi tiếp tục đánh giá và quyết định giữ hay cập nhật thêm. Hai vòng lặp này bổ sung cho nhau: learning xây nền tảng lâu dài, adaptation giúp agent sống sót và hiệu quả trong tình huống mới.