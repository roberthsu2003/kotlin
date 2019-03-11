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
