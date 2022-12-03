RDBMS的定义
	Data is organised into relations (table) and relationships + constraints
	数据被表，关系，约束所组织和管理

NoSQL的定义
	NoSQL = Not Only SQL models or non-relational database

为什么用NoSQL
	1.需要更大的可扩展性（greater scalability)
	2.high read and write throughput(吞吐量)
	3.no require a fixed table schema and use the concept of joins(不需要完整的表和连接的概念)
	4.所有的NoSQL 都没有完整的满足ACID


关系型数据库的局限性：
	在大数据的环境下会导致许多表的连接（降低查询性能，以及可扩展性弱）

Key-Value 存储（一种NoSQL）的特点
	1、一个 key-value 数据存储系统， 只支持一些基本操作， 如： SET(key, value)和 GET(key) 等；
	2、分布式：多台机器（nodes）同时存储数据和状态，彼此交换消息来保持数据一致，可视为一个完整的存储系统。  
	3、数据一致：所有机器上的数据都是同步更新的、不用担心得到不一致的结果；  
	4、冗余： 所有机器 （nodes） 保存相同的数据， 整个系统的存储能力取决于单台机器 （node）的能力；  
	5、容错：如果有少数 nodes 出错，比如重启、当机、断网、网络丢包等各种 fault/fail 都不影响整个系统的运行；  
	6、 高可靠性：容错、冗余等保证了数据库系统的可靠性。
	
Document-based databases（基于文档的数据库）
	1. 集合中的文档可以有不同的属性（表示不同的数据），但通常一个集合的所有文档都具有相似或者相关的用途
	2. 没有连接操作，所有内容都嵌入到单个对象中去
	3. 嵌入的对象通常为一对多的结果
	4. 一次检索请求足以得到相关的想要的信息

文档型数据库通常不适用于
	1.多对多的对象关系很难表达
	2.不支持acid事务，只保证单条数据的原子性和最终一致性
	3.不支持多表查询
	4.对一致性要求高的应用目前不太合适（性能）

数据库选择:
	1.如果应用程序数据对象看起来更像一棵树（类似文档）
		use the document-based model
	2. 如果多对多的关系是中新，那么选择关系型数据库比较合理，因为可以使用连接查询
	3. 如果数据像一个社交网络：则用图形模型比较合适

Graph-like Models（类似图的模型）:
	Vertices/notes: represent entities(表示实体)
	Edege/arcs: represent relationships(表示关系)

Benefits of using XML in document(在文档中使用XML的好处)
	• Self-describing, modular and portable data
	• A common, widely accepted data representation language for the Web
	• Standard support for checking validity of data (XML can have a schema)
	• Efficient search and query language
	• Standard support for querying XML docs 
	• Quick and simple search (XPath)
	• More comprehensive keyword + structure based search possible as well 
	(XQuery)

NoSQL的优缺点:
	1.不同的数据模型适用不同的场景
	2.通常为轻量级的应用，no schema required and need the relaxation in data consistency requirement
	3.没有成熟的RDBMS



	