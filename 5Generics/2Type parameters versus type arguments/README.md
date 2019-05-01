# Type parameters versus type arguments
~~~
將討論generic type 和 generic function,為何要有泛型? 如何使用它? 如何定義泛型類別, 介面, 和涵式。
在執行階段如何處理泛型, 和泛型子類別的關係, 泛型和可null能力處理。
~~~

### 定義時,使用type parameter,它代建立時會被替換的資料型別
	class SimpleList<T>{
	    fun add(item:T){
	        //code
	    }
	
	    fun get(index:Int):T{
	        //code
	    }
	}
	

### 使用時,type argument使用真實的資料類型
	fun main(){
	
	    class Student(val name:String);
	    val studentList = SimpleList<Student>()
	
	}

### 實際展示generic
	fun main(){	
	    val fruits = listOf("Babana", "Orange", "Apple", "Blueberry")
	    val bFruits = fruits.filter { it.startsWith("B") }
	    print(bFruits)  //[Babana, Blueberry]
	
	}