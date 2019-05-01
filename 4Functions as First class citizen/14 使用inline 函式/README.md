# 使用inline函式
	inline fun printExecutionTime(f: () -> Unit) {
	            val startTime = System.currentTimeMillis()
	            f()
	            val endTime = System.currentTimeMillis()
	            println("It took " + (endTime - startTime))
	}
	        fun measureOperation() {
	            printExecutionTime {
	                longOperation()
	            }
	}
	
### 呼叫inline function被反編譯後的結果
	fun measureOperation() {
            val startTime = System.currentTimeMillis() // 1
            longOperation() // 2
            val endTime = System.currentTimeMillis()
            println("It took " + (endTime - startTime))
	}


   





