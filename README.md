# Báo cáo Thực hành Kiểm thử hiệu năng với Apache JMeter

**Sinh viên thực hiện:** Võ Hoàng Dũng
**Mã sinh viên:** 23010828
**Môn học:** Đánh giá và kiểm định chất lượng phần mềm-1-3-25(LT5)

---

## 1. Mục tiêu kiểm thử
Thực hiện kiểm thử tải (Load Testing) cơ bản trên một API công khai để làm quen với công cụ Apache JMeter, cấu hình các thông số giả lập người dùng và đánh giá thời gian phản hồi, tỷ lệ lỗi của hệ thống.

**Mục tiêu (Target):** `https://jsonplaceholder.typicode.com/users` (API lấy danh sách người dùng)
**Phương thức:** GET

## 2. Kịch bản kiểm thử (Test Scenario)
Cấu hình giả lập người dùng truy cập đồng thời (Thread Group) với các thông số sau:
* **Number of Threads (users):** 10 người dùng ảo.
* **Ramp-up period:** 1 giây (Tạo toàn bộ 10 users trong vòng 1 giây).
* **Loop Count:** 1 vòng lặp.

![alt text](https://github.com/vo-hoangdung/Jmeter/blob/main/anh1.jpg)

## 3. Cấu hình HTTP Request
Thiết lập các thông số để gửi request tới máy chủ đích:
* **Protocol:** `https`
* **Server Name:** `jsonplaceholder.typicode.com`
* **Path:** `/users`

![alt text](https://github.com/vo-hoangdung/Jmeter/blob/main/anh2.jpg)
## 4. Kết quả thực hiện
Sau khi chạy kịch bản (Test Plan) và xóa bỏ các lỗi phát sinh do xác thực, thu được các kết quả thành công như sau:

### 4.1. Chi tiết các Request (View Results Tree)
Tất cả các request gửi đi đều nhận được phản hồi thành công từ server, biểu thị bằng biểu tượng khiên màu xanh lá cây với mã trạng thái `Response code: 200` và `Response message: OK`.

![alt text](https://github.com/vo-hoangdung/Jmeter/blob/main/anh3.jpg)

### 4.2. Báo cáo tổng hợp (Summary Report)
Dưới đây là các thông số hiệu năng thu thập được sau khi chạy 10 requests:

* **Samples:** 10 (Tổng số request đã gửi).
* **Error %:** 0.00% (Không có request nào bị lỗi, kết nối tới server ổn định).
* **Average:** [Nhập số ms trong ảnh của bạn] ms (Thời gian phản hồi trung bình).
* **Min / Max:** [Nhập số ms Min] / [Nhập số ms Max] ms (Thời gian phản hồi nhanh nhất / chậm nhất).
* **Throughput:** [Nhập số Throughput] request/sec (Lượng request xử lý trên giây).

![alt text](https://github.com/vo-hoangdung/Jmeter/blob/main/anh4.jpg)

## 5. Kết luận
* Việc cấu hình kịch bản kiểm thử trên JMeter đã thành công.
* * Hệ thống API `jsonplaceholder.typicode.com` hoạt động ổn định, không phát sinh lỗi (Error 0%) khi chịu tải 10 người dùng truy cập cùng lúc.
* Thời gian phản hồi của server tốt, đáp ứng nhanh các yêu cầu GET dữ liệu.
