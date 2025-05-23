Supplier and Purchase Order Report
Purpose: Monitor supplier performance and purchase order status.
Metrics:
Total purchase orders (purchase_order_num in inbound table).
Status of purchase orders (status in inbound table).
Visuals:
Table of purchase orders with their status.
Bar chart of purchase orders by supplier.




Here’s how you can approach building the **Supplier and Purchase Order Report** in Power BI, step by step, based on your schema and your report description:

---

## 1. **Data Model & Relationships**
- Use the `inbound` table as your main source.
- If you have a supplier table, connect `inbound[supplier_code]` (or similar) → `supplier[supplier_code]`.
- If not, use the available supplier information in the `inbound` table.

---

## 2. **Key Measures (DAX)**

**Total Purchase Orders**
```DAX
Total Purchase Orders = DISTINCTCOUNT(inbound[purchase_order_num])
```

**Purchase Orders by Status**
```DAX
Purchase Orders by Status = 
SUMMARIZE(
    inbound,
    inbound[status],
    "Order Count", DISTINCTCOUNT(inbound[purchase_order_num])
)
```

---

## 3. **Visuals**

- **Table:**  
  - Columns: `inbound[purchase_order_num]`, `inbound[status]`
  - Shows each purchase order and its current status

- **Bar Chart:**  
  - Axis: Supplier (if available, e.g., `inbound[supplier_code]` or `inbound[supplier_name]`)
  - Value: `Total Purchase Orders`
  - Shows the number of purchase orders per supplier

---

## 4. **Slicers/Filters**
- By status, supplier, or date if needed.

---

## 5. **Tips**
- If you want to analyze by supplier, ensure you have a supplier field in your `inbound` table or a related supplier table.
- Use conditional formatting in the table to highlight certain statuses (e.g., delayed, completed).

---

**Summary Table for Your Report**

| Visual Type | Axis/Columns                | Value(s)                | Filter/Slicer         |
|-------------|-----------------------------|-------------------------|-----------------------|
| Table       | Purchase Order, Status      | -                       | Status, Supplier      |
| Bar Chart   | Supplier                    | Total Purchase Orders   | Status, Supplier      |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!