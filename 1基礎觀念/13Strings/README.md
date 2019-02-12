# Strings
### 使用索引運算子存取字元
~~~
和java String操控一樣，這些多的是被定義在extensions
~~~
	val str = "abcd" 
	println (str[1]) // Prints: b

	val str = "abcd" 
	println(str.reversed()) // Prints: dcba 
	
	println(str.takeLast(2)) // Prints: cd
	println("john@test.com".substringBefore("@")) // Prints: john
	println("john@test.com".startsWith("@")) // Prints: false
