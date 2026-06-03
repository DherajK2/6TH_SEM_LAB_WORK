# Identifying Circumstances for Horizontal Partitioning - Practice Assignment 1

> Course: Foundations of Distributed Database Systems
>
> University: Johns Hopkins University
>
> Platform: Coursera

---

## Question 1

### In which contextual framework would the implementation of horizontal partitioning not constitute the most advantageous strategy?

**Answer**

- [ ] When the database needs to scale out to multiple nodes
- [ ] When the data can be easily divided into independent subsets
- [x] When the database requires frequent cross-partition joins
- [ ] When the database has a large volume of read-heavy transactions

---

## Question 2

### Which scenario would most benefit from horizontal partitioning?

**Answer**

- [ ] A real-time analytics system where all data needs to be processed simultaneously
- [ ] A social media application where users frequently share content across regions
- [x] An e-commerce platform where user data is predominantly accessed based on geographic region, and most transactions are local to the region
- [ ] A financial institution where the majority of transactions are global

---

## Question 3

### How might frequent cross-region interactions affect the decision to implement horizontal partitioning?

**Answer**

- [ ] Horizontal partitioning is irrelevant in this scenario
- [ ] Horizontal partitioning would not be ideal since the system requires frequent cross-region transactions and queries
- [ ] The platform would benefit from horizontal partitioning since it can distribute data efficiently across regions
- [x] Frequent cross-region interactions would cause frequent joins across partitions, diminishing the benefits of horizontal partitioning

---

## Question 4

### What constitutes a principal rationale for implementing horizontal partitioning?

**Answer**

- [ ] To simplify the database schema design
- [x] To improve query performance by reading smaller subsets of data
- [ ] To reduce the need for database backups
- [ ] To ensure data is always consistent across all nodes

---

## Question 5

### Which conditions typically necessitate the use of horizontal partitioning? (Select all that apply)

**Answer**

- [ ] High network latency between distributed nodes
- [ ] Uniform data access patterns
- [x] Limited storage capacity on a single node
- [x] Growing dataset size beyond a single node's capacity
- [x] Increased read and write throughput requirements

---

## Question 6

### Which factor would most likely drive the decision to use horizontal partitioning?

**Answer**

- [ ] The high rate of transactional consistency required for customer data
- [ ] The need to distribute data to different servers based on customer location
- [x] The ability to scale the database by logically splitting customers based on their region
- [ ] The need to maintain data consistency across all partitions

---

## Result

**Score: 5.8 / 6 (96.7%)**

## Repository

Foundations of Distributed Database Systems  
Module 3 - Practice Assignment 1  
Identifying Circumstances for Horizontal Partitioning
