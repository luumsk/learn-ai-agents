# MCP (Model Context Protocol)

MCP (Model Context Protocol) là một chuẩn giao tiếp để giúp model, ví dụ như LLM, nói chuyện với các hệ thống bên ngoài như app, dữ liệu hay service. Thay vì mỗi hệ thống có một cách gọi hàm khác nhau, MCP đưa ra một “ngôn ngữ chung” để model và các công cụ hiểu nhau. Nó quy định request và response sẽ ở dạng nào, thường là JSON có input, output và metadata rõ ràng. Nhờ vậy, model không chỉ sinh ra văn bản, mà còn có thể gọi hành động thật sự một cách an toàn, không bị nhầm lẫn về tham số.

Tool thì đơn giản hơn: nó chính là một hàm hay khả năng cụ thể mà model có thể dùng, ví dụ hàm mở file MRI hoặc hàm tìm email. Như vậy có thể hiểu MCP giống như chuẩn USB, còn Tool giống như chuột hoặc bàn phím. MCP không làm công việc, nó chỉ định nghĩa cách giao tiếp. Tool mới là nơi thực hiện công việc thật sự.

MCP quan trọng vì nó làm cho việc dùng tool trở nên thống nhất và an toàn. Tất cả tools đi qua MCP đều dùng chung một cách biểu diễn, nên model dễ dàng chuyển từ tool này sang tool khác. Nó cũng giúp một client có thể kết nối với nhiều server khác nhau mà không cần viết lại mọi thứ từ đầu.

Khi nào nên dùng MCP và khi nào chỉ cần Tool? Nếu bạn muốn xây dựng một hệ thống mở rộng, nhiều tool khác nhau cùng chạy, hoặc cần giao tiếp với hệ thống lớn, hãy dùng MCP. Nhưng nếu chỉ thử nghiệm nhanh, chỉ cần một vài hàm nhỏ cho đơn giản, thì dùng Tool trực tiếp sẽ nhẹ nhàng hơn.
