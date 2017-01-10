# - 设计模式 六大原则

设计模式之六大原则——开闭原则（OCP）
开闭原则（Open Closed Principle）是Java世界里最基础的设计原则，它指导我们如何建立一个稳定的、灵活的系统。

 

定义：

一个软件实体如类、模块和函数应该对扩展开放，对修改关闭。

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

第一，将相同的变化封装到一个接口或者抽象类中；

第二，将不同的变化封装到不同的接口或抽象类中，不应该有两个不同的变化出现在同一个接口或抽象类中。


-----------------------------------------------------------------------------------------------------------
设计模式之六大原则——迪米特法则（LoD，LKP）
定义：

迪米特法则（Law of Demeter，LoD）也称为最少知识原则（Least Knowledge Principle，LKP）。

一个对象应该对其他对象有最少的了解。通俗地讲，一个类应该对自己需要耦合或调用的类知道得最少，你（被耦合或调用的类）的内部是如何复杂都和我没关系，那是你的事情，我就知道你提供的public方法，我就调用这么多，其他的一概不关心。

下面的代码在方法体内部依赖了其他类，这严重违反迪米特法则

1
2
3
4
5
6
7
8
9
10
11
12
13
public class Teacher {
 
    public void commond(GroupLeader groupLeader) {
        List<Girl> listGirls = new ArrayList<Girl>();
 
        for (int i = 0; i < 20; i++) {
            listGirls.add(new Girl());
        }
 
        groupLeader.countGirls(listGirls);
    }
 
}
 

方法是类的一个行为，类竟然不知道自己的行为与其他类产生了依赖关系，这是不允许的。

正确的做法是：

1
2
3
4
5
6
7
public class Teacher {
 
    public void commond(GroupLeader groupLeader) {
        groupLeader.countGirls();
    }
 
}

public class GroupLeader {
 
    private List<Girl> listGirls;
 
    public GroupLeader(List<Girl> _listGirls) {
        this.listGirls = _listGirls;
    }
 
    public void countGirls() {
        System.out.println("女生数量是：" + listGirls.size());
    }
 
}

-----------------------------------------------------------------------------------------------------------

设计模式之六大原则——依赖倒置原则（DIP）
依赖倒置原则（Dependence Inversion Principle，DIP）的原始定义：

高层模块不应该依赖底层模块，两者都应该依赖其抽象；
抽象不应该依赖细节；
细节应该依赖抽象。
 

依赖倒置原则在Java语言中的表现是：

模块间的依赖通过抽象发生，实现类之间不发生直接的依赖关系，其依赖关系是通过接口或者抽象类产生的；
接口或抽象类不依赖于实现类；
实现类依赖接口或抽象类。

-----------------------------------------------------------------------------------------------------------
