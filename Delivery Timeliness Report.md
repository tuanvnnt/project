## Delivery Timeliness Report

- Purpose: Track delivery performance and identify delays.
- Metrics:
  - Difference between `order_date` and `delivery_date` in the `outbound` table.
  - Count of late deliveries.
- Visuals:
  - KPI card for average delivery time.
  - Line chart showing delivery performance over time.
  - Table of late deliveries by shop (`shop_code`) and region (`province`).

  Here’s how to approach building your **Delivery Timeliness Report** in Power BI, step by step, based on your description:

---

### 1. **Data Model & Relationships**
- Use the `outbound` table as your main fact table.
- Connect:
  - `outbound[shop_code]` → `shop[shop_code]`
  - `shop[province_id]` → `province[id]`
  - `outbound[order_date]` and `outbound[delivery_date]` → `date_tb[Date]` (for time-based visuals)

---

### 2. **Key DAX Measures**

**a. Delivery Time (Days) for each outbound record**
```DAX
Delivery Time (Days) = 
DATEDIFF(outbound[order_date], outbound[delivery_date], DAY)
```

**b. Average Delivery Time**
```DAX
Avg Delivery Time = 
AVERAGEX(
    outbound,
    DATEDIFF(outbound[order_date], outbound[delivery_date], DAY)
)
```

**c. Count of Late Deliveries**  
*(Assume late if delivery time > 2 days; adjust threshold as needed)*
```DAX
Late Delivery Count = 
CALCULATE(
    COUNTROWS(outbound),
    DATEDIFF(outbound[order_date], outbound[delivery_date], DAY) > 2
)
```

---

### 3. **Visuals to Build**

- **KPI Card:**  
  - Show `Avg Delivery Time`

- **Line Chart:**  
  - X-axis: `date_tb[Date]` (or month/year)
  - Y-axis: `Avg Delivery Time` or `Late Delivery Count`
  - Legend: Optional (by region, shop, etc.)

- **Table (for late deliveries):**  
  - Columns: `shop[shop_code]`, `province[province]`, `order_date`, `delivery_date`, `Delivery Time (Days)`
  - Filter: Only show rows where `Delivery Time (Days)` > 2

---

### 4. **Slicers/Filters**

- By region, shop, date, etc.

---

**Summary:**  
- Build relationships to connect `outbound`, `shop`, and `province`.
- Create DAX measures for delivery time and late deliveries.
- Use KPI, line chart, and filtered table visuals as described.

Let me know if you want help with specific DAX, visuals, or advanced filtering!