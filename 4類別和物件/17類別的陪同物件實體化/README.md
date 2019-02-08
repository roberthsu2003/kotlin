# 類別的陪同物件實體化

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