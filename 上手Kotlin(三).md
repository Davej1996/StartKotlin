# 上手Kotlin(三)

### 集合的创建与遍历

创建不可变集合

```kotlin
val list = listOf(1, 2, 3, 4)
for (num in list) {
	println(num)
}
```

创建可变集合

```kotlin
val mutableList = mutableListOf(1, 2, 3)
mutableList.add(4)
for (num in mutableList) {
	println(num)
}
```

创建map

```kotlin
val map = mapOf("Apple" to 1, "Banana" to 2, "Orange" to 3)
for ((fruit, number) in map) {
	println("fruit is $fruit , number is $number")
}
```

### Lambda表达式

语法结构

```kotlin
{参数名1: 参数类型,参数名2：参数类型 -> 
	函数体
}
```

#### 函数式Api

找字符串长度最长的

```kotlin
val list = listOf("Apple", "Banana", "Orange", "Pear")
val maxLengthFruit = list.maxBy { it.length }
println("字符串长度最长的fruit是：$maxLengthFruit")
```

把字符串都转成大写

```kotlin
val list = listOf("Apple", "Banana", "Orange", "Pear")
val newList = list.map { it.toUpperCase() }
```

过滤集合中的数据

```kotlin
val list = listOf("Apple", "Banana", "Orange", "Pear")
val newList = list.filter { it.length > 5 }
```

集合中至少存在一个元素满足条件

```kotlin
val list = listOf("Apple", "Banana", "Orange", "Pear")
val result = list.any { it.length > 5 }
```

集合中是否所有元素满足指定条件

```kotlin
val list = listOf("Apple", "Banana", "Orange", "Pear")
val result = list.all { it.length > 5 }
```

#### 空指针检查

kotlin默认所有的参数和变量都不可为空

参数可空

```kotlin
fun test1(name: String?) {
    if (name != null) {
        name.toInt()
    }
}
```

用?.简化

```kotlin
fun test1(name: String?) {
    name?.toInt()
}
```

```kotlin
fun test2(a: String?, b: String) {
    val c = if (a != null) {
        a
    } else {
        b
    }
}
```

用?:简化

```kotlin
fun test2(a: String?, b: String) {
    val c = a ?: b
}
```

非空断言：断定变量一定不为空，告诉编译器别帮我检查它空不空了，我断定他不为空

```kotlin
val result = content!!.toUpperCase()
```

使用let标准函数优化空检查代码，把调用对象传进lambda表达式中

```kotlin
fun doStudy(study: Study) {
    study?.let { stu -> 
         stu.read()
         stu.write()
    }
}
```

#### 函数的参数默认值

```kotlin
fun printParams(num: Int, str: String = "hello") {
    println("num is $num，str is $str")
}
```

有了这种小技巧，写次构造函数基本没必要了，因为可以直接在主构造函数上设置默认值，反正次构造函数也要直接或间接地调用主构造函数