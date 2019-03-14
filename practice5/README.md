# ch05 Function(函式)

> 2Function  


### function1.kt
> 建立sayHello Function 

	fun main(){
	    sayHello()
	}
	
	fun sayHello(){
	    println("歡迎光臨")
	}

### function2.kt
> 攝氏溫度轉華氏溫度

	fun main(){
	    println("攝氏10度轉華氏溫度=${temperature(10)}")
	    println("==================================")
	    print("請輸入攝氏溫度:")
	    val inputValue = readLine()!!.toInt()
	    val result = temperature(inputValue)
	    println("華氏溫度=%.2f".format(result))
	}
	
	fun temperature(value:Int):Double{
	   return 1.8 * value + 32
	}

### return.kt
> 返回值 **return**  
> 顯示數字

	fun main(){
	    print("請輸入數字 n:")
	    val n = readLine()!!.toInt()
	    showNum(n)
	}
	
	fun showNum(n:Int):Unit{
	    var i = 1
	   while (true){
	       if (i > n) return
	       print("$i ")
	       i++
	   }
	}
	

### callFunc.kt
> 呼叫Function

	fun main(){
	    print("請輸入姓名:");
	    val name = readLine()!!
	    println(greet(name))
	}
	
	fun greet(person:String):String{
	    val greeting = "您好," + person + "!"
	    return greeting
	}

### multiplePar.kt
> function使用**多個參數**

	fun main(){
	    print("請輸入姓名:");
	    val name = readLine()!!
	    println(greet(name, true))
	}
	fun greet(person:String, alreadyGreeted:Boolean):String{
	    if (alreadyGreeted) return  greetAgain(person)
	    else return  greet(person)
	}
	
	fun greet(person:String):String{
	    val greeting = "您好," + person + "!"
	    return greeting
	}
	
	fun greetAgain(person:String):String{
	    return "再一次您好" + person + "!"
	}

### minAndmax.kt 
> 一次傳出多個值

	fun main(){
	    print("請輸入數目")
	    val num = readLine()!!.toInt()
	    val nums = IntArray(num)
	    for (index in nums.indices){
	        println("請輸入第${index+0}個數字:")
	        nums[index] = readLine()!!.toInt()
	    }
	    val bounds = minMax(nums.toTypedArray())
	    println("最小值是${bounds.first},最大值是${bounds.second} ")
	}
	
	fun minMax(array:Array<Int>):Pair<Int,Int>{
	    var currentMin = array[0]
	    var currentMax = array[0]
	    for ((index,value) in array.withIndex()){
	        if (index == 0) continue
	        if (value < currentMin){
	            currentMin = value
	        }else if (value > currentMax){
	            currentMax = value
	        }
	    }
	
	    return Pair(currentMin,currentMax)
	
	}

### returnNullType.kt
> 傳出nullable

	fun main(){
	    print("請輸入數目")
	    val num = readLine()!!.toInt()
	    val nums = IntArray(num)
	    for (index in nums.indices){
	        println("請輸入第${index+0}個數字:")
	        nums[index] = readLine()!!.toInt()
	    }
	    val bounds = minMax(nums.toTypedArray())
	    if (bounds == null){
	        print("有錯誤")
	        return
	    }
	
	
	
	    println("最小值是${bounds.first},最大值是${bounds.second} ")
	
	}
	
	fun minMax(array:Array<Int>):Pair<Int,Int>?{
	    var currentMin = array[0]
	    var currentMax = array[0]
	    if (array.count() < 2) return null
	    for ((index,value) in array.withIndex()){
	        if (index == 0) continue
	        if (value < currentMin){
	            currentMin = value
	        }else if (value > currentMax){
	            currentMax = value
	        }
	    }
	
	    return Pair(currentMin,currentMax)
	
	}
