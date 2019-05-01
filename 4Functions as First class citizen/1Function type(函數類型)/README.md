# function type 函式類型

### function可以成為引數,function可以return,function可以指定給變數
	lateinit var a: (Int) -> Int
	lateinit var b: ()->Int
	lateinit var c: (String)->Unit

### 參數function type,return function type
	fun addCache(function: (Int) -> Int): (Int) -> Int {
	            // code
	}
	val fibonacciNumber: (Int)->Int = // function implementation
	val fibonacciNumberWithCache = addCache(fibonacciNumber)
	
### function不僅可以儲存在變數,也可以使用在泛型內
	var todoList: List<() -> Unit> = // ...
	        for (task in todoList) task()
### 將function指定給變數,變數呼叫function的2種方式
	val a: (Int) -> Unit = 
	a(10) // 1 
	a.invoke(10) // 1
