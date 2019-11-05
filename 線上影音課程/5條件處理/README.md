## 5條件處理
### if敘述
有條件的執行程式區塊，使用最多的是if敘述，一般可以有:  

指令  |  表式法
---- | ----
單項選擇 | if()
雙項選擇 | if() ... else
多項選擇 | if() ... else if() ... else

#### 單項選擇
```
fun main(){
    //密碼輸入判斷
    //讓使用者輸入密碼，如果輸入的密碼是("abcd"), 會顯示「密碼正確，歡迎進入kotlin世界」, 如果密錯誤,不做任何動作
    print("請輸入密碼:")
    val pwd = readLine() ?: ""
    if (pwd == "abcd") {
        println("密碼正確，歡迎進入kotlin世界")
    }
    /*可以改寫為
    if (pwd == "abcd")
        println("密碼正確，歡迎進入kotlin世界")
    */
}
```

#### 雙向選擇
* 將if當作statement  

```	
fun main(){
    //將if當作statement
    val x = 5
    if(x > 10){
        println("greater")
    } else {
        println("smaller")
    }

}
```
```
fun main(){
    //會顯示錯誤的進階密碼判斷
    //密碼輸入判斷
    //讓使用者輸入密碼，如果輸入的密碼是("abcd"), 會顯示「密碼正確，歡迎進入kotlin世界」, 如果密錯誤,顯示「密碼錯誤」
    print("請輸入密碼:")
    val pwd = readLine() ?: ""
    if (pwd == "abcd") {
        println("密碼正確，歡迎進入kotlin世界")
    }else{
        println("密碼錯誤")
    }
    /*
    //單行可省略括號
    if (pwd == "abcd") {
        println("密碼正確，歡迎進入kotlin世界")
    }else{
        println("密碼錯誤")
    }
    */

}
```
* 將if當作expression  

```
fun main(){
    //學生成績判斷
    //大於等於60分,顯示及格,反之顯示不及格
    print("請輸入學生分數(0-100):");
    val score = readLine()?.toIntOrNull() ?: 0
    /*
    //將if當作敘述式
    if (score >= 60)
        println("同學,您的分數及格")
    else
        println("同學,您的分數不及格")
    */

    //將if當作運算式
    println("同學,您的分數${if (score >= 60) "及格" else "不及格"}")
}
```
#### 多項選擇
```
fun main(){
    //分數等級
    //分數90以上"A+",80以上"A",70以上"B",60以上"C",60以下"D"等
    print("請輸入學生分數:(0-100):")
    val score = readLine()?.toIntOrNull() ?: 0
    var grade:String
    //使用statement
    /*
    if (score >= 90)
        grade = "A+"
    else if (score >= 80 )
        grade = "A"
    else if (score >= 70 )
        grade = "B"
    else if (score >= 60)
        grade = "C"
    else
        grade = "D"

    println("您的分數等級是:$grade")
 */
    //使用expression
    println("您的分數等級是:${
    if (score >= 90)
        "A+"
    else if (score >= 80 )
        "A"
    else if (score >= 70 )
        "B"
    else if (score >= 60)
        "C"
    else
        "D"
    }")

}
```

```
fun main(){
    //購買商品價格計算
    //10000 -> 8折
    //5000 -> 85折
    //3000 -> 9折
    //1000 -> 95折
    print("請輸入客人實付金額:")
    val payMenoy = readLine()?.toIntOrNull() ?: 0
    print("購買商品總價:")
    var total:Int = readLine()?.toIntOrNull() ?: 0

    /*
    //對待當作statement
    var discount:Int
    if (total >= 10000)
        discount =  (total * 0.8).toInt()
    else if (total >= 5000)
        discount = (total * 0.85).toInt()
    else if (total >= 3000)
        discount = (total * 0.9).toInt()
    else if (total >= 1000)
        discount = (total * 0.95).toInt()
    else
        discount = 0
    print("找錢${payMenoy - discount}給客戶");
    */

    //對待當作expression
    val discount = if (total >= 10000)
        (total * 0.8).toInt()
    else if (total >= 5000)
        (total * 0.85).toInt()
    else if (total >= 3000)
        (total * 0.9).toInt()
    else if (total >= 1000)
        (total * 0.95).toInt()
    else
        0
    
    print("找錢${payMenoy - discount}給客戶");

}
```
	
#### java對待if當作statement,kotlin對待if當作expression,取代三元運算式
	println(if(x > 10) "greater" else "smaller")
	
#### 對待當statements
	val hour = 10
	val greeting: String
	if (hour < 18) {
	      greeting = "Good day"
	 } else {
	      greeting = "Good evening"
	 }
	 
#### 對待當作expression
	val greeting = if (hour < 18) "Good day" else "Good evening"

#### 會自動return最後一行
	val hour = 10
	val greeting = if (hour < 18) {
	     //some code
	      "Good day"
	 } else {
			//some code
	      "Good evening"
	 }
	 println(greeting) // Prints: "Good day"


#### 也可以應用在字串樣板內
	val age = 18
	val message = "You are ${ if (age < 18) "young" else "of age" } person"
	 println(message) // Prints: You are of age person

### when敘述