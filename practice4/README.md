# ch04
### arrayScan.kt(輸入陣列所有元素的值並顯示)
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