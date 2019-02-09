# 暱名函式

	val a: (Int) -> Int = fun(i: Int) = i * 2 // 1
	val b: ()->Int = fun(): Int { return 4 }
	val c: (String)->Unit = fun(s: String){ println(s) }
	
###
	// Usage
	    println(a(10))
	    println(b())
	    c("Kotlin rules")
	// Prints: 20
	// Prints: 4
	// Prints: Kotlin rules
	
###使用類型推測
	var a = fun(i: Int) = i * 2
	var b = fun(): Int { return 4 }
	var c = fun(s: String){ println(s) }
	
###暱名函式參數使用類型推測
	var a: (Int)->Int = fun(i) = i * 2
	var c: (String)->Unit = fun(s){ println(s)
	
###使用invoke呼叫
	println(a.invoke(4))        // Prints: 8
	println(b.invoke())         // Prints: 4
	c.invoke("Hello, World!")   // Prints: Hello, World!

###函式類型可以null,使用invoke做安全呼叫
	var a: ((Int) -> Int)? = null // 1
	if (false) a = fun(i: Int) = i * 2
	print(a?.invoke(4)) // Prints: null
###
	val TAG = "MainActivity"
	        val errorHandler = fun (error: Throwable) {
	            if(BuildConfig.DEBUG) {
	                Log.e(TAG, error.message, error)
	            }
	            toast(error.message)
	            // Other methods, like: Crashlytics.logException(error)
	}
	// Usage in project
	val adController = AdController(errorHandler)
	val presenter = MainPresenter(errorHandler)
	// Usage
	val error = Error("ExampleError")
	errorHandler(error) // Logs: MainActivity: ExampleError

 