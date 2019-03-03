# 建構式和預設引數

### 有val,var是類別實體屬性,沒有就是建構式參數
	class Fruit(var weight:Double, fresh:Boolean)
	val fruit = Fruit(12.0, true)
	println(fruit.weight)
	println(fruit.fresh) // error
	
### 有default value
	class Fruit(var weight:Int=0, var fresh:Boolean=true, val color:String="green");
	
	fun main() {
	    val fruit = Fruit();
	    println(fruit.weight);
	    println(fruit.fresh);
	    println(fruit.color);
	}
		

