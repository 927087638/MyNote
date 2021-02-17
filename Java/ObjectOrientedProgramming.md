# Object Oriented Programming

OOP的特征：封装、继承、多态

类之间的关系：依赖、聚合、继承



## 类

- private public

- this

- 构造方法：一旦给出构造方法，系统则不再提供无参构造方法

  <p align="right"> 建议，自己给出一个无参构造</p>

## 继承

  ```java
public Zi extends Fu
{
    
}
  ```

java中，只可以继承一个类

可以多层继承

### 变量访问

先子后父

父类的私有内容，子类继承不到

`this`表示本类中，`super`表示父类中的

### 构造函数

子类会默认地调用一个父类的`无参构造`，即`super()`
也可以用`super(---)`来调用父类的其他构造函数

### 函数重写

防止函数名拼写错误

```java
@Override
```

