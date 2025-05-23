# Shop Performance Report

- Purpose: Evaluate the performance of individual shops.
- Metrics:
  - Total inbound and outbound quantities per shop.
  - Pullback quantities per shop.
- Visuals:
  - Bar chart of inbound and outbound quantities by shop.
  - Map visualization using `latitude` and `longitude` from the `shop` table.

Here’s how to approach building the **Shop Performance Report** in Power BI, step by step, based on your schema and your report description:

---

## 1. **Data Model & Relationships**
- Connect:
  - `inbound[shop_code]` → `shop[shop_code]`
  - `outbound[shop_code]` → `shop[shop_code]`
  - `pullback[from_shop]` or `pullback[to_shop]` → `shop[shop_code]`
- Use `shop[latitude]` and `shop[longitude]` for map visuals.

---

## 2. **Key Measures (DAX)**

**Total Inbound Quantity per Shop**
```DAX
Total Inbound = SUM(inbound[box_qty])
```

**Total Outbound Quantity per Shop**
```DAX
Total Outbound = SUM(outbound[box_qty])
```

**Total Pullback Quantity per Shop**
```DAX
Total Pullback = 
CALCULATE(
    SUM(pullback[box]),
    FILTER(pullback, pullback[from_shop] = shop[shop_code])
)
```
*(Or sum for both `from_shop` and `to_shop` as needed)*

---

## 3. **Visuals**

- **Bar Chart:**  
  - Axis: `shop[shop_name]` or `shop[shop_code]`
  - Values: `Total Inbound`, `Total Outbound`, `Total Pullback` (as series)

- **Map Visualization:**  
  - Location: `shop[latitude]`, `shop[longitude]`
  - Size/Color: `Total Inbound`, `Total Outbound`, or `Total Pullback`
  - Tooltip: Show shop name and quantities

---

## 4. **Slicers/Filters**
- By region, brand, or other shop attributes if needed.

---

## 5. **Tips**
- Make sure all relationships are set up in the Power BI model.
- Use tooltips on the map for more shop details.
- You can use clustered bar/column charts for easy comparison.

---

**Summary Table for Your Report**

| Visual Type | Axis/Location           | Value(s)                       | Filter/Slicer         |
|-------------|------------------------|--------------------------------|-----------------------|
| Bar Chart   | Shop Name/Code         | Inbound, Outbound, Pullback    | Region, Brand, etc.   |
| Map         | Latitude, Longitude    | Inbound/Outbound/Pullback      | Region, Brand, etc.   |

---

Let me know if you want help with specific DAX, Power BI visuals, or advanced filtering!