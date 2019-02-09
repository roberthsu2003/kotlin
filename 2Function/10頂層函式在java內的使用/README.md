# 頂層函式在java內的使用

### android runtime virtual Machine只能執行在 class內的code
	// Printer.kt
	        fun printTwo() {
	            print(2) 
	         }

	//Java
	public final class PrinterKt { // 1
	       public static void printTwo() { // 2
	        System.out.print(2); // 3
	       }
	}
	
	//Java file, call inside some method
        PrinterKt.printTwo()
  
### 在java內更方便使用kotlin的頂層函數
	在kotlin最上層，import上方
	//kotlin
	@file:JvmName("Printer")
	
	
	//Java
   	Printer.printTwo()
   	
### 在不同kt檔案內的頂層函式，可讓轉成相同java class內的靜態方法

	// Max.kt
	        @file:JvmName("Math")
	        @file:JvmMultifileClass
	        package com.example.math
	        fun max(n1: Int, n2: Int): Int = if(n1 > n2) n1 else n2
	        
	// Min.kt
	        @file:JvmName("Math")
	        @file:JvmMultifileClass
	        package com.example.math
	        fun min(n1: Int, n2: Int): Int = if(n1 < n2) n1 else n2
	 // java
		 		Math.min(1, 2)
	        Math.max(1, 2)	
	 

  