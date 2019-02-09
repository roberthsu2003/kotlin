# 使用inline函式
	data class User(val name: String, val surname: String, val phone: String)
	
	val (name, surname, phone) = user
	
###使用lambda
	val showUser: (User) -> Unit = { (name, surname, phone) ->
	      println("$name $surname have phone number: $phone")
	}
	
	val user = User("Marcin", "Moskala", "+48 123 456 789")
	showUser(user)
	 // Marcin Moskala have phone number: +48 123 456 789

###
	val f1: (Pair<Int, String>)->Unit = { (first, second) ->
	            /* code */ 
	 } // 1
	val f2: (Int, Pair<Int, String>)->Unit = { index, (f, s)->
	            /* code */ 
	} // 2
	val f3: (Pair<Int, String>, User) ->Unit = { (f, s), (name,surname, tel) ->
	           /* code */ 
	} // 3

###解構部份資料
	val f: (User)->Unit = { (name, surname) -> /* code */ }
	
###在解構中使用底線
	val f: (User)->Unit = { (name, _, phone) -> /* code */ }
	val third: (List<Int>)->Int = { (_, _, third) -> third }

###使用推測類型參數資料類型
	val f = { (name, surname): User -> /* code */ } //1
	
###
	val f = { (name: String, surname: String): User ->
	           /* code */}// 1
	val f: (User)->Unit = { (name, surname) ->
	          /* code */ } // 2
	
###解構在android的運用
	val map = mapOf(1 to 2, 2 to "A")
	val text = map.map { (key, value) -> "$key: $value" }
	println(text) // Prints: [1: 2, 2: A]
	
###解構在android的運用
	val listOfPairs = listOf(1 to 2, 2 to "A")
	val text = listOfPairs.map { (first, second) ->
	            "$first and $second" }
	println(text) // Prints: [1 and 2, 2 and A]

   





