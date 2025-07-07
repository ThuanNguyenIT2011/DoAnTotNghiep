# Xây Dựng Hệ Thống IoT Chăm Sóc Cây Trồng Thông Minh

## Thông Tin Bài Báo Cáo

**Người hướng dẫn**: ThS. Phan Thanh Hy  
**Sinh viên thực hiện**: Nguyễn Văn Thuận  
**Mã số sinh viên**: N20DCCN077  
**Lớp**: D20CQCNPM01-N  
**Khóa**: 2020 – 2025  
**Hệ**: Đại học chính quy 

# Giới Thiệu
Trong bối cảnh công nghệ đang phát triển vượt bậc, việc áp dụng các công nghệ hiện đại vào sản xuất nông nghiệp đã trở thành xu hướng tất yếu nhằm đáp ứng nhu cầu ngày càng cao của xã hội. Một trong những ứng dụng nổi bật là hệ thống **IoT (Internet of Things)**, cho phép giám sát và điều khiển các yếu tố môi trường một cách tự động và chính xác. Hệ thống này giúp tăng năng suất, giảm thiểu rủi ro, và bảo vệ môi trường.

**Việt Nam** là một quốc gia nông nghiệp với phần lớn diện tích đất dành cho trồng trọt. Tuy nhiên, ngành nông nghiệp trong nước đối mặt với nhiều thách thức, đặc biệt là sâu bệnh hại cây trồng gây thiệt hại lớn cho sản xuất. Để giải quyết vấn đề này, việc kết hợp IoT và học sâu (**deep learning**) như **ResNet** trong nhận diện sâu bệnh là một giải pháp hiệu quả, giúp nông dân phát hiện nhanh chóng và chính xác các loại sâu bệnh.

## Mục tiêu
Hệ thống được xây dựng nhằm hỗ trợ người nông dân trong việc giám sát, nhận diện sâu bệnh trên cây trồng và đưa ra các biện pháp xử lý kịp thời thông qua sự kết hợp của công nghệ IoT và mô hình học sâu ResNet50.

---

## Quy trình hoạt động

### 1. Thu thập dữ liệu ảnh từ lá cây
- **ESP32-CAM**: Được sử dụng để chụp ảnh lá cây và tự động gửi ảnh lên Fire Storage Realtime Database.  
- **Người dùng hoặc nông dân**: Có thể tải ảnh trực tiếp lên giao diện web (**Angular**) để phân tích.

### 2. Truy xuất ảnh từ hệ thống lưu trữ
- Ảnh được tải về từ Fire Storage thông qua **Django server**, nơi server thực hiện truy vấn và trả dữ liệu hình ảnh về giao diện web để hiển thị.

### 3. Dự đoán bệnh trên lá cây
- Người dùng gửi yêu cầu dự đoán từ giao diện web (**Angular**) xuống **Django server**.  
- Server kích hoạt **mô hình ResNet50**, đã được huấn luyện trước, để phân tích hình ảnh và nhận diện loại bệnh trên lá cây.

### 4. Truy xuất lời khuyên điều trị
- Dựa trên kết quả dự đoán của mô hình, server truy vấn cơ sở dữ liệu để lấy thông tin chi tiết về bệnh và **lời khuyên điều trị tương ứng**.

### 5. Trả kết quả về giao diện người dùng
- Kết quả gồm **loại bệnh** và **lời khuyên điều trị** sẽ được gửi từ **Django server** lên giao diện web (**Angular**) để hiển thị cho người dùng.  
- Người dùng có thể xem thông tin và áp dụng các biện pháp điều trị phù hợp.

---

## Ưu điểm của hệ thống
- **Tự động hóa cao**: Tích hợp ESP32-CAM và công nghệ học sâu để giảm thiểu công sức thủ công.  
- **Hiệu quả**: Dự đoán chính xác và cung cấp thông tin xử lý nhanh chóng.  
- **Thân thiện với người dùng**: Giao diện trực quan giúp nông dân dễ dàng sử dụng và tiếp cận công nghệ.

---

## Công nghệ sử dụng
- **IoT**: ESP32-CAM để thu thập và gửi dữ liệu ảnh.  
- **Frontend**: Angular cho giao diện người dùng.  
- **Backend**: Django server để xử lý ảnh và thực hiện dự đoán.  
- **Deep Learning**: ResNet50 để nhận diện bệnh trên lá cây.  
- **Cơ sở dữ liệu**: Firebase Fire Storage và Realtime Database để lưu trữ và truy vấn dữ liệu.

---

## Kết luận
Quy trình hoạt động khép kín của hệ thống đảm bảo **tính chính xác**, **tốc độ xử lý**, và **hiệu quả** trong việc hỗ trợ người dùng chăm sóc cây trồng. Đây là một bước tiến quan trọng, góp phần thúc đẩy nền nông nghiệp thông minh và bền vững tại Việt Nam.
