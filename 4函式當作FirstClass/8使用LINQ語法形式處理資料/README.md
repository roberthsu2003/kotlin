# 使用LINQ語法形式處理資料
###呼叫 thread function
	strings.filter { it.length == 5 }.map { it.toUpperCase() }
	
###沒有使用簡潔呼叫
	strings.filter({ s -> s.length == 5 }).map({ s -> s.toUpperCase() })