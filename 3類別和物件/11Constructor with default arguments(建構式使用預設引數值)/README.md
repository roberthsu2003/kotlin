# Constructor with default arguments(建構式使用預設引數值)

### 有val,var是類別實體屬性,沒有就是建構式參數
	class Fruit(var weight:Double, fresh:Boolean)
	val fruit = Fruit(12.0, true)
	println(fruit.weight)
	println(fruit.fresh) // error
	
### 有default value
	package lesson3_11
	
	class Fruit(var weight:Int=0, var fresh:Boolean=true, val color:String="green")
	
	fun main(){
	    val fruit = Fruit()
	    println(fruit.weight)
	    println(fruit.fresh)
	    println(fruit.color)
	
	    val fruit1 = Fruit(7, false)
	    println(fruit1.weight)
	    println(fruit1.fresh)
	    println(fruit1.color)
	
	    val fruit2 = Fruit(weight = 7, color = "Yellow", fresh = true)
	    println(fruit2.weight)
	    println(fruit2.fresh)
	    println(fruit2.color)
	}	

