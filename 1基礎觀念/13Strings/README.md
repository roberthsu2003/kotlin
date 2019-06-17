# Strings
### 使用索引運算子存取字元
~~~
使用和java String一樣Class，這些多的功能是被定義在extensions
kotlin在處理時，比java有多一些功能，可以使用indexing operator存取字元
~~~
	val str = "abcd" 
	println (str[1]) // Prints: b

	val str = "abcd" 
	println(str.reversed()) // Prints: dcba 
	
	println(str.takeLast(2)) // Prints: cd
	println("john@test.com".substringBefore("@")) // Prints: john
	println("john@test.com".startsWith("@")) // Prints: false


### strings + for...in
	fun main() {
	val str = "abcd"
	    for (c in str) {
	        println(c)
	    }
	}
	
### strings and + 會自動轉為String
	fun main() {
	    val s = "abc" + 1
	    println(s + "def")
	}
	
### 字串簡易表示法
	val s = "Hello, world!\n"

### 多行文字
	fun main() {
	    val text = """
	        |Tell me and I forget.
	        |Teach me and I remember.
	        |Involve me and I learn.
	        |(Benjamin Franklin)
	        """
	    println(text)
	    
	}

### 多行文字和trimMargin()
	fun main() {
	    val text = """
	        |Tell me and I forget.
	        |Teach me and I remember.
	        |Involve me and I learn.
	        |(Benjamin Franklin)
	        """.trimMargin()
	    println(text)
	    
	}