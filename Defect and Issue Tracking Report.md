# Defect and Issue Tracking Report

- Purpose: Monitor issues and resolutions in logistics.
- Metrics:
  - Total defects logged (`issue` in `defect` table).
  - Resolved vsunresolved issues.
- Visuals:
  - Table of defects with their status and solutions.
  - KPI card for the number of unresolved issues.

Here’s how you can approach building the **Defect and Issue Tracking Report** in Power BI, step by step, based on your schema and report description:

---

## 1. **Data Model & Relationships**
- Use the `defect` table as your main source.
- Connect:
  - `defect[purchase_order_num]` → `inbound[purchase_order_num]` (if you want to relate defects to inbound records)
  - `defect[barcode]` → `item_list[barcode]` (for item details)

---

## 2. **Key Measures (DAX)**

**Total Defects Logged**
```DAX
Total Defects = COUNTROWS(defect)
```

**Unresolved Issues Count**  
*(Assume unresolved if `solution` is blank or null)*
```DAX
Unresolved Issues = 
CALCULATE(
    COUNTROWS(defect),
    ISBLANK(defect[solution]) || defect[solution] = ""
)
```

**Resolved Issues Count**
```DAX
Resolved Issues = 
CALCULATE(
    COUNTROWS(defect),
    NOT(ISBLANK(defect[solution])) && defect[solution] <> ""
)
```

---

## 3. **Visuals**

- **Table:**  
  - Columns: `defect[barcode]`, `defect[purchase_order_num]`, `defect[defect_type]`, `defect[defect_qty]`, `defect[solution]`, `defect[note]`, `defect[checklist]`
  - Add a status column: "Resolved"/"Unresolved" based on `solution`

- **KPI Card:**  
  - Value: `Unresolved Issues`

---

## 4. **Slicers/Filters**
- By defect type, item, purchase order, or date (if available).

---

## 5. **Tips**
- Use conditional formatting in the table to highlight unresolved issues.
- You can add a pie or bar chart to show the proportion of resolved vs unresolved issues.

---

**Summary Table for Your Report**

| Visual Type | Columns/Value                | Filter/Slicer         |
|-------------|-----------------------------|-----------------------|
| Table       | Defect details, status      | Defect type, item     |
| KPI Card    | Unresolved Issues           | -                     |
| Pie/Bar     | Resolved vs Unresolved      | -                     |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!

Here’s how you can approach building the **Defect and Issue Tracking Report** in Power BI, step by step, based on your schema and report description:

---

## 1. **Data Model & Relationships**
- Use the `defect` table as your main source.
- Connect:
  - `defect[purchase_order_num]` → `inbound[purchase_order_num]` (if you want to relate defects to inbound records)
  - `defect[barcode]` → `item_list[barcode]` (for item details)

---

## 2. **Key Measures (DAX)**

**Total Defects Logged**
```DAX
Total Defects = COUNTROWS(defect)
```

**Unresolved Issues Count**  
*(Assume unresolved if `solution` is blank or null)*
```DAX
Unresolved Issues = 
CALCULATE(
    COUNTROWS(defect),
    ISBLANK(defect[solution]) || defect[solution] = ""
)
```

**Resolved Issues Count**
```DAX
Resolved Issues = 
CALCULATE(
    COUNTROWS(defect),
    NOT(ISBLANK(defect[solution])) && defect[solution] <> ""
)
```

---

## 3. **Visuals**

- **Table:**  
  - Columns: `defect[barcode]`, `defect[purchase_order_num]`, `defect[defect_type]`, `defect[defect_qty]`, `defect[solution]`, `defect[note]`, `defect[checklist]`
  - Add a status column: "Resolved"/"Unresolved" based on `solution`

- **KPI Card:**  
  - Value: `Unresolved Issues`

---

## 4. **Slicers/Filters**
- By defect type, item, purchase order, or date (if available).

---

## 5. **Tips**
- Use conditional formatting in the table to highlight unresolved issues.
- You can add a pie or bar chart to show the proportion of resolved vs unresolved issues.

---

**Summary Table for Your Report**

| Visual Type | Columns/Value                | Filter/Slicer         |
|-------------|-----------------------------|-----------------------|
| Table       | Defect details, status      | Defect type, item     |
| KPI Card    | Unresolved Issues           | -                     |
| Pie/Bar     | Resolved vs Unresolved      | -                     |

---

Let me know if you want help with specific DAX, SQL queries, or Power BI visual setup for this report!