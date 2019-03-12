# ch03
### ch1_if.kt 
> 單向選擇 

		fun main(){
		    print("請輸入密碼:")
		    val pass = readLine()
		   if (pass == "1234") {
		       println("歡迎光臨")
		   }
		}
		
> 雙向選擇 

	fun main(){
	    print("請輸入密碼:")
	    val pass = readLine()
	    if (pass == "1234") {
	        println("歡迎光臨")
	    }else{
	        println("密碼錯誤!請重新輸入")
	    }
	}
	

> 多向選擇

	fun main(){
	    val money:Int;
	    print("請輸入購買金額:")
	    money = readLine()!!.toInt()
	    print("實付金額:")
	    if (money >= 100000){
	        println(money * 0.8)
	    }else if (money >= 50000){
	        println(money * 0.85)
	    }else if (money >= 30000){
	        println(money * 0.9)
	    }else if (money >= 10000){
	        println(money * 0.95)
	    }else{
	        println(money)
	    }
	}

### ch2_if.kt
	fun main(){
	
	    println("請輸入整數值:")
	    val n = readLine()!!.toInt()
	    if(n > 0){
	        println("該值為正值");
	    }
	
	}
	
	//-------------------------------
	fun main(){
	    println("請輸入整數值:")
	    val n = readLine()!!.toInt()
	    if(n > 0)
	        println("該值為正值")
	
	}
	
	//-------------------------------
	fun main(){
	    println("請輸入整數值:")
	    val n = readLine()!!.toInt()
	
	    val answer = if(n > 0) "該值為正值" else "零或負數"
	
	    println(answer)
	
	}
	
	//-------------------------------
	fun main(){
	    println("請輸入整數值:")
	    val n = readLine()!!.toInt()
	
	    println("該值${if (n > 0)  "該值為正值" else "零或負數"}")
	
	
	
	}
	
### ch3_when.kt(四則運算式)
	fun main(){
	
	    val a = 20
	    val b = 40
	    println("請輸入4則運算式符號(+,-,*,/)")
	    val op = readLine()!!.toString();
	    when (op){
	        "+" -> println("a + b = ${a + b}")
	        "-" -> println("a - b = ${a - b}")
	        "*" -> println("a * b = ${a * b}")
	        "/" -> println("a / b = ${a / b}")
	        else -> println("錯誤")
	    }
	
	}

### ch3_when.kt(分數範圍判斷)
	fun main(){
	
	
	    println("請輸入成績0~100")
	    val score = readLine()!!.toInt()
	    when {
	        score > 90 -> println("優等")
	        score in 80..89 -> println("甲等")
	        score in 70..79 -> ("乙等")
	        score in 60..69 -> ("丙等")
	        else -> println("不及格")
	    }
	
	}
	
### ch4_forJava.java

	public class JavaFor {
	    public static void main(String[] args){
	        String str = "Foo Bar";
	        for(int i=0; i< str.length(); i++){
	            System.out.println(str.charAt(i));
	        }
	    }
	
	}

### ch4_forIn.kt(計算總和)
	fun main(){
	    var sum = 0;
	    for (i in 2..10){
	        sum += i;
	        println("第${i-1}次迴圈的i=$i,總和為$sum")
	    }
	}
	
~~~
	fun main(){
	    var sum = 0;
	    for (i in 2..10 step 2){
	        sum += i;
	        println("第${i/2}次迴圈的i=$i,總和為$sum")
	    }
	}
~~~	

	fun main(){
	    var sum = 0;
	    for (i in 10 downTo 2 step 2){
	        sum += i;
	        println("i=$i,總和為$sum")
	    }
	}

### ch4_forIn1.kt(計算每星期家庭收支)
	fun main(){
	    var sum = 0;
	    for (i in 1..7){
	        if (i==7) print("請輸入星期日的支出:")
	        else print("請輸入星期${i}的支出")
	
	        val n = readLine()!!.toInt()
	        sum += n
	    }
	
	    println("本星期的支出為${sum}元")
	}

### ch4_forNest.kt(#字三角形)
	fun main(){
	    for (i in 1..5){
	        print("外部迴圈第${i}次迴圈,內部執行次${i}迴圈   ")
	        for (j in 1..i){
	            print("#")
	        }
	        println()
	    }
	}
	
### ch4_forNest1.kt(九九乘法表)
	fun main(){
	    for (i in 1..9){
	        for(j in 1..9)
	            print("${i}*${j}=${i*j}\t")
	        println()
	    }
	}
	
### ch5_while(存錢買機車)
	fun main(){
	    var deposit = 0
	    var count = 0
	    var n:Int? = null
	
	    while (deposit < 30000){
	        count++
	        print("請輸入第幾個月份的存款:")
	        n = readLine()!!.toInt()
	        deposit += n
	
	    }
	    println("您存了${count}個月的總存款為:${deposit}元")
	
	}
	
### ch6_doWhile(密碼驗證)
	fun main(){
	    var pw:String? = null
	    do {
	        print("請輸入密碼:")
	        pw = readLine()
	    }while(pw != "1234")
	
	    println("恭喜!密碼正確!")
	
	}

### ch7_break(存錢)
	fun main(){
	    var deposite = 0
	    var count = 0
	    while (true){
	        count++
	        print("請輸入第${count}個月份的存款:")
	        val n = readLine()!!.toInt()
	        deposite += n
	        if(deposite >= 30000) break;
	    }
	    println("恭喜!存了${count}個月的總存款為:${deposite}元");
	
	}

### ch8_continue(樓層命名)
	fun main(){
	    var floor = 0;
	    print("請輸入本大樓的樓層數:")
	    val n = readLine()!!.toInt()
	    println("本大樓具有的樓層數為:")
	    while (floor <= n){
	        floor++;
	        if (floor == 4) continue
	        print("$floor  ")
	    }
	}