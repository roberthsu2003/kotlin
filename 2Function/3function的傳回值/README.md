# 傳回值
> 所有function都有傳回值
  
	fun main() {
	   printSum(3, 5);
	}
	
	fun printSum(a: Int, b:Int):Unit{
	   val sum = a + b;
	   print(sum);
	}
	
### kotlin Unit相等於 Java的void, Unit是物件，可以被儲存
	fun main() {
	    val p = printSum(3, 5)
	    println(p is Unit)
	}
	
	fun printSum(a: Int, b:Int):Unit{
	    val sum = a + b
	    println(sum)
	}
	
### Unit可以被省略

	fun printSum(a: Int, b:Int):Unit{
	    val sum = a + b
	    println(sum)
	}
### 當傳出Unit時，可以使用return，不用帶任何值
	fun main() {
	    val p = printSum(3, 5)
	    
	}
	
	fun printSum(a: Int, b:Int){
	   if(a<0 || b<0){
	       return
	   }
	   
	   val sum = a + b;
	   print(sum)
	}
### 當傳出傳出值時，實作一定要明確傳出
	fun sumPositive(a:Int, b:Int):Int{
	    if(a > 0 && b > 0){
	        return a + b;
	    }
	    //error
	}
	
	fun sumPositive(a:Int, b:Int):Int{
    if(a > 0 && b > 0){
        return a + b;
    }
    
    return 0;
	}
	