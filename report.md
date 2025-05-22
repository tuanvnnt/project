# REPORT DESCRIPTION

1Inbound and Outbound Flow Analysis

- Purpose: Monitor the flow of goods into and out of the system.
- Metrics:
  - Total inbound quantities (`box_qty`, `input_standard`, `input_taras_defect`, `input_paper_bag`, `input_visual_merchandising`).
  - Total outbound quantities (`box_qty`, `product_qty`, `paper_bag_qty`).
- Visuals:
  - Line chart showing inbound (`good_issue_date`) and outbound (`delivery_date`) trends over time.
- Bar chart comparing inbound and outbound quantities by shop (`shop_code`).

2Delivery Timeliness Report

- Purpose: Track delivery performance and identify delays.
- Metrics:
  - Difference between `order_date` and `delivery_date` in the `outbound` table.
  - Count of late deliveries.
- Visuals:
  - KPI card for average delivery time.
  - Line chart showing delivery performance over time.
  - Table of late deliveries by shop (`shop_code`) and region (`province`).

3Stock Disparity and Pullback Report

- Purpose: Identify mismatches between expected and actual stock levels and track pullbacks.
- Metrics:
  - Disparity in outbound (`disparity` column in `outbound` table).
  - Pullback quantities (`box_qty`, `good_qty` in `pullback` table).
- Visuals:
  - Heatmap of stock disparities by shop and region.
  - Table showing shops with the highest disparities.
  - Bar chart of pullback quantities by shop.

4Shop Performance Report

- Purpose: Evaluate the performance of individual shops.
- Metrics:
  - Total inbound and outbound quantities per shop.
  - Pullback quantities per shop.
- Visuals:
  - Bar chart of inbound and outbound quantities by shop.
  - Map visualization using `latitude` and `longitude` from the `shop` table.

5Inventory and Item Report

- Purpose: Track current stock levels and inventory movement.
- Metrics:
  - Remaining stock levels by item (`item_list` table).
  - Total inbound and outbound quantities by item.
  - Markdown prices and full prices.
- Visuals:
  - Bar chart of stock levels by item.
  - Table showing stock levels, markdown prices, and full prices.

6Defect and Issue Tracking Report

- Purpose: Monitor issues and resolutions in logistics.
- Metrics:
  - Total defects logged (`issue` in `defect` table).
  - Resolved vsunresolved issues.
- Visuals:
  - Table of defects with their status and solutions.
  - KPI card for the number of unresolved issues.

7Regional Logistics Report

- Purpose: Analyze logistics performance by region.
- Metrics:
  - Total inbound and outbound quantities by region (`region` in `province` table).
  - Pullback quantities by region.
- Visuals:
  - Map visualization of logistics performance by region.
  - Bar chart of inbound and outbound quantities by region.

8Brand Performance Report

- Purpose: Analyze performance by brand.
- Metrics:
  - Total inbound and outbound quantities by brand (`brand_code`).
  - Pullback quantities by brand.
- Visuals:
  - Pie chart of inbound and outbound quantities by brand.
  - Bar chart of pullback quantities by brand.

9Daily Activity Report

- Purpose: Track daily logistics activities and notes.
- Metrics:
  - Total quantities (`box_qty`, `good_qty` in `diary` table) by date.
  - Notes and staff activity.
- Visuals:
  - Line chart of daily quantities.
  - Table of diary entries with notes and staff.

10Supplier and Purchase Order Report

- Purpose: Monitor supplier performance and purchase order status.
- Metrics:
  - Total purchase orders (`purchase_order_num` in `inbound` table).
  - Status of purchase orders (`status` in `inbound` table).
- Visuals:
  - Table of purchase orders with their status.
  - Bar chart of purchase orders by supplier.

11Material and Item Insights

- Purpose: Analyze item materials and their distribution.
- Metrics:
  - Total items by material (`material` in `item_material` table).
  - Stock levels by material.
- Visuals:
  - Pie chart of items by material.
  - Table showing material details and associated items.

These reports can be created in Power BI by connecting to your SQLite database and leveraging the relationships defined in your schemaLet me know if you need help with specific SQL queries, DAX measures, or Power BI setup!
