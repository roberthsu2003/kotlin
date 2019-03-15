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

### argumentName.kt
> 使用引數名稱  
> 使用引數名稱後,後面的參數也一定要使用引數名稱  
> java 內建function無法使用

	fun main(){
	   someFunction(3,2)
	   someFunction(3,secondParameterName = 2)
	   someFunction(firstParameterName = 3,secondParameterName = 2)
	}
	
	fun someFunction(firstParameterName:Int, secondParameterName:Int){
	
	}

### defaultParameterValue.kt
> 預設參數值

	fun main(){
	   someFunction(3)
	   someFunction(parameterWithoutDefault = 3)
	   someFunction(parameterWithoutDefault = 3,parameterWithDefault = 10)
	}
	
	fun someFunction(parameterWithoutDefault:Int, parameterWithDefault:Int = 12){
	
	}

### vararg.kt
> 任何數量的引數

	fun main(){
	    val sum = sum(3,5,9,45,98,75)
	   println("總和是:${sum}")
	}
	
	fun sum(vararg numbers:Int):Int{
	    var total = 0
	    for (value in numbers){
	        total += value
	    }
	    return  total
	}

### SingleExpressionFunction.kt
> 單一運算式函式

	fun main(){
	   print("請輸入正方型的邊長:")
	    val x = readLine()!!.toInt()
	    println("正方型的面積是${square1(x)}")
	}
	
	fun square(x:Int):Int{
	    return  x * x
	}
	
	fun square1(x:Int):Int = x * x

### singleExpressionFunctionWithWhen.kt
> 單一運算式函式使用When

	fun main(){
	    print("請輸入學生成績:")
	    val sum = readLine()!!.toInt()
	    println("學生的等級是${scoreLevel(sum)}")
	}
	
	fun scoreLevel(score:Int) = when{
	    score >= 90 -> "優等"
	    score in 80..89 -> "甲等"
	    score in 70..79 -> "乙等"
	    score in 60..69 -> "丙等"
	    else -> "不及格"
	}

### TopLevelFunction
	//Test.kt
	package  com.exapple
	
	fun printOne(){
	    println(1)
	}
	
	fun printTwo(){
	    println(2)
	}
	
	fun printThree(){
	    println(3)
	}
	
	
	//Main.kt
	import com.example.*

	fun main(){
	    printOne()
	    printTwo()
	    printThree()
	}

### usingKotlinFunctionInJavaCode
	//Min.kt
	@file:JvmName("Math")
	@file:JvmMultifileClass
	
	package com.example.math
	fun min(n1:Int, n2:Int) = if (n1 < n2) n1 else n2
	
	
	
	//Max.kt
	@file:JvmName("Math")
	@file:JvmMultifileClass
	
	package  com.example.math
	
	fun max(n1:Int, n2:Int) = if (n1 > n2) n1 else n2
	
	
	
	//JavaMain.java
	import com.example.math.Math;

	public class JavaMain {
	    public static void main(String[] args){
	        System.out.println(Math.max(15, 10));
	        System.out.println(Math.min(15, 10));
	    }
	}