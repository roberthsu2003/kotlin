## 字串型別
#### 一般定義
	val c = 'x' // Char
	val message = "Hello" // String
	val m = message[0] // Char

####  kotlin string template, 使用$
	val name = "Eva"
	val age = 27
	val message = "My name is $name and I am $age years old"
	println(message)
	//Prints: My name is Eva  and I am 27 years old

#### kotlin string template, 使用${}
	val name = "Eva"
	val message = "My name has ${name.length} characters"
	println(message) //Prints: My name has 3 characters

#### $,${}字串格式表達式
	val name = "Anne"
	val yearOfBirth = 1985
	val yearNow = 2018
	val message = "$name is ${yearNow - yearOfBirth} years old"
	
#### 使用索引運算子存取字元
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


#### strings + for...in
	fun main() {
	val str = "abcd"
	    for (c in str) {
	        println(c)
	    }
	}
	
#### strings and + 會自動轉為String
	fun main() {
	    val s = "abc" + 1
	    println(s + "def")
	}
	
#### 字串簡易表示法
	val s = "Hello, world!\n"

#### 多行文字
	fun main() {
	    val text = """
	        Tell me and I forget.
	        Teach me and I remember.
	        Involve me and I learn.
	        (Benjamin Franklin)
	        """
	    println(text)
	    
	}

#### 多行文字和trimMargin()
	fun main() {
	    val text = """
	        |Tell me and I forget.
	        |Teach me and I remember.
	        |Involve me and I learn.
	        |(Benjamin Franklin)
	        """.trimMargin()
	    println(text)
	    
	}