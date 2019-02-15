# 其它重複執行

	val range = 1..6
	for(i in range) {
	 	print("$i ") 
	}
	// prints: 1 2 3 4 5 6
	
### 
	val range = 1..6
	for(i in range) {
	  print("$i ")
	  if (i == 3) break 
	}
	// prints: 1 2 3
	
###
	val intRange = 1..6
	val charRange = 'A'..'B' 
	for(value in intRange) {
	   if(value == 3) break
	   println("Outer loop: $value ") 
	   for (char in charRange) 
	   { 
	      println("\tInner loop: $char ") 
	   } 
	}
	
	// prints
	Outer loop: 1
	Inner loop: A Inner loop: B
	Outer loop: 2
	Inner loop: A Inner loop: B
	
###

	val intRange = 1..5
	for(value in intRange) { 
	   if(value == 3) continue
	   
	   println("Outer loop: $value ")
	   
		for (char in charRange) { 
		    println("\tInner loop: $char ") 
		} 
	}
	
	
	// prints
	Outer loop: 1
	Inner loop: A Inner loop: B
	Outer loop: 2
	Inner loop: A Inner loop: B
	Outer loop: 4
	Inner loop: A Inner loop: B
	Outer loop: 5
	Inner loop: A Inner loop: B

###

	val charRange = 'A'..'B'
	val intRange = 1..6
	 
	outer@ for(value in intRange) { 
	     println("Outer loop: $value ") 
	     for (char in charRange) {
	     if(char == 'B') break@outer 
	     println("\tInner loop: $char ") 
	    } 
	}
	
	// prints 
	Outer loop: 1 
	Inner loop: A

###
	fun doSth() {
	   val charRange = 'A'..'B'
	   val intRange = 1..6
	   for(value in intRange) {
	     println("Outer loop: $value ") 
	     for (char in charRange) { 
	       println("\tInner loop: $char ") 
	       return
	     } 
	    } 
	}
	
	println("Before method call") 
	doSth() 
	println("After method call")
 
	//Outer loop: 1 
	//Inner loop: A
