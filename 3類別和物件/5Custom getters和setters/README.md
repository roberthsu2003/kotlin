# 自訂的getter和setter

### 簡易constructor
	class Fruit(var weight: Double,
	             val fresh: Boolean,
	             val ecoRating: Int)

### 建立自訂getter 和 setter要使用在class body內建立
	class Fruit(var weight: Double, val fresh: Boolean, ecoRating: Int)
	    {
	        //propert被建立在class body內，必需要有一個初始化的值
	        var ecoRating: Int = ecoRating
	    }

### 建立有預設值的property
	class Fruit(var weight: Double, val fresh: Boolean) {
	           //propert被建立在class body內，必需要有一個初始化的值，也可以使用一個default value
	            var ecoRating: Int = 3
	}

### property在class body被建立時可以type(使用推測)
	class Fruit(var weight: Double, val fresh: Boolean) {
	           //Int被省略
	            var ecoRating = 3
	}

	
### 透過其它屬性計算出其它屬性值
	class Apple(var weight: Double, val fresh: Boolean) {
	            //透過其它屬性計算出其它屬性值
	            //不同的重量建立不同的ecoRating值
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
	                return field //使用field 代表自已這個property
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
### heavy沒有真的值儲存，只是單獨計算
	class Fruit(var weight: Double) {
	          val heavy             // 1
	          get() = weight > 20
	      }
	//usage
	var fruit = Fruit(7.0)
	println(fruit.heavy) //prints: false
	fruit.weight = 30.5
	println(fruit.heavy) //prints: true
	
### heavy沒有真的值儲存，只是單獨計算(也可以這樣寫)
	class Fruit(var weight: Double) {
	    val heavy = weight > 20;
	}
	//usage
	var fruit = Fruit(7.0)
	println(fruit.heavy) //prints: false
	fruit.weight = 30.5
	println(fruit.heavy) //prints: true

### 計算屬性
	class Car {
		var usable: Boolean = true 
		var inGoodState: Boolean = true
		//crashed property沒有field,囚為是計算所得的
		var crashed: Boolean 		
		get() = !usable && !inGoodState 	
		set(value) { 
			usable = false 
			inGoodState = false 
		}
	}


