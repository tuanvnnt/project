Material and Item Insights
Purpose: Analyze item materials and their distribution.
Metrics:
Total items by material (material in item_material table).
Stock levels by material.
Visuals:
Pie chart of items by material.
Table showing material details and associated items.




Here’s how you can implement the **Material and Item Insights** report in Power BI, step by step, based on your schema and your requirements:

---

## 1. **Data Model & Relationships**
- Use the `item_material` table as your main source for materials.
- Connect:
  - `item_material[barcode]` → `item_list[barcode]` (to get item details and stock info)
  - If you have a stock table, connect it to `item_list[barcode]` as well.

---

## 2. **Key Measures (DAX)**

**Total Items by Material**
```DAX
Total Items by Material = 
COUNTROWS(
    FILTER(item_material, item_material[material] = SELECTEDVALUE(item_material[material]))
)
```
*(Or simply use COUNTROWS or DISTINCTCOUNT of barcodes grouped by material in visuals.)*

**Stock Levels by Material**
```DAX
Stock by Material = 
SUMX(
    FILTER(item_material, item_material[material] = SELECTEDVALUE(item_material[material])),
    RELATED(item_list[stock_qty])
)
```
*(Adjust `[stock_qty]` to your actual stock column name in `item_list`.)*

---

## 3. **Visuals**

- **Pie Chart:**  
  - Legend: `item_material[material]`
  - Values: Count of items (barcodes) per material

- **Table:**  
  - Columns: `item_material[material]`, `item_material[barcode]`, `item_list[item_full_name]`, `item_list[stock_qty]`
  - Shows material, associated items, and their stock levels

---

## 4. **Slicers/Filters**
- By material, item, or other attributes as needed.

---

## 5. **Tips**
- Make sure relationships are set up in the Power BI model.
- Use tooltips in the pie chart for more item details.
- You can add conditional formatting in the table to highlight low stock.

---

**Summary Table for Your Report**

| Visual Type | Axis/Columns                        | Value(s)                | Filter/Slicer         |
|-------------|-------------------------------------|-------------------------|-----------------------|
| Pie Chart   | Material                            | Count of Items          | Material              |
| Table       | Material, Barcode, Item Name, Stock | -                       | Material, Item        |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!