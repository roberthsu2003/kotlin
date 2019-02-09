# sealed class

	//vehicle.kt
	        sealed class Vehicle()
	        class Car : Vehicle()
	        class Truck : Vehicle()
	        class Bus : Vehicle()
	
	    
###
	//vehicle.kt
	sealed class Vehicle()
	open class Bus : Vehicle()
	//data.kt
	class SchoolBus:Bus()
	
###
	//vehicle.kt
	sealed class Vehicle()
	sealed class Bus : Vehicle()
	//data.kt
	class SchoolBus:Bus() //Error cannot access Bus
	
###sealed class和when
	when (vehicle) {
	            is Car -> println("Can transport 4 people")
	            is Truck -> println("Can transport furnitures ")
	            is Bus -> println("Can transport 50 people ")
	}
	
