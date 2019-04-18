# companion object instantiation類別的陪同物件實體化
~~~
companion object 是lazy,代表只有被第一次使用時，才會初初始化。所謂第一次使用的方法有，當companion object的成員初呼叫, 所以在class的init內，去呼叫companion的成員。所以在class初始化
~~~

###陪同物件init
	class Car {
	            init {
	                count++;
	                println("Car created")
	             }
	            companion object {
	                var count: Int = 0
	                init {
	                    println("Car companion object created")
	                } 
	            }
	}
	
	Car.count  // Prints: Car companion object created
	Car() // Prints: Car created
	
###先建立companion init再來才是類別的init

	Car()
	//Prints: Car companion object created
	//Prints: Car created
	Car()  //Prints: Car created
	Car.count