# 23701511_NguyenMinhTan_Cabsystem
## 1. Quy trình nghiệp vụ
### Hệ thống CAB được xây dựng nhằm số hóa và nâng cao hiệu quả toàn bộ quy trình đặt xe, từ khi khách hàng tạo yêu cầu đến khi chuyến đi hoàn thành, thanh toán và đánh giá tài xế. Qua phân tích nghiệp vụ, hệ thống xác định ba nhóm người dùng chính gồm khách hàng, tài xế và nhân viên vận hành, cùng các bên liên quan như ban giám đốc, bộ phận tài chính, chăm sóc khách hàng và các nhà cung cấp dịch vụ bên ngoài. 
### Quy trình nghiệp vụ cốt lõi bao gồm đăng ký và xác thực tài khoản, tạo yêu cầu đặt xe, xác định tài xế phù hợp dựa trên vị trí và trạng thái hoạt động, gửi và xử lý yêu cầu nhận chuyến, theo dõi trạng thái và vị trí chuyến đi, tính cước, thanh toán, thông báo và đánh giá sau chuyến. Hệ thống cần xử lý các trường hợp ngoại lệ như tài xế từ chối hoặc không phản hồi, không tìm được tài xế, thanh toán thất bại hoặc chuyến đi phát sinh sự cố. Bên cạnh các yêu cầu chức năng, hệ thống phải đáp ứng các yêu cầu phi chức năng về khả năng mở rộng, tính sẵn sàng, bảo mật, phân quyền, bảo vệ dữ liệu và ghi nhận nhật ký hoạt động, đồng thời cho phép tích hợp linh hoạt với các dịch vụ thanh toán, bản đồ/GPS và thông báo bên ngoài. 
### Trong quá trình phân tích, BA cũng cần làm rõ các quy tắc nghiệp vụ chưa được xác định như cách tính cước, tiêu chí ưu tiên tài xế, thời gian phản hồi, chính sách hủy chuyến, xử lý mất kết nối và thời gian lưu trữ dữ liệu để đảm bảo giải pháp đáp ứng đúng nhu cầu kinh doanh và có khả năng mở rộng trong tương lai.
## Stakeholder

| # | Stakeholder | Vai trò chính |
|---|---|---|
| 1 | **Ban giám đốc** | Định hướng kinh doanh, phê duyệt phạm vi, ngân sách và mục tiêu hệ thống |
| 2 | **Khách hàng** | Đăng ký, đặt xe, theo dõi chuyến, thanh toán và đánh giá tài xế |
| 3 | **Tài xế** | Nhận/từ chối chuyến, cập nhật trạng thái, vị trí và hoàn thành chuyến |
| 4 | **Nhân viên vận hành** | Theo dõi chuyến, điều phối tài xế và xử lý các trường hợp bất thường |
| 5 | **Nhân viên CSKH** | Hỗ trợ khách hàng, xử lý khiếu nại và tra cứu thông tin chuyến |
| 6 | **Bộ phận tài chính/kế toán** | Quản lý doanh thu, giao dịch, đối soát và báo cáo tài chính |
| 7 | **Quản trị viên hệ thống / IT** | Quản lý tài khoản, phân quyền, bảo mật và vận hành hệ thống |
| 8 | **Nhà cung cấp thanh toán** | Xử lý thanh toán điện tử và trả kết quả giao dịch cho CAB |
## Ma trận Stakeholder CAB

```mermaid
quadrantChart
    title Stakeholder Matrix - CAB
    x-axis "Interest thấp" --> "Interest cao"
    y-axis "Power thấp" --> "Power cao"

    quadrant-1 "Manage Closely"
    quadrant-2 "Keep Satisfied"
    quadrant-3 "Monitor"
    quadrant-4 "Keep Informed"

    "Ban giám đốc": [0.90, 0.95]
    "Nhân viên vận hành": [0.85, 0.85]
    "Quản trị viên / IT": [0.80, 0.90]
    "Khách hàng": [0.90, 0.35]
    "Tài xế": [0.85, 0.30]
    "Nhân viên CSKH": [0.75, 0.40]
    "Tài chính / Kế toán": [0.45, 0.75]
    "Nhà cung cấp thanh toán": [0.40, 0.70]
```
## 4.Business Goals

Hệ thống CAB được xây dựng nhằm số hóa quy trình đặt xe, nâng cao hiệu quả vận hành và cải thiện trải nghiệm khách hàng. Các mục tiêu kinh doanh chính bao gồm:

| ID | Business Goal | Mô tả |
|---|---|---|
| **BG01** | **Số hóa quy trình đặt xe** | Tự động hóa quy trình từ khi khách hàng tạo yêu cầu, tìm tài xế, thực hiện chuyến đến thanh toán và đánh giá. |
| **BG02** | **Tối ưu phân công tài xế** | Tự động tìm và ưu tiên tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành. |
| **BG03** | **Nâng cao trải nghiệm khách hàng** | Cho phép khách hàng đặt xe, theo dõi trạng thái chuyến, thông tin tài xế, cước phí, thanh toán và đánh giá. |
| **BG04** | **Nâng cao hiệu quả vận hành** | Hỗ trợ nhân viên vận hành theo dõi chuyến, quản lý tài xế và xử lý các trường hợp bất thường. |
| **BG05** | **Quản lý tập trung dữ liệu và giao dịch** | Quản lý tập trung thông tin khách hàng, tài xế, phương tiện, chuyến đi, cước phí và giao dịch. |
| **BG06** | **Đảm bảo khả năng mở rộng** | Xây dựng nền tảng có thể phục vụ số lượng lớn người dùng và dễ dàng mở rộng dịch vụ, thanh toán và thông báo trong tương lai. |
| **BG07** | **Đảm bảo an toàn và ổn định** | Bảo vệ dữ liệu người dùng, kiểm soát quyền truy cập và hạn chế ảnh hưởng khi một thành phần của hệ thống gặp sự cố. |
| **BG08** | **Hỗ trợ quản trị và ra quyết định** | Cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. |
