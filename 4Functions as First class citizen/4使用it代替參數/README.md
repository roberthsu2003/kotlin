# 使用it
 
	//可以省略lambda參數，有以下2個條件
	//1.只有一個參數
	//2.參數的資料類型可以推測
	
	val a: (Int) -> Int = { it * 2 }         // 1
	val c: (String)->Unit = { println(it) }  // 2

###LINQ style
	strings.filter { it.length = 5 }.map { it.toUpperCase() }
	
