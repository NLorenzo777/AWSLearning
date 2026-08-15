# Understanding Secondary Indexes in DynamoDB [^](../README.md)

## Why Do Secondary Indexes Exist?

Before learning what a secondary index is, it's important to understand **why it exists**.

Imagine you own a library with **1 million books**.

Each book has the following information:

| Book ID | Title | Author | Genre | Year |
|---------|---------|---------|---------|------|
| B001 | Harry Potter | J.K. Rowling | Fantasy | 1997 |
| B002 | The Hobbit | J.R.R. Tolkien | Fantasy | 1937 |
| B003 | Clean Code | Robert C. Martin | Programming | 2008 |

Suppose the books are organized **only by Book ID**.

```
B001
B002
B003
B004
...
```

If someone asks:

> "Can I borrow Book ID B003?"

Finding it is very easy because the books are already organised by Book ID.

---

## The Problem

Now suppose someone asks:

> "Show me all Fantasy books."

Since the books are only organised by Book ID, you must examine every book.

```
B001 ✔ Fantasy
B002 ✔ Fantasy
B003 ✖ Programming
B004 ✔ Fantasy
...
```

This is known as a **table scan**.

With one million books, this becomes slow and inefficient.

---

# DynamoDB Works the Same Way

A DynamoDB table has a **Primary Key**.

For example:

```
BookID
```

DynamoDB is extremely fast when searching by the primary key.

```
BookID = B003
```

However, what if you want to search by:

```
Author = "J.K. Rowling"
```

or

```
Genre = "Fantasy"
```

DynamoDB cannot efficiently answer these requests unless another lookup structure exists.

This is where **Secondary Indexes** come in.

---

# Think of an Index as Another Catalogue

Real libraries usually have multiple catalogues.

For example:

- Catalogue by Author
- Catalogue by Title
- Catalogue by Genre

The books themselves never move.

Instead, the library creates additional lookup lists.

For example:

## Catalogue by Author

```
J.K. Rowling
    Harry Potter
    Fantastic Beasts

Robert C. Martin
    Clean Code
    Clean Architecture

J.R.R. Tolkien
    The Hobbit
    The Lord of the Rings
```

Now finding every Tolkien book becomes very easy.

The books are still stored in the same place.

The library simply has another way to locate them.

---

# DynamoDB Secondary Index

Suppose your table contains:

| CustomerID | Name | City |
|------------|------|------|
| 100 | Alice | London |
| 101 | Bob | Paris |
| 102 | Charlie | London |

Primary Key:

```
CustomerID
```

Finding a customer by ID is fast.

```
CustomerID = 101
```

But suppose you want:

```
City = London
```

Without an index, DynamoDB must inspect every record.

```
Alice ✔
Bob ✖
Charlie ✔
```

With a secondary index on **City**, DynamoDB maintains another lookup:

```
London
    Alice
    Charlie

Paris
    Bob
```

Now querying:

```
City = London
```

returns results almost immediately.

---

# Real-World Scenario 1 — Online Shopping

Imagine an online shopping application.

| OrderID | CustomerID | Status |
|----------|------------|---------|
| O001 | C101 | Shipped |
| O002 | C102 | Pending |
| O003 | C101 | Pending |

Primary Key:

```
OrderID
```

Looking up an order by its ID is easy.

```
OrderID = O003
```

However, customers usually ask:

> "Show me all of my orders."

This means searching by:

```
CustomerID = C101
```

Without an index, every order must be scanned.

With a secondary index:

```
CustomerID

C101
    O001
    O003

C102
    O002
```

The customer's orders are returned immediately.

---

# Real-World Scenario 2 — Food Delivery

Suppose a food delivery service stores:

| OrderID | Driver | Status |
|----------|---------|-----------|
| 1 | Mike | Delivering |
| 2 | Sarah | Delivered |
| 3 | Mike | Waiting |

Primary Key:

```
OrderID
```

A dispatcher asks:

> "Show all deliveries assigned to Mike."

Without an index, every order is checked.

With an index:

```
Mike
    Order 1
    Order 3

Sarah
    Order 2
```

The answer is returned instantly.

---

# Real-World Scenario 3 — Hospital

Suppose a hospital stores:

| PatientID | Doctor | Room |
|------------|---------|------|
| 100 | Dr Smith | 201 |
| 101 | Dr Smith | 205 |
| 102 | Dr Jones | 310 |

Primary Key:

```
PatientID
```

A doctor asks:

> "Show me all of my patients."

Without an index, every patient record must be scanned.

With an index:

```
Dr Smith

Patient100
Patient101
```

The results are immediately available.

---

# Why Not Create an Index for Every Attribute?

Every index must be maintained.

Whenever data changes:

```
Update Table
      │
      ▼
Update Every Relevant Index
```

If you have many indexes:

- More storage is required.
- More write operations are performed.
- Write costs increase.
- Writes become slightly slower.

Therefore, create indexes only for attributes that you frequently search or query.

---

# Another Analogy

Think about your phone's contact list.

Each contact contains:

```
Name
Phone Number
Company
City
```

Your phone allows you to browse contacts by:

- Name
- Company
- City

The contact itself isn't duplicated.

Instead, your phone maintains different lookup methods.

This is exactly what DynamoDB secondary indexes do.

---

# Summary

A **Secondary Index** is an additional lookup structure maintained by DynamoDB that allows you to efficiently query data using attributes other than the table's primary key, without scanning the entire table.

---

# What's Next?

DynamoDB provides two kinds of secondary indexes:

- **Global Secondary Index (GSI)**
    - Uses a different partition key (and optional sort key).
    - The most commonly used type.

- **Local Secondary Index (LSI)**
    - Uses the same partition key as the base table.
    - Uses a different sort key for alternative querying within the same partition.

Understanding how DynamoDB partitions data will make the difference between GSIs and LSIs much easier to understand.