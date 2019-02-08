# 屬性和建構式參數

### 有val,var是類別實體屬性,沒有就是建構式參數
	class Fruit(var weight:Double, fresh:Boolean)
	val fruit = Fruit(12.0, true)
	println(fruit.weight)
	println(fruit.fresh) // error
	

