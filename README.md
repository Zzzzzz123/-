# - 设计模式 六大原则

设计模式之六大原则——开闭原则（OCP）
开闭原则（Open Closed Principle）是Java世界里最基础的设计原则，它指导我们如何建立一个稳定的、灵活的系统。

 

定义：

一个软件实体如类、模块和函数应该对扩展开放，对修改关闭。

Softeware entities like classes,modules and functions should be open for extension but closed for modifications.

 

开闭原则的含义是说一个软件实体应该通过扩展来实现变化，而不是通过修改已有代码来实现变化。

软件实体包括以下几个部分：

项目或软件产品中按照一定的逻辑规则划分的模块
抽象和类
方法
开闭原则是为软件实体的未来事物而制定的对现行开发设计进行约束的一个原则。

 

注意：开闭原则对扩展开放，对修改关闭，并不意味着不做任何修改，低层模块的变更，必然要有高层模块进行耦合，否则就是一个孤立无意义的代码片段了。

 

变化的类型：

逻辑变化
子模块变化
可见试图变化
一个项目的基本路径应该是这样的：项目开发、重构、测试、投产、运维，其中的重构可以对原有的设计和代码进行修改，运维尽量减少对原有代码修改，保持历史代码的纯洁性，提高系统的稳定性。

 

开闭原则的重要性：

开闭原则对测试的影响
开闭原则可是保持原有的测试代码仍然能够正常运行，我们只需要对扩展的代码进行测试就可以了。

开闭原则可以提高复用性
在面向对象的设计中，所有的逻辑都是从原子逻辑组合而来的，而不是在一个类中独立实现一个业务逻辑。只有这样代码才可以复用，粒度越小，被复用的可能性就越大。

开闭原则可以提高可维护性
面向对象开发的要求
 

如何使用开闭原则：

抽象约束
第一，通过接口或者抽象类约束扩展，对扩展进行边界限定，不允许出现在接口或抽象类中不存在的public方法；

第二，参数类型、引用对象尽量使用接口或者抽象类，而不是实现类；

第三，抽象层尽量保持稳定，一旦确定即不允许修改。

元数据（metadata）控制模块行为
元数据就是用来描述环境和数据的数据，通俗地说就是配置参数，参数可以从文件中获得，也可以从数据库中获得。

Spring容器就是一个典型的元数据控制模块行为的例子，其中达到极致的就是控制反转（Inversion of Control）

制定项目章程
在一个团队中，建立项目章程是非常重要的，因为章程中指定了所有人员都必须遵守的约定，对项目来说，约定优于配置。

封装变化
对变化的封装包含两层含义：

第一，将相同的变化封装到一个接口或者抽象类中；

第二，将不同的变化封装到不同的接口或抽象类中，不应该有两个不同的变化出现在同一个接口或抽象类中。
