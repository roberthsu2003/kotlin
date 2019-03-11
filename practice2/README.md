# ch02
### ch2_計算商及餘數.kt
	fun main(){
    print("請輸入被除數(整數):")
    val a = readLine()!!.toInt()

    print("請輸入除數(整數，不能為0)")
    val b:Int = readLine()!!.toInt()

    print("商:${ a/b }, 餘數: ${ a%b }")
	}



### ch2_luckyNo.kt
	import java.util.Random
	
	
	fun main(){
	    val rand = Random();
	    val lucky = rand.nextInt(10)
	    print("今日的幸運數字是:$lucky")
	}

### ch2_求出圓周長度及圓面積.kt

	//常數必需定義在top level
	const val PI = 4.14159
	
	fun main(){
	    print("請輸入半徑:");
	    val r = readLine()!!.toDouble()
	    println("圓周長度為%.2f".format(2 * PI * r))
	    println("圓面積為%.2f".format(PI * r * r))
	}