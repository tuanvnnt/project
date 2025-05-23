# Inventory and Item Report

- Purpose: Track current stock levels and inventory movement.
- Metrics:
  - Remaining stock levels by item (`item_list` table).
  - Total inbound and outbound quantities by item.
  - Markdown prices and full prices.
- Visuals:
  - Bar chart of stock levels by item.
  - Table showing stock levels, markdown prices, and full prices.

Here’s how you can approach building the **Inventory and Item Report** in Power BI, step by step, based on your schema and your report description:

---

## 1. **Data Model & Relationships**
- Connect:
  - `inbound[barcode]` and `outbound[barcode]` (if available) → `item_list[barcode]`
  - If `barcode` is not in `inbound`/`outbound`, use another item identifier (e.g., `style_code`, `variant`)
- Use `item_list` as your main item reference table.

---

## 2. **Key Measures (DAX)**

**Total Inbound Quantity by Item**
```DAX
Total Inbound by Item = 
SUM(inbound[box_qty])
```

**Total Outbound Quantity by Item**
```DAX
Total Outbound by Item = 
SUM(outbound[box_qty])
```

**Current Stock Level by Item**
```DAX
Current Stock by Item = 
[Total Inbound by Item] - [Total Outbound by Item]
```
*(You may need to use CALCULATE and FILTER to sum by item/barcode if not directly related.)*

---

## 3. **Visuals**

- **Bar Chart:**  
  - Axis: `item_list[item_full_name]` or `item_list[barcode]`
  - Value: `Current Stock by Item`

- **Table:**  
  - Columns: `item_list[item_full_name]`, `Current Stock by Item`, `item_list[full_price]`, `item_list[markdown_price]`

---

## 4. **Slicers/Filters**
- By brand, type, or other item attributes.

---

## 5. **Tips**
- Make sure all relationships are set up in the Power BI model.
- If you want to show movement over time, use the date table and plot inbound/outbound by month.
- Use conditional formatting in the table to highlight low stock or markdowns.

---

**Summary Table for Your Report**

| Visual Type | Axis/Columns                | Value(s)                        | Filter/Slicer         |
|-------------|-----------------------------|---------------------------------|-----------------------|
| Bar Chart   | Item Name/Barcode           | Current Stock                   | Brand, Type, etc.     |
| Table       | Item Name, Stock, Prices    | Stock, Full Price, Markdown     | Brand, Type, etc.     |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!