# ch03
### ch1_positive.kt
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