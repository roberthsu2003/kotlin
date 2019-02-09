# 使用it

	val a: (Int) -> Int = { it * 2 }         // 1
	val c: (String)->Unit = { println(it) }  // 2

###LINQ style
	strings.filter { it.length = 5 }.map { it.toUpperCase() }
	
