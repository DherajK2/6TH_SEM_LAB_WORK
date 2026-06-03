# Introduction to Distributed Database Architectures - Module 2

> Course: Foundations of Distributed Database Systems  
> University: Johns Hopkins University  
> Platform: Coursera

## Question 1
**Which of the following most accurately reflects the role of directory management in a distributed database system?**

### Answer
- [x] To maintain a comprehensive and dynamic catalog of data fragments, including their current locations, and to update this catalog in response to changes such as node additions, removals, and data fragment migration.

---

## Question 2
**Which types of transparency are crucial for ensuring a seamless experience in a distributed database system?**

### Answers
- [ ] Transaction Transparency
- [x] Replication Transparency
- [x] Network Transparency
- [ ] Schema Transparency
- [x] Data Independence

---

## Question 3
**Which concurrency control techniques are utilized in distributed database systems to ensure transaction integrity and consistency?**

### Answers
- [x] Timestamp Ordering
- [x] Multiversion Concurrency Control (MVCC)
- [ ] Data Replication
- [x] Two-Phase Locking (2PL)
- [ ] Shadow Paging

---

## Question 4
**What is the predominant rationale for implementing redundancy in a distributed database system?**

### Answer
- [x] To enhance system reliability and maintain continuous data availability even in the event of node failures, network partitions, or other disruptions, while balancing the trade-offs in storage overhead and data synchronization complexity.

---

## Question 5
**What is a major challenge in ensuring data consistency across geographically distributed nodes?**

### Answer
- [x] Ensuring global data consistency and synchronization across nodes despite the challenges posed by network latency, partitions, and the need for distributed consensus protocols.

---

## Disclaimer

These notes are intended for educational and revision purposes while studying the Coursera course **Foundations of Distributed Database Systems** offered by **Johns Hopkins University**.

Please use these notes responsibly and adhere to Coursera's Honor Code.
