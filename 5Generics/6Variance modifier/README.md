# Variance modifier
~~~
泛型預設是in-variance
~~~
	public class Box<T>
	fun sum(list:Box<Number>){
	    //code
	}
	
	fun main(){
	    sum(Box<Any>()) //錯誤
	    sum(Box<Number>()) //正確
	    sum(Box<Int>) //錯誤
	}


