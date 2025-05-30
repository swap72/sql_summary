# 🔗 SQL JOINs Summary (Cheat Sheet)

## 1. `INNER JOIN`
- Returns only rows **with matching values** in both tables.
- Excludes unmatched rows.

```sql
SELECT *
FROM A
INNER JOIN B ON A.id = B.a_id;
```

✅ Only rows where `A.id = B.a_id` exist in **both** tables.

---

## 2. `LEFT JOIN` (or `LEFT OUTER JOIN`)
- Returns **all rows from the left table** (A).
- If no match in B, shows NULLs for B's columns.

```sql
SELECT *
FROM A
LEFT JOIN B ON A.id = B.a_id;
```

✅ All rows from A. If no match in B → NULLs.

---

## 3. `RIGHT JOIN` (or `RIGHT OUTER JOIN`)
- Returns **all rows from the right table** (B).
- If no match in A, shows NULLs for A's columns.

```sql
SELECT *
FROM A
RIGHT JOIN B ON A.id = B.a_id;
```

✅ All rows from B. If no match in A → NULLs.

---

## 4. `FULL OUTER JOIN`
- Returns **all rows from both tables**.
- If no match, fills with NULLs on the side that’s missing.

```sql
SELECT *
FROM A
FULL OUTER JOIN B ON A.id = B.a_id;
```

✅ All rows from A + B, matched or not.

---

## 5. `CROSS JOIN`
- Returns the **Cartesian product**: every row in A with every row in B.

```sql
SELECT *
FROM A
CROSS JOIN B;
```

✅ All combinations of rows from A × B.



# 🔑 SQL Keys – Interview Questions Cheat Sheet

## 🧱 Basic Questions

### 1. What is a primary key?
A column (or set of columns) that **uniquely identifies each row** in a table. Cannot be NULL or duplicated.

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100)
);
```

---

### 2. What is a foreign key?
A column in one table that **refers to the primary key** in another table. It creates a **relationship** between two tables.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

---

### 3. Can a table have more than one primary key?
❌ **No.** A table can have **only one primary key**, but it can consist of **multiple columns** (composite key).

---

### 4. What is a composite key?
A primary key made of **two or more columns** that together uniquely identify a row.

```sql
PRIMARY KEY (StudentID, CourseID)
```

---

### 5. What is a unique key?
Enforces **uniqueness** of values in a column like a primary key, but **can accept one NULL**.

---

## 🧠 Intermediate to Advanced

### 6. Difference between primary key and unique key?

| Feature        | Primary Key     | Unique Key       |
|----------------|-----------------|------------------|
| Uniqueness     | ✅ Yes           | ✅ Yes            |
| NULLs Allowed  | ❌ No            | ✅ Yes (once)     |
| Count per table| Only one        | Multiple allowed |

---

### 7. What happens when you insert a duplicate primary key?
❌ SQL throws a **constraint violation error** because primary keys must be unique.

---

### 8. Can a foreign key reference a unique key?
✅ **Yes!** A foreign key can reference a **unique key** instead of a primary key.

---

### 9. What is a candidate key?
Any column (or combination of columns) that can uniquely identify rows.  
➡️ Every primary key is a candidate key, but not all candidate keys are used.

---

### 10. What is an alternate key?
A **candidate key** that is **not chosen** as the primary key.

---

## 🔐 Constraint-Related Questions

### 11. What is the purpose of key constraints?
To enforce **data integrity**, prevent duplicates, and define **relationships** between tables.

---

### 12. What is `ON DELETE CASCADE` in a foreign key?
Automatically deletes **child rows** when the **parent row** is deleted.

```sql
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
ON DELETE CASCADE
```

---

## 🧪 Practical Questions

### 13. How do you find the primary key of a table?

**In SQL Server:**
```sql
sp_pkeys 'TableName';
```

**In MySQL:**
```sql
SHOW KEYS FROM TableName WHERE Key_name = 'PRIMARY';
```

---

### 14. Can a foreign key be NULL?
✅ Yes. It means the row doesn’t reference any row in the parent table.

---

### 15. Can a table have multiple foreign keys?
✅ Yes. A table can have **many foreign keys**, referencing different parent tables.

---
