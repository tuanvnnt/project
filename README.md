1. xây dưng sqlite database for inventory management
2. xây dựng các power bi report for inventory management
3. xây dựng 1 app để view các DO chưa nhập 


- tạo tool liên kết để làm việc với database
  - liên kết với tool tạo DO TO để insert tự động vào table outbound sao khi tạo xong
  - liên kết với tool new DO để insert tự động vào table inbound sau khi check DO mới
  - tạo tool liên kết database để auto NXT
- bước tạo report : dùng SQL và powerbi
  - báo cáo luân chuyển
    - luân chuyển shop-shop HCM, shop-kho HCM dữ liệu: theo database luân chuyển import từ file báo qua mail của shop
    - luân chuyển shop-kho tỉnh, dữ liệu từ inbound file
- báo cáo tồn kho
  - tạo 1 database chuyên import zmb52 của thư mục báo cáo tồn ngày
- báo cáo hiệu xuất kho bãi
  - tạo 1 database chuyên export capacity và lx02
- năng xuất scan
  - tool đổ dữ liệu scan hằng tuần và cập nhật vào 1 database riêng
- dự báo nhu cầu
  - báo cáo power bi dựa theo dữ liệu quá khứ để tạo dự báo luân chuyển và dự báo nhập new cont
- lập kế hoạch năng lực
