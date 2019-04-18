# enum class(例舉class)
### 一般的enum class定義
	enum class Color{
	    RED,
	    ORANGE,
	    BLUE,
	    GRAY,
	    VIOLET
	}
	
	fun main(){
	    val favouriteColor = Color.BLUE
	    val selectedColor = Color.valueOf("BLUE")
	    println(favouriteColor == Color.BLUE)
	
	    val selectedColor1 = enumValueOf<Color>("BLUE")
	    println(selectedColor1 == Color.BLUE)
	
	
	    for(color in Color.values()){
	        println("name:${color.name},ordinal:${color.ordinal}")
	    }
	}

### enum class可以有自訂的property,每個成員有對應的property value
	enum class Color(val r:Int, val g:Int, val b:Int){
	    RED(255,0,0),
	    ORANGE(255,165,0),
	    BLUE(0,0,255),
	    GRAY(49,79,79),
	    VIOLET(238,130,238)
	}
	
	fun main(){
	  val color = Color.BLUE
	  val rValue = color.r
	  val gValue = color.g
	  val bValue = color.b
	  println(rValue);
	  println(gValue);
	  println(bValue)
	}


