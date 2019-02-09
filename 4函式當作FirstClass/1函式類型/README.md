# 函式類型
	lateinit var a: (Int) -> Int
	lateinit var b: ()->Int
	lateinit var c: (String)->Unit

###
	fun addCache(function: (Int) -> Int): (Int) -> Int {
	            // code
	}
	val fibonacciNumber: (Int)->Int = // function implementation
	val fibonacciNumberWithCache = addCache(fibonacciNumber)
	
###
	var todoList: List<() -> Unit> = // ...
	        for (task in todoList) task()
###
	val a: (Int) -> Unit = //... 
	a(10) // 1 
	a.invoke(10) // 1
