# Generic constraints

~~~
限制type parameter的資料型別。一般沒指定就是以最上限Any?
SimpleList<T> == SimpleList<T:Any?>
~~~

	class SimpleList<T>
	class Student
	
	fun main(){
	
	  var intList = SimpleList<Int>()
	  var studentList = SimpleList<Student>()
	  var carList = SimpleList<Boolean>()
	
	}
	
### 限定只有Number型別

	class SimpleList<T:Number>
	
	
	fun main(){
	
	  var intList = SimpleList<Int>()
	  var numberList = SimpleList<Number>()
	  var doubleList = SimpleList<Double>()
	  var stringList = SimpleList<String>() //錯誤  
	
	}