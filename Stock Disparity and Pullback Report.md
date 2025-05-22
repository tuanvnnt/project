# Stock Disparity and Pullback Report

- Purpose: Identify mismatches between expected and actual stock levels and track pullbacks.
- Metrics:
  - Disparity in outbound (`disparity` column in `outbound` table).
  - Pullback quantities (`box_qty`, `good_qty` in `pullback` table).
- Visuals:
  - Heatmap of stock disparities by shop and region.
  - Table showing shops with the highest disparities.
  - Bar chart of pullback quantities by shop.

Here’s how you can approach building the **Stock Disparity and Pullback Report** in Power BI, step by step, following your schema and report style:

---

## 1. **Data Model & Relationships**
- Use the `outbound` table for stock disparity (`disparity` column).
- Use the `pullback` table for pullback quantities (`box`, `qty` columns).
- Connect:
  - `outbound[shop_code]` → `shop[shop_code]`
  - `pullback[from_shop]` or `pullback[to_shop]` → `shop[shop_code]`
  - `shop[province_id]` → `province[id]`
  - For region/area analysis, use `province[region]` and `province[area]`.

---

## 2. **Key Measures**

**a. Disparity Count/Value**
```DAX
Disparity Count = 
CALCULATE(
    COUNTROWS(outbound),
    NOT(ISBLANK(outbound[disparity])) && outbound[disparity] <> ""
)

Disparity Value (if numeric) = 
SUMX(
    FILTER(outbound, ISNUMBER(VALUE(outbound[disparity]))),
    VALUE(outbound[disparity])
)
```

**b. Pullback Quantities**
```DAX
Total Pullback Box = SUM(pullback[box])
Total Pullback Qty = SUM(pullback[qty])
```

---

## 3. **Visuals**

- **Heatmap:**  
  - Axis: Shop (from `shop`), Region (from `province`)
  - Value: Disparity Count or Value  
  - Use a matrix or conditional formatting in a matrix visual to create a heatmap effect.

- **Table:**  
  - Columns: Shop, Region, Disparity Value/Count  
  - Sort to show shops with the highest disparities at the top.

- **Bar Chart:**  
  - Axis: Shop  
  - Value: Total Pullback Box or Qty

---

## 4. **Slicers/Filters**
- By region, area, shop, date (if needed).

---

## 5. **Tips**
- If `disparity` is text, you may need to convert it to a number for calculations.
- For heatmap, use matrix visual with conditional formatting (color scale) on the disparity value/count.
- For pullback, you can analyze both `from_shop` and `to_shop` as needed.

---

**Summary Table for Your Report**

| Visual Type | Axis/Legend         | Value(s)                | Filter/Slicer         |
|-------------|---------------------|-------------------------|-----------------------|
| Heatmap     | Shop, Region        | Disparity Value/Count   | Region, Area, Shop    |
| Table       | Shop, Region        | Disparity Value/Count   | Region, Area, Shop    |
| Bar Chart   | Shop                | Pullback Box/Qty        | Region, Area, Shop    |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!