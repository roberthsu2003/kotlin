# 迴圈
## for in 迴圈 整合 Ranges
### 使用Ranges

```kotlin
fun main(){
    //計算1到10的總合
    var sum = 0;
    for (i in 1..10) {
        sum += i
        println("sum + $i = $sum")
    }
}
```

### 使用Ranges 和 step

```kotlin
fun main(){
    //計算1到9的奇數總合
    var sum = 0;
    for (i in 1..9 step 2) {
        sum += i
        println("sum + $i = $sum")
    }
}
```

### 使用Ranges 和 downTo

```kotlin
fun main(){
    //請使用者輸入一個數值,然後請輸出倒數至0的值
    print("請輸入一個正整數值:")
    val num = readLine()?.toIntOrNull() ?: 0
    for (i in num downTo 0)
        println(i)
}
```

### 使用Range的downTo 和 step

```kotlin
fun main(){
    //請輸出身高200,198,196...150公分的標準體重
    //(身高-100) * 0.9
    for (height in 200 downTo 150 step 2)
        println("身高:$height ->標準體重:${(height-100) * 0.9}");
}
```


### for 和 if 整合  

```kotlin
fun main(){
    //請輸入一個整數值,顯示所有此值的約數
    print("請使用者輸入一個整數值:")
    val value = readLine()?.toIntOrNull() ?: 0
    for (i in value downTo 1){
        if(value % i == 0) print("$i  ")
    }
}
```

### 巢狀迴圈

```kotlin
package lesson6

fun main(){
    //請輸出九九乘法表
    for (first in 1..9){
        for (second in 1..9)
            print("$first * $second = ${first * second}\t")
        println()
    }
}
```

### 使用repeat function

```kotlin
fun main(){
    //輸出2的次方數
    var sum = 1
    print("請輸入2的次方數:")
    val n = readLine()?.toIntOrNull() ?: 0
    repeat(n){
        sum *= 2
    }
    print("2的${n}次方是$sum")
}
```


## for in 迴圈 整合 Array
### forIn和陣列
```kotlin
package lesson6

fun main(){
    //請輸入學生5科的成績,計算總合和平均
    val scores = Array(5){0}
    var sum = 0
    for(i in scores.indices){
        print("請輸入學生第${i}科的分數:")
        scores[i] = readLine()?.toIntOrNull() ?: 0
    }

    for(score in scores){
        sum += score
    }

    println("學生總分為$sum,平均為${sum/5.0}")


}

```
### forIn和陣列的indices,withIndex()

```kotlin
package lesson6

fun main(){
    //請輸入一星期每天的支出，並顯示每天的支出和總支出
    var sum = 0
    val week =  Array(7){0}
    for (i in week.indices){
      week[i] = when (i+1){
           7 -> {
               print("星期日支出:")
               readLine()?.toIntOrNull() ?: 0
           }
          else -> {
              print("星期${i+1}支出:")
              readLine()?.toIntOrNull() ?: 0
          }
       }
    }

    for((index,value) in week.withIndex()){
        when(index+1){
            7 -> println("星期日支出是$value")
            else -> println("星期${index+1}的支出是$value")
        }
        sum += value
    }

    println("一星期的總支出是:$sum")
}
```

### while迴圈
```kotlin
fun main(){
    //每月存錢買價值50000元的機車,存夠錢後顯示通知
    var deposit = 0
    var i = 0
    while(deposit<50000){
        i++
        print("第${i}個月的存款是:");
        deposit += readLine()?.toIntOrNull() ?: 0
    }
    println("總存款為${deposit},足夠購買機車了")
}
```

### do-while迴圈

```kotlin
fun main(){
    //請設計一個輸入每位學生的成績，當輸入完成後，輸入任一個英文字，結束程式，計算總分
    var sum = 0
    do {
        print("請輸入學生分數:")
        var score = readLine()?.toIntOrNull()
        sum += score ?: 0;
    } while (score != null)

    print("學生總成績是$sum")

}
```

### break

```kotlin
fun main(){

    //請設計一個輸入每位學生的成績，當輸入完成後，輸入任一個英文字，結束程式，計算總分
    var sum = 0
    do {
        print("請輸入學生分數:")
        var score = readLine()?.toIntOrNull() ?: break
        sum += score
    } while (true)

    print("學生總成績是$sum")


}
```


### continue

```kotlin
fun main(){
    //只要加總奇數
    var deposit = 0
    val lists = mutableListOf<Int>()
    while(true){
        print("請輸入奇數加總:")
        val value = readLine()?.toIntOrNull() ?: break
        if(value % 2 == 0)
           continue
        lists.add(value)
        deposit += value;
    }
    println("奇數有${lists},加總為${deposit}")
}
```