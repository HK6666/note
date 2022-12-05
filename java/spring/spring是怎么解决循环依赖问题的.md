
## spring的循环依赖有几种
 1.原型模式循环依赖（无法解决）
 2.单例bean循环依赖-构造参数产生依赖（无法解决）
 3.单例bean循环依赖-setter产生依赖（可以解决）

单例发现循环依赖：先解析beanA 存入一个currentlyCreationSet 再解析beanB 又触发beanA解析，触发冲突

原型发现循环依赖：解析加入currentlyCreationSet 一样（主要是没有查询一级缓存的逻辑）用的ThreadLocal-currentlyInCreationSet

## 早期对象
	1.未进行属性注入的
	2.未进行对象init方法调用
	3.未进行后处理器处理
	4.但和最后的对象内存地址是一样的，都是同一个对象