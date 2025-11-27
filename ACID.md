ACID is an acronym that guarantees database transactions are processed reliably.
### A - Atomicity
**The "All or Nothing" Rule**
- In the occurrence of failure, the database is returned to its state before the transaction started.
- The transaction is all-or-nothing.

### C - Consistency
**The "Rules Must Be Followed" Rule**
Consistency ensures that a transaction brings the database from one **valid state** to another. It guarantees that all data written to the database must be valid according to all defined rules, including constraints, cascades, triggers, and any other application-specific logic.
- If a transaction would violate this (or any other) rule, it is aborted and rolled back.
- The transaction follows all database rules.
###  I - Isolation
**The "Mind Your Own Business" Rule**
Isolation ensures that concurrent execution of transactions leaves the database in the same state as if the transactions were executed **sequentially** (one after the other). It controls how and when the changes made by one transaction are visible to others.
- Transactions don't interfere with each other.
#### Isolation levels:
- read uncommited
- read commited
- repeatable read/ snapshot isolation
- serialized
### D - Durability
**The "It's Permanent" Rule**
Durability guarantees that once a transaction has been committed, it will remain committed even in the case of a system failure (like a power outage or crash). The changes are permanent and stored in non-volatile memory (like a disk).
- The database system ensures this by writing the transaction details to a log _before_ it confirms the commit. After a crash, the database can recover by replaying this log.
- Once done, a transaction's changes are permanent.


## BASE
It's important to note that while [[ACID]] is a cornerstone of traditional relational database systems (like PostgreSQL, [[MySQL]], Oracle), many modern [[NoSQL]] databases sacrifice full ACID compliance (especially strong Isolation) in favor of other advantages like scalability and performance, offering instead a "BASE" model (Basically Available, Soft state, Eventual consistency). The choice between ACID and BASE depends entirely on the specific requirements of your application.

