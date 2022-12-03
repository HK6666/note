Transactions and Concurrency
事务和并发

Goal of DBMS: “data integrity is always maintained
数据库的目标: 始终保持数据完整性

DBMS通过三个概念确保数据的完整性（ensure data integrity）
	1.Transation processing 事务处理
	2.Concurrency control 并发控制
	3.Recovery mechanisms 恢复机制

什么是事务处理
	A database transaction is a "logical unit of work" in a DB application

A transaction must always terminate, either
事务只有执行成功或者失败
	• successfully (COMMIT), with all changes correctly preserved
	• unsuccessfully (ABORT), with database unchanged

![[事务只有成功和失败.png]]

To describe transaction effects, we consider:
	• READ - transfer data from disk to memory
	• WRITE - transfer data from memory to disk
	• ABORT - terminate transaction, unsuccessfully
	• COMMIT - terminate transaction, successfully

事务操作符号定义
![[事务操作符号定义.png]]

事务前后状态必须一致

ACID Properties
Data integrity is assured if transactions satisfy the following:
Atomicity（原子性）
• Either all operations of transaction are reflected in database or none are.
（事务的操作要么反映在数据库中，要么没有）
Consistency（一致性）
• Execution of a transaction in isolation preserves data consistency.
（隔离执行事务可保持数据一致性）
Isolation（隔离性）
• Each transaction is "unaware" of other transactions executing concurrently in the 
system.（执行事务的过程，系统中其他组件不可见）
Durability（持久性）
• After a transaction completes successfully, its changes persist even after subsequent 
system failure.（事务一旦执行成功，则后续即使故障也会存在）

Atomicity is handled by the commit and rollback mechanisms.
• commit saves all changes and ends the transaction
• rollback undoes changes already made by the transaction
Durability is handled by implementing stable storage, via
• redundancy, to deal with hardware failures
• logging/checkpoint mechanisms, to recover state

事务的序列化处理（主要研究调度是否是  schedule is conflict serializible.）


Testing Serializability - precedence graph
有 写操作在读操作前面才画线

![[序列化的例子.png]]

例子二：
	![[序列化的例子2.png]]

![[序列化的例子3.png]]

并发控制的种类
Concurrency Control Methods
Approaches that DBMS use to produce serializable schedules:
• lock-based: synchronise transaction execution via locks on some portion of 
the database.
• multiversion-based: allow multiple “consistent” versions of the data to exist, 
and allocate each transaction exclusively to access one version.
• timestamp-based: organise transaction execution in advance by assigning 
timestamps to operations.
• validation-based (optimistic concurrency control): exploit typical 
execution-sequence properties of transactions to determine safety 
dynamically

Lock-based Concurrency Control
读锁（共享锁）
	多个事务都可以读到的锁，但只读不能修改
写锁（排他锁）
	只有一个事务可以获取和修改

  
为了保证可串行化，事务还必须遵守两阶段锁定协议
	第一个阶段Growing Phase 不停的获取锁
	第二个阶段Shrinking Phase，不停的释放锁


Problems with Locking
Appropriate locking can guarantee correctness.
However, it also introduces potential undesirable effects:
• Deadlock
No transactions can proceed; each waiting on lock held by another.
• Starvation
One transaction is permanently "frozen out" of access to data.
• Reduced performance
Locking introduces delays while waiting for locks to be released.