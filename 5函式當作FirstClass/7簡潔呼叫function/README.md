# 簡潔呼叫function
###呼叫 thread function
	thread {
	        operation1()
	        operation2()
	 }

###自行定義可簡潔呼叫的function
	fun addLogs(tag: String, f: () -> Unit) {
	            println("$tag started")
	            val startTime = System.currentTimeMillis()
	            f()
	            val endTime = System.currentTimeMillis()
	            println("$tag finished. It took " + (endTime - startTime))
	}
	
	//呼叫語法
	addLogs("Some operations") {
	            // Operations we are measuring
	}
	
	//呼叫
	addLogs("Sleeper") {
	            Thread.sleep(1000)
	}
	
	//結果
	Sleeper started
	Sleeper finished. It took 1001
	
###版本確定使用一般寫法
	
	if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP) {
            // Operations
	}
###版本確定使用簡潔呼叫function的寫法
	fun ifSupportsLolipop(f:()->Unit) {
	            if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.LOLLIPOP)
	            {
	             f()         
	            }
	}
	
	//Usage
	ifSupportsLollipop {
	    // Operation
	}

###應用
	fun repeatUntilError(code: ()->Unit): Throwable {
	            while (true) {
	                try { 
	                  code()
	                } catch (t: Throwable) {
	                    return t
	                } 
	             }
	}
	
	
	// Usage
	val tooMuchAttemptsError = repeatUntilError {
	     attemptLogin()
	 }
