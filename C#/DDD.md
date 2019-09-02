# DDD

- [DDD](#ddd)

---

聚合（以及聚合根）：聚合表示一组领域对象(包括实体和值对象)，用来表述一个完整的领域概念。而每个聚合都有一个根实体，这个根实体又叫做聚合根。举个简单的例子，一个电脑包含硬盘、CPU、内存条等，这一个组合就是一个聚合，而电脑就是这个组合的聚合根。博主觉得关于聚合的划分学问还是挺大的，需要在实践中慢慢积累。同一个实体，在不同的聚合中，它可能是聚合根，也可能不是，需要根据实际的业务决定。聚合根是聚合所表述的领域概念的主体，外部对象需要访问聚合内的实体时，只能通过聚合根进行访问，而不能直接访问。

仓储只能对聚合根做操作

在设计时，将仓储接口放在领域层，而将仓储的具体实现放在基础结构层，领域层通过接口访问数据存储