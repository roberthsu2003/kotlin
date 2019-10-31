# 運算式和運算子
## 運算式
kotlin中的敘述分為很多種型式，運算式是其中一種敘述。運算式是由運算子(operator)和運算元(operand)所組成; 運算元可以是變數或是數值，而運算子就是數學上的運算符號,如+,-,*,%等等。

```
val intA = num + 2
+ 和 = 就是運算子
intA 和 num就是運算元
```

 名稱 | 說明
 --- | ---  
運算子 | +,-,*,/
運算元 | 1+2的1和2
單元運算子 | -24的-
二元運算子 | 1+2的+
沒有三元運算子 | if (判斷式) 程式碼1 else 程式碼2


## 指定運算子
將右邊的值給左邊

```
//變數 = 值;
//intA = 10;

fun main(){
    val first = 20
    val second = 35
    var sum = 0
    println("計算前sum的值是$sum");
    sum = first + second
    println("計算後sum的值是$sum")
}
```

## 算數運算子
算數運算子(arithmetic operator)在數學上經常會使用到，下表列出它們的成員

算數運算子|意義|
-----|----|
+| 加 |
-| 減 |
*|乘|
/|除|
%|餘|
++|遞增|
--|遞減|


```
//讓使用者輸入被除數(整數)及除數(整數，不可以是零)，程式會顯示兩數相除的商及餘數。
	
fun main(){
   var n = 0
   var m = 0
   print("請輸入被除數(整數):")
   n = readLine()?.toIntOrNull() ?: 0
   print("請輸入除數(整數,不可以為0):")
   m = readLine()?.toIntOrNull() ?: 1

   println("商=${n/m} 餘數= ${n % m}")
}

```


> ### 課程小練習 plus_s.kt  
> ----
> 計算使用者輸入的2個任意數，程式會顯示2數相加的總和。
> 
> 顯示=======  
> 請輸入第一個數值:45.67  
> 請輸入第二個數值:67.47  
> 兩個數的和是xxx.xx  


```
fun main(){
    //前置遞增運算子
    var x = 1
    var y = ++x
    //x = x + 1
    //y = x
    println("x = $x, y = $y")


    //後置遞增運算子
    var m = 1
    var n = m++;
    //n = m
    //m = m + 1
    println("m = $m, n = $n")

}
```

## 比較運算子 
if敘述常常會使用到比較運算子，所以先簡單了解一下if敘述的用法。
 
 運算子 | 意義 
---|--- 
 == | 內容相等 
 != | 內容不相等 
 > | 大於 
 < | 小於 
 >= | 大於等於 
 <= | 小於等於 


```
if(條件判斷)
	敘述


fun main(){
    val x = 5
    if (x > 0)
        print("x的值大於零");
}
``` 





## 邏輯運算子 


! | not
---|---
&&  | and 
//(直的符號) | or 

```

fun main(){
    print("請輸入學生分數(0-100):");
    val num = readLine()?.toIntOrNull() ?: -1

    if(num < 0 || num > 100){
        println("學生分數輸入錯誤");
    }

    if(num < 60 && num >= 0){
        println("學生成績不及格");
    }

}
```

## 複合指定運算子
 運算子 | 意義 
---|--- 
+= | 加等於 
-= | 減等於 
*= | 乘等於 
/= | 除等於 

```
fun main(){
    //請使用者輸入一個任意數，程式會顯示此數的平方值及立方值
    val num:Double
    var result:Double
    print("請輸入任意的數值:")
    num = readLine()?.toDoubleOrNull() ?: 0.0
    result = num
    result *= num
    println("此數的平方是:$result")
    result *= num
    println("此數的立方是:$result")
}
```



> ### 課程小練習 complex_s.kt  
> ----
> 請以(複合指定運算子)設計程式,讓用者輸入三個任意數，程式會顯示3數相加的總和(Double) 
>  
> 顯示=======  
>
> 請輸入第一個數值:45.67  
> 請輸入第二個數值:67.47  
> 兩個數的和是xxx.xx  


## 括號運算子
先乘除後加減

```
fun main(){
    var sum = 0.0
    sum = 12 - 2 * 6 / 2.0 + 1
    println("sum的值是:$sum")

    sum = (12 - 2 * 6 ) / (2.0 + 1)
    print("sum的值是:$sum")

}
```

## 沒有三元運算式  

```
kotlin沒有三元運算式
語法:
if(條件判斷) 程式碼1 else 程式碼2 ;

```

```
fun main(){
    //kotlin沒有三元運算式，使用if運算式代替
    val in1:Double
    val in2:Double
    val in3:Double
    var max:Double

    print("請輸入第一個數:");
    in1 = readLine()?.toDoubleOrNull() ?: 0.0

    print("請輸入第二個數:");
    in2 = readLine()?.toDoubleOrNull() ?: 0.0

    max = if (in1 > in2) in1 else in2

    print("請輸入第二個數:");
    in3 = readLine()?.toDoubleOrNull() ?: 0.0

    max = if (max > in3) max else in3

    println("輸入三個數中最大的數為:$max")

}
```

 




> ### 課程小練習 ifelse_s.kt  
> ----
> 讓使用者輸入國文成績,程式會顯示該成績是否及格.
>  
> 顯示=======  
>
> 請輸入國文成績:80  
> 成績及格(成績不及格)  
 


### 數學算式轉換電腦運算
```
	// Name : ladder.kt
	//讓使用者輸入梯形的上底、下底及高，程式會計算梯形的面積(上底加下底乘以高除以2)
	
fun main(){
    val top:Int
    val bottom:Int
    val height:Int
    val area:Double

    println("請輸入梯形的上底(公分):")
    top = readLine()?.toIntOrNull() ?: 0

    println("請輸入梯形的下底(公分):")
    bottom = readLine()?.toIntOrNull() ?: 0

    println("請輸入梯形的高(公分):")
    height = readLine()?.toIntOrNull() ?: 0

    area = (top + bottom) * height / 2.0
    println("梯形的面積:$area 平方公分")
}

```

> ### 課程小練習  
> ----
> 讓使用者輸入圓柱體的半徑及高，程式會計算圓柱體的體積(圓柱體體積的公式為「圓週率乘以半徑平方再乘以高)。
>  
> 顯示=======  
>
> 請輸入圓柱體的半徑(公分):10  
> 請輸入圓柱體的高(公分):5  
> 圓柱體的體積:xxxx立方公分



