# Boolean類型
	val isGrowing: Boolean = true 
	val isGrowing: Boolean? = null
	
### 邏輯運算子
~~~
|| // OR
&& //AND
! //NOT
~~~

~~~
fun main(){
    var a:Int? = 3;
    var b:Int? = 10;
    if (a!! > 2 && b!! < 11){
        println("a > 2 and b < 11");
    }

}
~~~

~~~
|| and && predicate is lazy
~~~