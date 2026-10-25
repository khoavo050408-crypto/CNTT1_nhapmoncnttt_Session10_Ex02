# 1. Mục tiêu

Nhận diện và sửa lỗi vi phạm 5 Quy tắc Vàng trong tư duy Database. Vận dụng hàm TRIM() để làm sạch dữ liệu trước khi sử dụng AutoFilter.

# 2. Bối cảnh và vấn đề

Startup đang sử dụng một bảng Excel để quản lý thiết bị IoT. Khi sử dụng tổ hợp phím Ctrl + Shift + L để lọc các thiết bị bị hỏng, kết quả xuất hiện thành hai nhóm riêng biệt: “hỏng” có dấu cách và “hỏng” không có dấu cách.

Nguyên nhân là do dữ liệu trong cột Trạng thái chứa các khoảng trắng thừa. Điều này khiến Excel nhận diện chúng là những giá trị khác nhau dù hiển thị giống nhau.

Ngoài ra, nút Filter không hoạt động trên toàn bộ bảng do xuất hiện một hàng trống ở giữa vùng dữ liệu. Bảng tính còn chứa các ô gộp (Merge Cell) tại hàng tiêu đề, gây ảnh hưởng đến quá trình lọc và quản lý dữ liệu.

# 3. Phân tích vấn đề

Bảng tính hiện tại vi phạm một số quy tắc vàng trong tư duy Database.

Thứ nhất, dữ liệu trong mỗi cột cần thống nhất về loại thông tin để thuận tiện cho việc lọc, sắp xếp và xử lý.

Thứ hai, không nên gộp ô trong vùng dữ liệu. Việc sử dụng Merge Cell tại hàng tiêu đề có thể gây khó khăn khi sử dụng AutoFilter.

Thứ ba, không để hàng trống xen giữa dữ liệu vì Excel có thể xác định vùng dữ liệu không đầy đủ, khiến Filter chỉ áp dụng đến một phần của bảng.

Thứ tư, dữ liệu phải thống nhất về cách nhập. Các giá trị như “hỏng” và “hỏng ” có khoảng trắng thừa có thể bị Excel xem là hai giá trị khác nhau khi lọc.

Thứ năm, mỗi hàng cần đại diện cho một bản ghi và mỗi cột phải có tiêu đề rõ ràng để bảo đảm cấu trúc bảng nhất quán.

# 4. Khắc phục và hoàn thiện dữ liệu

## 4.1. Gỡ bỏ Merge Cell

Chọn hàng tiêu đề đang chứa các ô gộp. Sau đó, vào Home → Merge & Center → Unmerge Cells để gỡ bỏ gộp ô.

Kiểm tra và bảo đảm mỗi cột có một tiêu đề riêng biệt, chẳng hạn như Mã thiết bị, Tên thiết bị, Vị trí và Trạng thái.

## 4.2. Xóa các hàng trống

Xác định các hàng trống nằm xen giữa vùng dữ liệu. Chọn các hàng cần xóa, nhấp chuột phải và chọn Delete.

Kiểm tra lại để bảo đảm các bản ghi được nối liền nhau, không còn hàng trống làm gián đoạn bảng.

## 4.3. Sử dụng hàm TRIM() để làm sạch cột Trạng thái

Giả sử cột Trạng thái nằm ở cột E và dữ liệu bắt đầu từ ô E2. Tại một cột phụ, nhập công thức:

`=TRIM(E2)`

Sao chép công thức xuống toàn bộ các hàng dữ liệu. Sau đó, sao chép cột kết quả đã làm sạch, chọn cột Trạng thái ban đầu và sử dụng Paste Special → Values để thay thế dữ liệu cũ bằng các giá trị đã làm sạch.

Cuối cùng, xóa cột phụ nếu không còn cần sử dụng.

Hàm TRIM() có tác dụng loại bỏ khoảng trắng đầu và cuối chuỗi, đồng thời thu gọn các khoảng trắng thông thường liên tiếp ở giữa chuỗi.

Ví dụ, giá trị “hỏng ” hoặc “ hỏng” sẽ được chuyển thành “hỏng”. Tuy nhiên, nếu dữ liệu chứa khoảng trắng đặc biệt như ký tự không ngắt dòng CHAR(160), cần xử lý bổ sung bằng hàm SUBSTITUTE().

## 4.4. Bật lại AutoFilter

Sau khi hoàn thiện cấu trúc và làm sạch dữ liệu, chọn một ô bất kỳ trong bảng rồi nhấn Ctrl + Shift + L để bật AutoFilter.

Nhấp vào nút lọc tại cột Trạng thái và chọn giá trị “hỏng” để hiển thị các thiết bị đang bị lỗi.

Nếu cần quản lý dữ liệu lâu dài, có thể chọn toàn bộ vùng dữ liệu và nhấn Ctrl + T để chuyển thành Excel Table. Khi đó, bảng có cấu trúc rõ ràng và dễ mở rộng khi thêm thiết bị mới.

# 5. Kết quả và kết luận

Sau khi thực hiện các bước khắc phục, bảng Excel quản lý thiết bị IoT có cấu trúc dữ liệu thống nhất, không còn ô gộp gây ảnh hưởng đến vùng dữ liệu hoặc hàng trống làm gián đoạn bảng.

Cột Trạng thái được làm sạch bằng hàm TRIM(), giúp hạn chế tình trạng một giá trị bị chia thành nhiều nhóm khi sử dụng AutoFilter.

Việc tuân thủ các quy tắc vàng trong tư duy Database giúp dữ liệu dễ quản lý, giảm sai sót và nâng cao hiệu quả tìm kiếm, lọc và phân tích thông tin. Đây là nền tảng quan trọng để xây dựng các bảng dữ liệu có chất lượng và phục vụ tốt cho công tác quản lý thiết bị IoT.
