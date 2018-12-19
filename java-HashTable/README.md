# java-HashTable-analysis





#### HashTable 与 HashMap的区别

##### 线程安全性

- HashMap是线程非安全的
- HashTable是线程安全的

##### 键值的区别

- HashMap KEY 与 VALUE都可以是NULL
- HashTable   KEY 与 VALUE不可为空



##### 迭代的区别

- HashMap的迭代器(Iterator)是fail-fast迭代器，当有其它线程改变了HashMap的结构（增加或者移除元素），将会抛出ConcurrentModificationException





> HashTable源码中并没有显示的判断key不可以为空，而是在获取key的hashCode直接抛出空指针异常

```java
public synchronized V put(K key, V value) {
        
        if (value == null) {
            throw new NullPointerException();
        }
        Entry<?,?> tab[] = table;
        int hash = key.hashCode();
  		...
        return null;
    }
```



> HashTable 中大量使用了synchronized