# when運算式
	fun main(){
	    val x = 5
	    when (x) {
	        1 -> print("x == 1")
	        2 -> print("x == 2")
	        else -> println("x 不是1也不是2")
	    }
	    
	}
### 當作運算式
	val message= when (vehicle) {
	    "Car" -> {
	    // Some code
	     "Four wheels"
	    }
	     "Bike" -> {
	     // Some code
	      "Two wheels"
	    }
	       else -> {
	       //some code
	       "Unknown number of wheels"
	    }
	 }
	 println(message) //Prints: Two wheels
	 
### 群組比對
	val vehicle = "Car"
	    when (vehicle) {
	       "Car", "Bike" -> print("Vehicle")
	       else -> print("Unidentified funny object")
	}

### 比較類型
	val name = when (person) {
	           is String -> person.toUpperCase()
	           is User -> person.name
	           //Code is smart casted to String, so we can
	           //call String class methods
	           //...
	}	

### 範圍
	val riskAssessment = 47
	val risk = when (riskAssessment) {
	           in 1..20 -> "negligible risk"
	           !in 21..40 -> "minor risk"
	           !in 41..60 -> "major risk"
	           else -> "undefined risk"
	        }
	println(risk) // Prints: major risk
	
### 
	val riskAssessment = 80
	val handleStrategy = "Warn"
	val risk = when (riskAssessment) {
	            in 1..20 -> print("negligible risk")
	            !in 21..40 -> print("minor risk")
	            !in 41..60 -> print("major risk")
	            else -> when (handleStrategy){
	                "Warn" -> "Risk assessment warning"
	                "Ignore" -> "Risk ignored"
	                else -> "Unknown risk!"
	}
	}
	println(risk) // Prints: Risk assessment warning

###
	private fun getPasswordErrorId(password: String) = when {
	        password.isEmpty() -> R.string.error_field_required
	        passwordInvalid(password) -> R.string.error_invalid_password
	        else -> null
	}
	
### 
~~~

fun main() {
    
    print(getPasswordErrorId(50));
}
fun getPasswordErrorId(num: Int) = when {
	        (num > 50) -> "abc"
	       (num <= 50) -> "efg"
	        else -> null
	}
	
~~~
	
###
	val large:Boolean = true
	    when(large){
	        true -> println("Big")
	        false -> println("small")
	}

	
