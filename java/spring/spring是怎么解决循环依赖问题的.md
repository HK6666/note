
## spring的循环依赖有几种
 1.原型模式循环依赖（无法解决）
 2.单例bean循环依赖-构造参数产生依赖（无法解决）
 3.单例bean循环依赖-setter产生依赖（可以解决）

单例发现循环依赖：先解析beanA 存入一个currentlyCreationSet 再解析beanB 又触发beanA解析，触发冲突

原型发现循环依赖：