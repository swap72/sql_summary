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

