
# SQL Join Practice Project

This project includes sample SQL code to practice different types of joins using three tables: `Customers`, `Orders`, and `Payments`.

---

## 📋 Table Structures

### Customers
```sql
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(50),
    city VARCHAR(30)
);
```

### Orders
```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
```

### Payments
```sql
CREATE TABLE Payments (
    payment_id INT PRIMARY KEY,
    order_id INT,
    amount DECIMAL(10, 2),
    payment_date DATE,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);
```

---

## 🔢 Sample Data

### Insert into `Customers`
```sql
INSERT INTO Customers VALUES
(1, 'Arun', 'Chennai'),
(2, 'Priya', 'Delhi'),
(3, 'Ravi', 'Bangalore'),
(4, 'Sneha', 'Mumbai'),
(5, 'Karan', 'Hyderabad');
```

### Insert into `Orders`
```sql
INSERT INTO Orders VALUES
(101, 1, 'Laptop', '2024-12-01'),
(102, 2, 'Phone', '2024-12-03'),
(103, 1, 'Keyboard', '2024-12-05'),
(104, 4, 'Monitor', '2024-12-07'),
(105, 5, 'Mouse', '2024-12-08');
```

### Insert into `Payments`
```sql
INSERT INTO Payments VALUES
(201, 101, 55000.00, '2024-12-02'),
(202, 102, 15000.00, '2024-12-04'),
(203, 104, 12000.00, '2024-12-08');
```

---

## 🔍 SQL Join Queries

### ✅ INNER JOIN
```sql
SELECT c.customer_name, o.product
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id;
```

### ✅ LEFT JOIN
```sql
SELECT c.customer_name, o.product
FROM Customers c
LEFT JOIN Orders o ON c.customer_id = o.customer_id;
```

### ✅ RIGHT JOIN
```sql
SELECT c.customer_name, o.product
FROM Customers c
RIGHT JOIN Orders o ON c.customer_id = o.customer_id;
```

### ✅ FULL JOIN
```sql
SELECT c.customer_name, o.product
FROM Customers c
FULL JOIN Orders o ON c.customer_id = o.customer_id;
```

### ✅ JOIN Across 3 Tables
```sql
SELECT c.customer_name, o.product, p.amount
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
FULL JOIN Payments p ON o.order_id = p.order_id;
```

---

## 🧪 Select Data (for debugging or view)
```sql
SELECT * FROM Customers;
SELECT * FROM Orders;
SELECT * FROM Payments;
```

