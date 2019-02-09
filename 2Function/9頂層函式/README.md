# 頂層函式

### 放在kt檔內，不在class內
		// Test.kt
	        package com.example
	        fun printTwo() {
	            print(2)
	        }

### 必需明確的import
	// Test.kt
	        package com.example
	        fun printTwo() {
	            print(2)
	        }
	        // Main.kt
	        import com.example.printTwo
	        fun main(args: Array<String>) {
	            printTwo()
	        }
