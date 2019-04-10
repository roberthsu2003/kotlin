# property對constructor parameter

### 有val,var是類別實體屬性,沒有就是建構式參數
	class Fruit(var weight:Double, fresh:Boolean)

	fun main(){
	    val fruit = Fruit(12.0, true)
	    println(fruit.weight)
	    // fresh是constructor parameter
	    //println(fruit.fresh)
	}
	

Class declaration  | Getter generated | Setter generated | Type
------------- | ------------- | --------- | ------
class Fruit(name:String) | NO | NO | Constructor parameter
class Fruit (val name:String)  | YES | NO | Property
class Fruit (var name:String) | YES | YES | Property