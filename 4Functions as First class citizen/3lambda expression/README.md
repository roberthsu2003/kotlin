# lambda expression
### {arguments -> function body}

lambda | function type |
-------|---------------|
{1} | ()->Int 
{s:String -> println(s)} | (String) -> Unit |
{a:Int, b:Int -> a + b | (Int,Int) -> Int |  

	var a: (Int) -> Int = { i: Int -> i * 2 }
	var b: ()->Int = { 4 }
	var c: (String)->Unit = { s: String -> println(s) }
	
### lambda的function body最後一行就是自動return,所以不允許再有(return), 除非有return at label
	var a: (Int) -> Int = { i: Int -> return i * 2 }
	 // Error: Return is not allowed there
	 var l: (Int) -> Int = l@ { i: Int -> return@l i * 2 }
	 
### 可以有多行

	val printAndReturn = { i: Int, j: Int ->
	            println("I calculate $i + $j")
	            i + j // 1 
	}
	
### 使用;,多行可以變一行
	val printAndReturn = {i: Int, j: Int -> println("I calculate $i + $j"); i+j}
	
### lambda的body區可以使用外部的屬性和函式
	val text = "Text"
	var a: () -> Unit = { println(text) }
	a() // Prints: Text
	a() // Prints: Text

### lambda就是closure，可以改變外部的屬性值,但java8的lambda不可以
	var i = 1
	val a: () -> Int = { ++i }
	println (i)     // Prints: 1
	println (a())   // Prints: 2
	println (i)     // Prints: 2
	println (a())   // Prints: 3
	println (i)     // Prints: 3

### android實作
	fun setUpCounter() {
	            var value: Int = 0
	            val showValue = { counterView.text = "$value" }
	            counterIncView.setOnClickListener { value++; showValue() }
	            // 1
	            counterDecView.setOnClickListener { value--; showValue() }
	            // 1
	}
### lambda 參數可以不用定義資料類型，傳出值也不必定義傳出值，可以使用推測
	val a:(Int)->Int={i->i*2} //i的資料類型透過推法可以知道是Int, 透過i*2可以知道return type
	val c: (String)->Unit = { s -> println(s) } // s透過推測可以知道是String

### lambda的變數資料類型也可以使用推測
	val b = { 4 } // 1 
	val c={s:String->println(s)} //2 
	val a = { i: Int -> i * 2 } // 3

	
	
	
	