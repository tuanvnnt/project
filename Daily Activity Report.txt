Daily Activity Report
Purpose: Track daily logistics activities and notes.
Metrics:
Total quantities (box_qty, good_qty in diary table) by date.
Notes and staff activity.
Visuals:
Line chart of daily quantities.
Table of diary entries with notes and staff.


Here’s how to approach building the **Daily Activity Report** in Power BI, step by step, based on your description and schema:

---

## 1. **Data Model & Relationships**
- Use the `diary` table as your main source.
- Connect:
  - `diary[diary_date]` → `date_tb[Date]`
  - `diary[staff]` → staff table (if you have one, otherwise just use as text)

---

## 2. **Key Measures (DAX)**

**Total Box Quantity by Date**
```DAX
Total Box Qty = SUM(diary[box])
```

**Total Good Quantity by Date**
```DAX
Total Good Qty = SUM(diary[qty])
```

---

## 3. **Visuals**

- **Line Chart:**  
  - X-axis: `diary[diary_date]` (or `date_tb[Date]`)
  - Y-axis: `Total Box Qty` and/or `Total Good Qty`
  - Legend: Quantity type (if you want both lines)

- **Table:**  
  - Columns: `diary[diary_date]`, `diary[box]`, `diary[qty]`, `diary[staff]`, `diary[note]`
  - You can add filters for staff or date if needed

---

## 4. **Slicers/Filters**
- By staff, date, or other relevant fields.

---

## 5. **Tips**
- Use tooltips in the line chart to show notes or staff for each day.
- Conditional formatting in the table can highlight days with high or low activity.

---

**Summary Table for Your Report**

| Visual Type | Axis/Columns                | Value(s)                | Filter/Slicer         |
|-------------|-----------------------------|-------------------------|-----------------------|
| Line Chart  | Date                        | Box Qty, Good Qty       | Staff, Date           |
| Table       | Date, Box, Qty, Staff, Note | -                       | Staff, Date           |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!