# 名稱參數和lambda整合

	fun getAndFillList(onStart: () -> Unit = {},
	        onFinish: () -> Unit = {}){
		// code 
	}
	
	getAndFillList(
            onStart = { view.loadingProgress = true } ,
            onFinish = { view.loadingProgress = false }
	)

	getAndFillList(onFinish = { view.swipeRefresh.isRefreshing = false })
	
	getAndFillList()
