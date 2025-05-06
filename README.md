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



1. Inventory Report1. Báo Cáo Tồn Kho
Current stock levels per SKUMức tồn kho hiện tại theo mã sản phẩm (SKU)
Overstocked and understocked itemsSản phẩm tồn kho quá nhiều hoặc quá ít
Aging inventory (unsold for X days)Hàng tồn lâu (chưa bán trong X ngày)
Seasonal item trackingTheo dõi hàng theo mùa

2. Inbound Shipment Report2. Báo Cáo Nhập Hàng
Expected deliveries from suppliersCác lô hàng sắp đến từ nhà cung cấp
Delays or discrepanciesCác lô hàng bị chậm hoặc sai lệch
Supplier performance (ontime, infull rates)Hiệu suất nhà cung cấp (giao hàng đúng hạn, đủ số lượng)

3. Outbound Delivery Report3. Báo Cáo Giao Hàng Ra
Orders dispatched (by channel: retail, ecommerce, wholesale)Các đơn hàng đã xuất (theo kênh: bán lẻ, thương mại điện tử, bán sỉ)
Carrier performance (ontime deliveries, damage claims)Hiệu suất hãng vận chuyển (giao đúng hạn, hàng hư hỏng)
Backorders or delayed shipmentsCác đơn hàng bị chậm hoặc bị thiếu

4. Warehouse Efficiency Report4. Báo Cáo Hiệu Suất Kho Hàng
Pickpackship time metricsThời gian lấy – đóng gói – giao hàng
Order accuracy rateTỷ lệ giao hàng chính xác
Labor productivityNăng suất lao động
Space utilizationMức sử dụng không gian kho

5. Transportation/Logistics Cost Report5. Báo Cáo Chi Phí Vận Chuyển/Logistics
Cost per shipment/unitChi phí mỗi lô hàng hoặc mỗi đơn vị
Freight charges breakdown (air, sea, ground)Phân tích chi phí vận chuyển (đường hàng không, đường biển, đường bộ)
Thirdparty logistics (3PL) feesChi phí thuê ngoài (3PL)
Cost per distribution channelChi phí theo từng kênh phân phối

6. Returns & Reverse Logistics Report6. Báo Cáo Hàng Hoàn Trả & Logistics Ngược
Return rate by product type or channelTỷ lệ hàng hoàn trả theo sản phẩm hoặc kênh bán
Reasons for returns (fit, quality, etc.)Lý do trả hàng (size không đúng, lỗi sản phẩm, v.v.)
Cost impact of returnsTác động chi phí do hoàn trả
Restocking efficiencyHiệu quả xử lý hàng hoàn

7. Forecast vs. Actual Report7. Báo Cáo Dự Báo So Với Thực Tế
Compare sales/demand forecasts to actual shipmentsSo sánh giữa dự báo bán hàng và sản lượng thực tế giao hàng
Identify gaps in planning or overorderingNhận diện các sai lệch trong kế hoạch hoặc đặt hàng quá mức

8. Customs & Import Compliance Report (for international fashion firms)8. Báo Cáo Hải Quan & Tuân Thủ Xuất Nhập Khẩu (đối với công ty thời trang quốc tế)
Status of import/export declarationsTrạng thái tờ khai hải quan
Duties, tariffs, and delaysThuế, phí nhập khẩu, các sự cố chậm trễ
Compliance issuesVấn đề về tuân thủ

9. Sustainability & ESG Logistics Metrics9. Báo Cáo Về Tính Bền Vững & ESG Trong Logistics
CO₂ emissions per shipmentLượng khí CO₂ phát thải mỗi chuyến hàng
Use of ecofriendly packagingTỷ lệ sử dụng bao bì thân thiện môi trường
Return reduction initiativesCác sáng kiến giảm hàng hoàn
