# Vấn đề :
Hiện tại, tất cả nhân viên đều dùng chung một cửa sổ trình duyệt Google Chrome mặc định. Hậu quả là phòng khám liên tục gặp sự cố hỗn loạn:  
• Xung đột phiên đăng nhập (Session Conflict): Khi Bác sĩ trực đang mở hồ sơ kê đơn cho bệnh nhân A, bạn thực tập sinh mở thêm một tab đăng nhập tài khoản Cổng học tập PTIT / GitHub cá nhân, khiến hệ thống CarePulse bị văng đăng xuất (Logout) giữa chừng.  
• Lộ lọt riêng tư: Khi Bác sĩ trưởng khoa dùng máy chiếu để hội chẩn ca bệnh nặng với tuyến trên, thanh lịch sử duyệt web và các gợi ý tìm kiếm cá nhân (mua sắm Shopee, Facebook, video Youtube) hiện lên trước mặt toàn thể đồng nghiệp.  
• Rác thanh Bookmark: Thanh dấu trang chứa hơn 80 liên kết lộn xộn, không phân loại, khiến việc tìm đường link Tra cứu Dược thư Quốc gia mất tới 3 phút mỗi ca khám.
# Yêu cầu :
**Phần 1: Báo cáo phân tích kiến trúc đa Profile**

**1.** Phân tích nguyên nhân sâu xa dẫn đến hiện tượng 'văng phiên đăng nhập' (Session Conflict) dưới góc độ lưu trữ Cookies trong thư mục User Data khi dùng chung 1 Profile.

**2.** Thiết kế Mô hình 3 Profile chuyên dụng cho máy tính trạm khám CarePulse. Với mỗi Profile, nêu rõ: Tên Profile, Mục đích sử dụng, Màu Theme nhận diện thị giác, và các loại dữ liệu được lưu trữ độc lập (Cookies, History, Bookmarks, Extensions).

**Phần 2: Thiết kế hệ thống Bookmark & Quy trình an toàn**

**3.** Dựng cây thư mục Bookmark chuẩn (`Ctrl + Shift + O`) gồm 3 thư mục chính phục vụ bác sĩ trực: `📁 01_CarePulse_Clinic`, `📁 02_Pharma_Portal`, `📁 03_Medical_Tools`. Liệt kê ít nhất 3 dịch vụ web cần lưu trong mỗi thư mục.

**4.** Hướng dẫn áp dụng mẹo Favicon-Only cho 4 trang web dùng hàng ngày (CarePulse, Cổng BHYT, Dược thư, Google Dịch) để tiết kiệm diện tích thanh công cụ gấp 3 lần.

**5.** Xử lý Bẫy an ninh: Khi có đoàn thanh tra hoặc khách mượn máy tính kiểm tra trong 30 phút, nhân viên phòng khám phải kích hoạt chế độ duyệt web nào (Guest Profile hay Incognito)? Giải thích lý do và cảnh báo nguy cơ nếu bật tính năng Cloud Sync tài khoản cá nhân trên máy trạm y tế này.
# Cách làm :


1.  Khắc phục văng phiên (Session Conflict):
    
    -   Phân tách độc lập hoàn toàn 3 Profile riêng biệt (Work, Personal, Sandbox/Test). Mỗi Profile có User Data Directory và kho lưu trữ Cookie độc lập, triệt tiêu hoàn toàn xung đột giữa tài khoản y tế CarePulse và tài khoản cá nhân.
        
2.  Cấu trúc Bookmark & Tối ưu giao diện:
    
    -   Tổ chức 3 thư mục chính:  `📁 01_CarePulse_Clinic,  `📁 02_Pharma_Portal`,  `📁 03_Medical_Tools` (chứa đầy đủ các công cụ tra cứu chuyên môn).
        
    -   Áp dụng mẹo Favicon-Only (xóa tên chữ, giữ lại biểu tượng) trên thanh Bookmark để tiết kiệm không gian hiển thị gấp 3 lần.
        
3.  Xử lý An ninh & Bẫy dữ liệu:
    
    -   Khi có thanh tra hoặc khách mượn máy: Bắt buộc dùng Guest Profile (cách ly hoàn toàn dữ liệu, tự xóa khi đóng) thay vì ẩn danh (Incognito).
        
    -  Cảnh báo tối cao:Tuyệt đối khôngbật Cloud Sync tài khoản cá nhân lên máy trạm y tế dùng chung để tránh rò rỉ mật khẩu và dữ liệu bệnh nhân.
