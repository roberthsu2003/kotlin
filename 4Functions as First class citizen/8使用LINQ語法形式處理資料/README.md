# processing data structures using LINQ style
	
### 沒有使用簡潔呼叫
	strings.filter({ s -> s.length == 5 }).map({ s -> s.toUpperCase() })
	
### LINQ style的呼叫
	strings.filter { it.length == 5 }.map { it.toUpperCase() }
