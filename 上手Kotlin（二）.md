# 上手Kotlin（二）

### 类与对象

##### 继承

与Java不同，不是所有的类都可以被继承，给了open关键字的类才可以被子类继承

```kotlin
open class Person {
    
}

class Student : Person() {
    
}
```

##### 构造函数

分主构造函数和次构造函数

主构造函数

```kotlin
class Coder(val name: String) {
    
    init {
        //主构造函数的逻辑写在这儿
        println(name)
    }
}
```

Kotlin规定，当一个类既有主构造函数，又有次构造函数的时候，所有的次构造函数都必须直接或间接地调用主构造函数

```kotlin
class Student(val sno: String, val grade: Int, name: String, age: Int) {
    constructor(name: String, age: Int) : this("", 0, name, age)
    constructor() : this("", 0)
}
```

Kotlin是允许只有次构造函数，却没有主构造函数的

```kotlin
class GoodStudent : Student {
    constructor(name: String) : super(name, 18) {

    }
}
```

#### 接口

```kotlin
interface Study {
    fun read()
    fun write()
}
```

接口允许默认实现

```kotlin
interface Study {
    fun read()
    fun write() {
        println("在写字")
    }
}
```

#### 数据类

```kotlin
data class Coffee(val milk: String, val water: String)
```

没错，就这么一行，不用像Java那样写Get，Set，toString方法了

#### 单例类

```kotlin
object Singleton {
    fun test() {
        
    }
}

//调用
fun main() {
    Singleton.test()
}
```

虽然看起来有点像Java的静态类