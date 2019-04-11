# Destructive declaration 拆解的宣告

### 拆解宣告
~~~
將物件的property拆解出來成為變數
~~~
	data class Person(val firstName: String, val lastName: String,val height: Int)
	val person = Person("Igor", "Wojda", 180)
	var (firstName, lastName, height) = person
	println(firstName) // prints: "Igor"
	println(lastName) // prints: "Wojda"
	println(height) // prints: 180
	        
### 上面拆解宣告的方式
	val person = Person("Igor", "Wojda", 180)
	var firstName = person.component1()
	var lastName = person.component2()
	var height = person.component3()
	

### 使用底線省略
	val person = Person("Igor", "Wojda", 180)
	var (firstName, _, height) = person
	println(firstName) // prints: "Igor"
	println(height) // prints: 180
	
### 拆解字串
	val file = "MainActivity.kt"
	val (name, extension) = file.split(".", limit = 2)
	
### 拆解和for一起使用
	val authors = listOf(
	           Person("Igor", "Wojda", 180),
	           Person("Marcin", "Moskała", 180)
	)
	println("Authors:")
	for ((name, surname) in authors) {
	     println("$name $surname")
	}
  