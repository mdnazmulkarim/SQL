### Adding some common SQL:

**1: Binary Tree, detecting Leaf, inner, root node**

| Comumn | Type    |
|--------|---------|
| N      | Integer |
| P      | Integer |

Sample Data:

| N   | P    |
|-----|------|
| 1   | 2    |
| 3   | 2    |
| 6   | 8    |
| 9   | 8    |
| 2   | 5    |
| 8   | 5    |
| 5   | null |

```
SELECT  outerT.N,
    CASE 
        WHEN outerT.P IS NULL THEN 'Root'
        WHEN NOT EXISTS (
                SELECT  1 FROM  BST innerT WHERE  innerT.P = outerT.N
            ) THEN 'Leaf'
        ELSE 'Inner' 
    END
FROM BST outerT order by outerT.N;
```

