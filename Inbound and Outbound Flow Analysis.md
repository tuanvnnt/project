# SAVE CONVERSATION

## Inbound and Outbound Flow Analysis

- Purpose: Monitor the flow of goods into and out of the system.
- Metrics:
  - Total inbound quantities (`box_qty`, `input_standard`, `input_taras_defect`, `input_paper_bag`, `input_visual_merchandising`).
  - Total outbound quantities (`box_qty`, `product_qty`, `paper_bag_qty`).
- Visuals:
  - Line chart showing inbound (`good_issue_date`) and outbound (`delivery_date`) trends over time.
- Bar chart comparing inbound and outbound quantities by shop (`shop_code`).

Thank you for sharing your schema and your report idea! Here’s how you can approach **Inbound and Outbound Flow Analysis** in Power BI, step by step, tailored to your database:

---

## **1. Data Model Setup**

**Relationships to build in Power BI:**

- `inbound[shop_code]` → `shop[shop_code]`
- `outbound[shop_code]` → `shop[shop_code]`
- `shop[province_id]` → `province[id]`
- `inbound[good_issue_date]`, `outbound[delivery_date]` → `date_tb[Date]`
- (Optional) `inbound[brand_code]` → `brand[brand_code]`

---

## **2. Measures to Create**

**Inbound:**

```DAX
Total Inbound Box = SUM(inbound[box_qty])
Total Inbound Standard = SUM(inbound[input_standard])
Total Inbound Defect = SUM(inbound[input_taras_defect])
Total Inbound Paper Bag = SUM(inbound[input_paper_bag])
Total Inbound Visual Merch = SUM(inbound[input_visual_merchandising])
```

**Outbound:**

```DAX
Total Outbound Box = SUM(outbound[box_qty])
Total Outbound Product = SUM(outbound[product_qty])
Total Outbound Paper Bag = SUM(outbound[paper_bag_qty])
```

**Trend Over Time (for line chart):**

- Use `date_tb[Date]` as the X-axis.
- Use the above measures as Y-axis values.
- Filter inbound by `good_issue_date`, outbound by `delivery_date`.

**By Shop (for bar chart):**

- Axis: `shop[shop_name]` or `shop[shop_code]`
- Values: Total inbound/outbound measures.

---

## **3. Visuals to Build**

- **Line Chart:**  
  - X-axis: `date_tb[Date]`
  - Y-axis: Total inbound and outbound quantities (can use multiple lines for each measure)
  - Legend: Inbound/Outbound

- **Bar Chart:**  
  - X-axis: `shop[shop_code]` or `shop[shop_name]`
  - Y-axis: Total inbound and outbound quantities

- **Slicers:**  
  - By brand, region, area, date, etc.

---

## **4. Example DAX for Monthly Trend**

```DAX
Inbound Box by Month = 
CALCULATE(
    [Total Inbound Box],
    GROUPBY(date_tb, date_tb[Year], date_tb[Month_Number_Of_Year])
)
```

**(But usually, you just use the date table’s hierarchy in visuals.)*

---

## **5. Tips**

- Make sure your date columns are recognized as Date type in Power BI.
- Use the date table (`date_tb`) for time intelligence (trend, filtering by month/year).
- You can add more visuals for region/area by connecting through the `shop` and `province` tables.

---

## **Summary Table for Your Report**

| Visual Type   | Axis/Legend           | Value(s)                                  | Filter/Slicer         |
|---------------|-----------------------|-------------------------------------------|-----------------------|
| Line Chart    | Date                  | Inbound/Outbound quantities               | Brand, Region, Area   |
| Bar Chart     | Shop                  | Inbound/Outbound quantities               | Brand, Region, Area   |
| Slicer        | -                     | -                                         | Brand, Date, Region   |

---

If you want, I can help you with more advanced DAX (for averages, moving averages, etc.) or with other report sections! Just let me know your next focus.
