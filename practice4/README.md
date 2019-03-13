# ch04 Array

> 基礎觀念-> array  
> 基礎觀念-> Range

### arrayScan.kt
> 輸入陣列所有元素的值並顯示  

	import  java.util.Scanner
	
	fun main(){
	    val stdIn = Scanner(System.`in`)
	    System.out.print("元素數:")
	    val n = stdIn.nextInt()
	    val a = arrayOfNulls<Int>(n)
	    for (i in a.indices){
	        System.out.print("a[${i}]=")
	        a[i] = stdIn.nextInt()
	    }
	    System.out.println("陣列內的數值為:")
	    for ((index, value) in a.withIndex())
	        System.out.println("a[${index}]=$value")
	}


### simpleArray.kt
	fun main(){
	    val array = intArrayOf(5, 6, 7);
	    for (item in 0..(array.count()-1)) println("array內的項目是:${array[item]}")
	}
~~~
fun main(){
    val array = intArrayOf(5, 6, 7)
    for (item in array) println("array內的項目是:${item}")
}
~~~

### arrayRand.kt
> 指定亂數給陣列的所有元素，並且以橫向長條圖顯示

	import  java.util.Random
	
	fun main(){
	    val rand = Random()
	    println("元素數:")
	    val n = readLine()!!.toInt()
	    val array = IntArray(n)
	    for (i in array.indices)
	        array[i] = rand.nextInt(9) + 1
	
	    for ((index,value) in array.withIndex()){
	        print("array[$index] = ")
	        for (i in 1..value) print("*")
	        println()
	    }
	}

### highScore.kt
> 輸入分數並顯示最高分  

	fun main(){
	    print("請輸入人數:");
	    val studentsCount = readLine()!!.toInt()
	    val studentScores = IntArray(studentsCount){
	        print("請輸入第${it+1}個學生的分數:")
	        readLine()!!.toInt()
	    }
	
	    for (score in studentScores){
	        print("${score}, ")
	    }
	    println()
	
	    var max = 0
	    for (score in studentScores){
	        if (score > max) max = score
	    }
	
	    println("學生們最高的分數為${max}")
	
	}


### lotterys.kt
> 輸入樂透分數，查詢中了幾顆星

	fun main(){
	    val lotterys = intArrayOf(15, 11, 21, 27, 28, 33)
	    val nums = IntArray(6){
	        print("請輸入6個號碼的第${it+1}號碼(0-38):")
	        readLine()!!.toInt()
	    }
	    var matchNum = 0
	    for (num in nums){
	        if (num in lotterys) matchNum++
	    }
	
	    println("您中了${matchNum}顆星")
	
	}
	
