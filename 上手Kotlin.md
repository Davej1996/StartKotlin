# 上手Kotlin

### 变量

val：value	不可变变量

var：variable	可变变量

### 函数

```kotlin```

```kotlin
fun methodName(param1: String,param2: String): Int {    
    return param1.toInt() + param2.toInt()
}
```

### 逻辑控制

##### if

```kotlin```

```kotlin
fun largerNumber(num1: Int, num2: Int): Int {    
    if (num1 > num2) {        
        return num1    
    } else {
        return num2    
    }
}
```

不同于Java的是，这里的if语句可以返回值

```kotlin
fun largerNumber(num1: Int, num2: Int): Int {
    return if (num1 > num2) {
        num1
    } else {
        num2
    }
}
```

简化一下

```kotlin
fun largerNumber(num1: Int, num2: Int): Int = if (num1 > num2) {
    num1
} else {
    num2
}
```

##### when

```kotlin
fun getScore(name: String) = when (name) {
    "a" -> 30
    "b" -> 40
    else -> 0
}
```

```kotlin
fun getScore(name: String) = when {
    name.startsWith("a") -> 30
    name == "b" -> 40
    else -> 0
}
```

##### 循环

```kotlin
fun loop() {
    for (i in 0 until 10 step 2) {
        println(i)
    }
}
```

```kotlin
fun loop() {
    for (i in 10 downT0 0 step 2) {
        println(i)
    }
}
```

