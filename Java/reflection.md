# 反射

反射就是为了解决在运行时，对实例一无所知的情况下如何调用他的方法

### 基础

对于每个类型，JVM都会创建一个Class类型的实例，这个实例中包含了这个类型的全部信息，因此在运行时只要获取到这个实例就可以知道全部类型信息，这种通过Class实例获取类型信息的方法就是Reflection

有三种方式获取这个实例：
- 直接通过class的静态变量，例如`String.class`
- 通过实例的`getClass`方法
- 如果知道类的完整名称，可以直接通过Class的静态方法获取：`Class.forName('Java.lang.String')`
上述方法返回就是Class类型的实例，可以直接调用这个实例的`newInstance()`创建新该类型实例

### 访问字段

使用`getField(),getFields()`等接口来访问字段，得到`Field`类型实例，调用这个类型的方法可以访问到这个字段的名称，类型，修饰符，值等，还可以修改值，具体接口如下：
```java
Field f = String.class.getField('fieldName');
f.getName();
f.getType();

person p = new person();
fp = p.getClass().getField('name');
Object fVal = fp.get(p);
fp.set(p,'newName');
```
注意，其中查看和修改值都要传入实例对象，这可能说明一个类的多个实例的一个字段共享同一个Field对象

### 访问方法

使用和上述访问字段几乎同样的方式可以访问方法，注意因为有重载，所以在获取时要指定方法名称和参数类型，返回的对象为`Method`类型实例，通过该实例可以获取方法各种信息，以及可以使用`Method.invoke()`来调用该方法，