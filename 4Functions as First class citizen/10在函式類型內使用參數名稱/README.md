# 在函式類型內使用參數名稱
###沒有使用參數名稱
	fun setOnItemClickListener(listener: (Int, View, View)->Unit) {
	            // code
	 }
	setOnItemClickListener { position, view, parent -> /* ... */ }
	
###有使用參數名稱
	fun setOnItemClickListener(listener: (position:Int, view:View, parent:View)->Unit) {
		    // code
	}
	setOnItemClickListener { position, view, parent -> /* ... */ 
	}