1. xây dưng sqlite database for inventory management
2. xây dựng các power bi report for inventory management
3. xây dựng 1 app để view các DO chưa nhập 


1 tạo tool liên kết để làm việc với database
1.1 liên kết với tool tạo DO TO để insert tự động vào table outbound sao khi tạo xong
1.2 liên kết với tool new DO để insert tự động vào table inbound sau khi check DO mới
1.4 tạo tool liên kết database để auto NXT
2 bước tạo report : dùng SQL và powerbi
2.1 báo cáo luân chuyển
- luân chuyển shop-shop HCM, shop-kho HCM dữ liệu: theo database luân chuyển import từ file báo qua mail của shop
- luân chuyển shop-kho tỉnh, dữ liệu từ inbound file
2.2 báo cáo tồn kho
- tạo 1 database chuyên import zmb52 của thư mục báo cáo tồn ngày
2.3 báo cáo hiệu xuất kho bãi
- tạo 1 database chuyên export capacity và lx02
2.4 năng xuất scan
- tool đổ dữ liệu scan hằng tuần và cập nhật vào 1 database riêng
2.5 dự báo nhu cầu
- báo cáo power bi dựa theo dữ liệu quá khứ để tạo dự báo luân chuyển và dự báo nhập new cont
2.6 lập kế hoạch năng lực
