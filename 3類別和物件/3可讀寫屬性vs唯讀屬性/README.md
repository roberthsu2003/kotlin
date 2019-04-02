# 可讀寫屬性vs唯讀屬性
### 使用var 和 val
	fun main() {
	    class Person(
	            var name: String,
	            // Read-write property (generated getter and setter)
	            val age: Int      // Read-only property (generated getter)
	        )
	        //usage
	        val person = Person("Eva", 25)
	        val name = person.name
	        person.name = "Kate"
	        val age = person.age
	        person.age = 28 //error: read-only property
	}

### 
	class Car (var speed: Double)
	
	val car: Car = Car(7.4) 
	car.speed = 9.2
	val speed = car.speed
	
	val car = Car(7.0)
	println(car.speed) //prints 7.0 
	//後運算先傳出值
	car.speed++ 
	println(car.speed) //prints 8.0 
	car.speed--
	car.speed--
	println(car.speed) //prints: 6.0
