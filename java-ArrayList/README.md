

# java-ArrayList-analysis



#### 类标识

> RandomAccess 表示ArrayList能够进行快速随机访问

> Cloneable 表示ArrayList能够进行克隆

> Serializable 表示ArrayList能够进行序列化

```java
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable
```



#### 属性

> 默认容量为10

```java
  private static final int DEFAULT_CAPACITY = 10;
```

> 用户指定的空数组变量

```java
 private static final Object[] EMPTY_ELEMENTDATA = {};
```

> 返回的空数组变量

```java
private static final Object[] DEFAULTCAPACITY_EMPTY_ELEMENTDATA = {};
```

> 元素存放的数组

```java
transient Object[] elementData;
```

> arrayList数组的大小

```java
 private int size;
```

#### 构造方法

##### 指定元素个数

```java
    public ArrayList(int initialCapacity) {
        if (initialCapacity > 0) {
            this.elementData = new Object[initialCapacity];
        } else if (initialCapacity == 0) {
            this.elementData = EMPTY_ELEMENTDATA;
        } else {
            throw new IllegalArgumentException("Illegal Capacity: "+
                                               initialCapacity);
        }
    }
```

##### 空构造方法

> 返回空的object的数组

```java
    public ArrayList() {
        this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
    }
```

##### 指定Collection集合

> 将Collection转化成数组。

```java
    public ArrayList(Collection<? extends E> c) {
        elementData = c.toArray();
        if ((size = elementData.length) != 0) {
            // c.toArray might (incorrectly) not return Object[] (see 6260652)
            if (elementData.getClass() != Object[].class)
                elementData = Arrays.copyOf(elementData, size, Object[].class);
        } else {
            // replace with empty array.
            this.elementData = EMPTY_ELEMENTDATA;
        }
    }
```



