# Implementing Horizontal Partitioning Based on Query Patterns - Practice Assignment 2

> Course: Foundations of Distributed Database Systems
>
> University: Johns Hopkins University
>
> Platform: Coursera

---

## Question 1

### Which considerations should be evaluated when implementing horizontal partitioning based on query patterns? (Select all that apply)

**Answer**

- [x] Physical location of users
- [x] Size of each partition
- [x] Frequency of access for each partition
- [ ] Database vendor
- [ ] Backup and recovery procedures

---

## Question 2

### When designing a partitioning strategy based on query patterns, which are the best practices to follow? (Select all that apply)

**Answer**

- [x] Regularly updating partitioning strategy
- [x] Minimizing cross-partition queries
- [ ] Ensuring even distribution of data
- [x] Analyzing historical query logs
- [ ] Choosing the cheapest storage option

---

## Question 3

### Which methodologies are indispensable when employing derived horizontal fragmentation? (Select all that apply)

**Answer**

- [ ] Fragmenting based on primary key values
- [x] Fragmenting based on join operations
- [ ] Using hash functions to distribute data
- [x] Minimizing redundancy in the fragments

---

## Question 4

### What partitioning strategy would optimize query performance when queries frequently retrieve orders for specific customers?

**Answer**

- [ ] Partition the Customers table based on customer location and Orders table based on order date
- [ ] Vertically partition the Orders table to separate important columns
- [x] Apply derived horizontal fragmentation on the Orders table, aligning it with the partitioning of the Customers table
- [ ] Hash partition both tables independently

---

## Result

**Score: 4 / 4 (100%)**

## Repository

Foundations of Distributed Database Systems  
Module 3 - Practice Assignment 2  
Implementing Horizontal Partitioning Based on Query Patterns
