# 定義類型小名
	data class User(val name: String, val surname: String)
	typealias Users = List<User>

	typealias Weight = Double
	
	typealias Length = Int

###使用typealias
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
	
###
	typealias Dictionary<V> = Map<String, V>
	typealias Array2D<T> = Array<Array<T>>

###
	typealias Action<T> = (T) -> Unit
	typealias CustomHandler = (Int, String, Any) -> Unit
###
	typealias OnElementClicked = (position: Int, view: View, parent: View)->Unit




