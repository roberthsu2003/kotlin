# combination of named arguments and lambda expressions

### 定義參數onStart有default value, onFinish也有 default value
	fun getAndFillList(onStart: () -> Unit = {},
	        onFinish: () -> Unit = {}){
		// code 
	}
	//呼叫使用2個引數名稱
	getAndFillList(
            onStart = { view.loadingProgress = true } ,
            onFinish = { view.loadingProgress = false }
	)
	
	//呼叫使用1個引數名稱，另一個使用default value
	getAndFillList(onFinish = { view.swipeRefresh.isRefreshing = false })
	
	//呼叫沒有使用引數名稱，全部使用default value
	getAndFillList()
