# if敘述
	val x = 5
	if(x > 10){
	     println("greater")
	} else {
	     println("smaller")
	}
	
### 這也是正確的
	val x = 5
	if(x > 10)
	     println("greater")
	 else
	      println("smaller")
	 
### java對待if當作statement,kotlin對待if當作expression
	println(if(x > 10) "greater" else "smaller")
	
### 對待當statements
	val hour = 10
	val greeting: String
	if (hour < 18) {
	      greeting = "Good day"
	 } else {
	      greeting = "Good evening"
	 }
	 
### 對待當作expression
	val greeting = if (hour < 18) "Good day" else "Good evening"

### 會自動return最後一行
	val hour = 10
	val greeting = if (hour < 18) {
	     //some code
	      "Good day"
	 } else {
			//some code
	      "Good evening"
	 }
	 println(greeting) // Prints: "Good day"


### 
	val age = 18
	val message = "You are ${ if (age < 18) "young" else "of age" } person"
	 println(message) // Prints: You are of age person
