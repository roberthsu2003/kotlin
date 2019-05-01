# 定義類型小名
	data class User(val name: String, val surname: String)
	typealias Users = List<User>

	typealias Weight = Double
	
	typealias Length = Int

### 使用type alias
	val users: Users = listOf(
	    User("Marcin", "Moskala"),
	    User("Igor", "Wojda")
	 )
	 fun calculatePrice(length: Length) {
	       // ...
	  }
	  calculatePrice(10)
	  val weight: Weight = 52.0
	  val length: Length = 34
###
	typealias Length = Int
	var intLength: Int = 17
	val length: Length = intLength
	intLength = length
	
### type aliase 使用在generic type
	typealias Dictionary<V> = Map<String, V>
	typealias Array2D<T> = Array<Array<T>>

### type aliase 經常使用在為function type 命名
	typealias Action<T> = (T) -> Unit
	typealias CustomHandler = (Int, String, Any) -> Unit
	
### 也可使用在function type parameter names
	typealias OnElementClicked = (position: Int, view: View, parent: View)->Unit




