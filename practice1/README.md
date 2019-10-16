# ch01
### print
```
print() --> 不換行
println() --> 換行
```

```
fun main(){
	print("Hello!World")
}
```
	
```
當行註解 
//

多行註解
/*

*/
```

```
println("晚安!" + " 吃晚餐沒?");
字串的連結 --> +
```

```
println("晚安!\n吃晚餐沒?");
```

```
//自由格式敘述
1.單字中間不可插入空白
2.字串值不可中途換行
```


### ch2_readLine.kt
	fun main(){
	    print("請輸入姓名:")
	    val name = readLine()!!
	    print("歡迎" + name + "使用本軟體")
	}
	
### ch3_variable.kt
	fun main(){
	    var intA:Int
	    var a:Char
	    intA = 10
	    a = 'a'
	    println("intA=" + intA)
	    println("a=" + a)
	}
	
### ch4_score.kt
	fun main(){
	    println("姓名\t座號\t國文\t數學\t英文")
	    print("張山甲\t01\t89\t92\t76\n")
	    print("謝中正\t02\t89\t92\t76\n")
	    print("張英九\t03\t89\t92\t76\n")
	    print("王英菁\t04\t89\t92\t76\n")
	}

### ch5_型別自動轉換.kt
	onst val PI:Double = 3.14159
	
	fun main(){
	    val radius:Int = 10;
	    val area = PI * radius *radius;
	    print("圓面積=$area")
	}
	
	
### ch6_型別自動轉換使用=.kt
	package myKotlin
	
	const val PI:Double = 3.14159
	fun main(){
	    val radius:Int = 10;
	    //val area:Int = PI * radius *radius; //錯誤
	    val area:Int = (PI * radius * radius).toInt()
	    print("圓面積=$area")
	}
	
### ch7_計算成績.kt
	fun main(){
	    print("請輸入國文成績(0-100):")
	    val chinese = readLine()!!.toDouble()
	    print("請輸入英文成績(0-100):")
	    val english = readLine()!!.toDouble()
	    print("請輸入數學成績(0-100):")
	    val math = readLine()!!.toDouble()
	    val sum = chinese + english + math
	    val ave:Double = sum / 3
	    println("您的總分為${"%.2f".format(sum)},平均為${"%.2f".format(ave)}分")
	    println("您的總分為%.2f,平均為%.2f分".format(sum,ave))
	}
