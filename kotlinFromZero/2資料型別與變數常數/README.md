# 資料型別與變數常數
## 2種變數宣告和字串樣版
### var 宣告變數(可以改變內容)
```
fun main(args: Array<String>) {
	       var fruit:String =  "橘子" 
	       fruit  = "香蕉" 
}
```

### val 宣告變數(不可以改變內容)
```
fun main(args: Array<String>) {
        val fruit:String= "橘子"
        a = "香蕉" //錯誤
}
```

### Strings樣板

java字串使用+運算子

``` 
//Java
String name = "Eva";
int age = 27;
String message = "My name is" + name + "and I am" + age + "years old";
```
kotlin string template, 使用$ 
 
```
val name = "Eva"
val age = 27
val message = "My name is $name and I am $age years old"
println(message)
//Prints: My name is Eva  and I am 27 years old
```

kotlin string template, 使用${}  

```
val name = "Eva"
val message = "My name has ${name.length} characters"
println(message) //Prints: My name has 3 characters
```

```
範例1:從鍵盤輸入字串
fun main() {
    print("請問大名是:");
    val name = readLine()!!
    print("您好! $name 先生");
}
```

```
範例2:從鍵盤輸入整數
import java.util.Scanner;
fun main() {
    val stdIn = Scanner(System.`in`)
    println("將x與y進行加減乘除運算")

    print("x的值:")
    val x = stdIn.nextInt()

    print("y的值:")
    val y = stdIn.nextInt()

    println("x + y: ${x + y}.");
    println("x - y: ${x - y}.");
    println("x * y: ${x * y}.");
    println("x / y: ${x / y}.");
}
```
------
------
## kotlin的類型推測  
### 建立要求是字串的變數
```
var title: String
```
### 同時宣告變數名稱和資料類型並將內容傳給變數(明確宣告變數類型)
	var title: String = "Kotlin"

### 宣告變數名稱和將內容傳給變數，資料類型請編譯器自行推測(不明確宣告)
	var title = "Kotlin"

### kotlin 是 strongly type language
	var title = "Kotlin"
	title = 12 // 1, Error


### 使用Any類型，代表可以使用任何形別

	var title: Any = "Kotlin"
	title = 12
	
### 明確宣告
	var age: Int = 18

### 值表達式無沒推測為正確類型時，可以使用明確宣告
	var age: Short = 18

### 使用指定型別的值表達式
	var age: Long = 18 // 明確宣告變數
	var age = 18L //指定Long的值表達式
	
### 錯誤的語法(無法推測)
	val title // 錯誤
	
```
範例
1製作指定值給三個int型態的變數，然後計算其總和與平均值(使用明確宣告)
2製作指定值給三個int型態的變數，然後計算其總和與平均值(使用不明確宣告)
```

-----------------------
-----------------------

## kotlin的基本資料型別
### kotlin的基本數值型別
類型 | 位元 | 範圍 
----|-----|-----
Byte| 8 bits| -128 to 127
Short| 16 bits | -32768 to 32767
Int | 32 bits | -2147483648 to -2147483647
Long | 64 bits | -huge to (huge-1)

### 進位值
```
2進位
x = 0b10

8進位
不支援

16進位
y = 0xab

```

### kotlin的浮點資料型別
Float | Double
------|-------
32 bits | 64 bits
~7位     | ~16位

```
var d = 123.5
```

### kotlin的布林值
```
var isBraking = true
var isTrained = false
```

### kotlin的字串和字元
```
var letter = 'D'
var name = "Fido"
```

### 明確宣告變數的資料型別
```
var smallNum:Short
var tinyNum:Byte
var title: String
```

### 同時明確宣告和指定值
```
var z:Short = 6
var title: String = "Kotlin"
var age: Int = 18
```

### 宣告變數名稱和將內容傳給變數，資料類型請編譯器自行推測(不明確宣告)

```
var title = "Kotlin"

```

### 使用指定型別的值表達式

```
var age: Long = 18 // 明確宣告變數
var age = 18L //指定Long的值表達式
```
### kotlin 是 strongly type language
```
var title: Any = "Kotlin"
title = 12
```

### 錯誤的語法(無法推測)
```
val title // 錯誤
```

### kotlin和java有一點不一樣，小的資料類型不能隱式轉換為大的資料類型

```
var weight : Int = 12
var truckWeight: Long = weight // 錯誤

var x = 5;
var y = x;
var z:Long = x //錯誤
```

### 需要明確轉換為相同資料類型
```
var weight:I nt = 12
var truckWeight: Long = weight.toLong()
```

### 數值可以轉換的方法
```
> toByte():Byte
> toShort():Short
> toInt():Int
> toLong():Long
> toFloat():Float
> toDouble():Double
> toChar():Char
```

### kotlin浮點數值表示法
```
> 27.5 //Double
> 27.5F //Float
```

### 浮點數值轉換為整數值，小數點會被去除
```
var x = 123.456
var y:Int = x.toInt()
```

### 小測驗
```
var x: Int = 65.2  //錯誤
var isPunk = true
var message = 'Hello' //錯誤
var y = 7
var z: Int = 7
var z: Int = y
y = y + 50
var s:Short
var bigNum:Long = y.toLong()
var b:Byte = 2
var smallNum = b.toShort()
b = smallNum //錯誤
isPunk = "false" //錯誤
var k = y.toDouble()
b = k.toByte()
s = 0b10001
```