
## spring的循环依赖有几种
 1.原型模式循环依赖（无法解决）
 2.单例bean循环依赖-构造参数产生依赖（无法解决）
 3.单例bean循环依赖-setter产生依赖（可以解决）

单例发现循环依赖：先解析beanA 存入一个currentlyCreationSet 再解析beanB 又触发beanA解析，触发冲突

原型发现循环依赖：解析加入currentlyCreationSet 一样（主要是没有查询一级缓存的逻辑）用的ThreadLocal-currentlyInCreationSet

## 早期对象
    bean的生命周期：实例化-属性赋值-初始化-销毁
	1.未进行属性注入的
	2.未进行对象init方法调用
	3.未进行后处理器处理
	4.但和最后的对象内存地址是一样的，都是同一个对象

单例bean循环依赖-setter产生依赖：先放入三级缓存（A和B都），然后再升级到二级缓存，最后完成依赖注入后升级到一级缓存 并清理二级三级缓存

1.一级缓存：存放完全初始化好的bean
2.二级缓存：存放没有填充属性的原始bean
3.三级缓存：存放bean的工厂对象