# sealed class
### sealed class有限定，所有的子類別必需在同一個kt檔案內
	//vehicle.kt
	sealed class Vehicle()
	class Car : Vehicle()
	class Truck : Vehicle()
	class Bus : Vehicle()
	
	    
### sealed的子類別可以在別的kt檔內繼承
	//vehicle.kt
	sealed class Vehicle()
	open class Bus : Vehicle()
	//data.kt
	class SchoolBus:Bus()

### 限制sealed的子類別可以在別的kt檔內繼承,sealed不需要有open和finale,sealed有abstract的所有功能
	//vehicle.kt
	sealed class Vehicle()
	sealed class Bus : Vehicle() //加上sealed,不需要open,也不需要abstract
	//data.kt
	class SchoolBus:Bus() //Error cannot access Bus

### sealed class和when
	when (vehicle) {
	            is Car -> println("Can transport 4 people")
	            is Truck -> println("Can transport furnitures ")
	            is Bus -> println("Can transport 50 people ")
	}
	
