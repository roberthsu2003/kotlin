# 自訂的getter和setter

### 簡易constructor
	class Fruit(var weight: Double,
	                    val fresh: Boolean,
	                    val ecoRating: Int)

### 建立自訂getter 和 setter要使用有body的建立法
	class Fruit(var weight: Double, val fresh: Boolean, ecoRating: Int)
	    {
	        var ecoRating: Int = ecoRating
	    }

### 建立有預設值的property
	class Fruit(var weight: Double, val fresh: Boolean) {
	            var ecoRating: Int = 3
	}
	
### 透過其它屬性計算出其它屬性值
	class Apple(var weight: Double, val fresh: Boolean) {
	            var ecoRating: Int = when(weight) {
	                in 0.5..2.0 -> 5
	                in 0.4..0.5 -> 4
	                in 0.3..0.4 -> 3
	                in 0.2..0.3 -> 2
	                else -> 1
	            }
	}
	
### 建立屬性getter和setter
	class Fruit(var weight: Double) {
	            var ecoRating: Int = 3
	            get() {
	                println("getter value retrieved")
	                return field
	            }
	            set(value) {
	                field = if (value < 0) 0 else value
	                println("setter new value assigned $field")
	            }
	}
	// Usage
	val fruit = Fruit(12.0)
	val ecoRating = fruit.ecoRating
	// Prints: getter value retrieved
	fruit.ecoRating = 3;
	// Prints: setter new value assigned 3
	fruit.ecoRating = -5;
	// Prints: setter new value assigned 0
	

### 建立read-only get
	class Fruit(var weight: Double) {
	          val heavy             // 1
	          get() = weight > 20
	      }
	//usage
	var fruit = Fruit(7.0)
	println(fruit.heavy) //prints: false
	fruit.weight = 30.5
	println(fruit.heavy) //prints: true


