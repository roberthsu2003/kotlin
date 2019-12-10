# data class
- 使用data class會讓kotlin的compiler自動幫class產一些methods(equals,hasCode,toString,copy,componentN)
- data class不可以是inner,abstract,sealed class

```kotlin
data class Product(var name:String, var price:Double)


fun main(){
	val productA = Product("spoon",30.2)
	val productB = Product("spoon",30.2)
	val productC = Product("Fork",17.4)

	println(productA == productA)  // prints: true
	println(productA == productB)  // prints: true
	println(productA == productC)  // prints: false
	println(productA) //Product(name=Spoon, price=30.2)
	println(productC) // Product(name="Fork",price=17.4)		
}
```

- copy

```kotlin
data class Product(var name:String, var price:Double)


fun main(){
	val productA = Product("spoon",30.2)
	val productB = Product("spoon",30.2)
	val productC = Product("Fork",17.4)

	val productA = Product("Spoon", 30.2) 
	print(productA) // prints: Product(name=Spoon, price=30.2)
	
	val productB = productA.copy() 
	print(productB) // prints: Product(name=Spoon, price=30.2)
	
	val productB = Product(productA)			
}
```

- Mutable object - modify object state

```kotlin
data class Product(var name:String, var price:Double)
var productA = Product("Spoon", 30.2) 
productA.name = "Knife"
```
- Immutable object
```kotlin
Product(val name:String, val price:Double)
var productA = Product("Spoon", 30.2) 
productA = productA.copy(name = "Knife")
```

# Destructive declaration 拆解的宣告

## data class 的拆解宣告
- 將物件的property拆解出來成為變數

```kotlin
data class Person(val firstName: String, val lastName: String,val height: Int)
val person = Person("Igor", "Wojda", 180)
var (firstName, lastName, height) = person
println(firstName) // prints: "Igor"
println(lastName) // prints: "Wojda"
println(height) // prints: 180
```

### 使用componentN()拆解

```kotlin
val person = Person("Igor", "Wojda", 180)
var firstName = person.component1()
var lastName = person.component2()
var height = person.component3()
```
	

### 使用底線省略
	
```kotlin
val person = Person("Igor", "Wojda", 180)
var (firstName, _, height) = person
println(firstName) // prints: "Igor"
println(height) // prints: 180
```
	
### 拆解字串
```kotlin
val file = "MainActivity.kt"
val (name, extension) = file.split(".", limit = 2)
```
	
### 拆解和for一起使用
```kotlin
val authors = listOf(
	       Person("Igor", "Wojda", 180),
	       Person("Marcin", "Moskała", 180)
)
println("Authors:")
for ((name, surname) in authors) {
	 println("$name $surname")
}
```

