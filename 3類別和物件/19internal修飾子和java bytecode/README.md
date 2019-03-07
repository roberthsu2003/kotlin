# internal修飾子和java bytecode

	open class Person {
	            protected open fun speak() {}
	}
	        class Student() : Person() {
	            public override fun speak() {
	            }
	}
	val person = Person()
	//person.speak() // 1
	val student = Student()
	student.speak() // 2
	
###

	internal class Fruit private constructor() {
	           var weight: Double? = null
	           companion object {
	               fun create() = Fruit()
	           } 
	}


	var fruit: Fruit? = null // Accessible
	fruit = Fruit() // Error
	fruit = Fruit.create() // Accessible
	
###

	class Car {
	            init {
	                  count++;
	                  println("Car created")
	            }
	            
	            companion object {
	                init {
	                    println("Car companion object created")
	                }
	                var count: Int = 0
	                    private set
	            } 
	}

	
	    
	    