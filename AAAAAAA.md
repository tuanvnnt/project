
## Regional Logistics Report

- Purpose: Analyze logistics performance by region.
- Metrics:
  - Total inbound and outbound quantities by region (`region` in `province` table).
  - Pullback quantities by region.
- Visuals:
  - Map visualization of logistics performance by region.
  - Bar chart of inbound and outbound quantities by region.

## Brand Performance Report

- Purpose: Analyze performance by brand.
- Metrics:
  - Total inbound and outbound quantities by brand (`brand_code`).
  - Pullback quantities by brand.
- Visuals:
  - Pie chart of inbound and outbound quantities by brand.
  - Bar chart of pullback quantities by brand.

## Daily Activity Report

- Purpose: Track daily logistics activities and notes.
- Metrics:
  - Total quantities (`box_qty`, `good_qty` in `diary` table) by date.
  - Notes and staff activity.
- Visuals:
  - Line chart of daily quantities.
  - Table of diary entries with notes and staff.

## Supplier and Purchase Order Report

- Purpose: Monitor supplier performance and purchase order status.
- Metrics:
  - Total purchase orders (`purchase_order_num` in `inbound` table).
  - Status of purchase orders (`status` in `inbound` table).
- Visuals:
  - Table of purchase orders with their status.
  - Bar chart of purchase orders by supplier.

## Material and Item Insights

- Purpose: Analyze item materials and their distribution.
- Metrics:
  - Total items by material (`material` in `item_material` table).
  - Stock levels by material.
- Visuals:
  - Pie chart of items by material.
  - Table showing material details and associated items.

These reports can be created in Power BI by connecting to your SQLite database and leveraging the relationships defined in your schemaLet me know if you need help with specific SQL queries, DAX measures, or Power BI setup!
