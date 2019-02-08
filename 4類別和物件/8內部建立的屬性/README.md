# 內部建立的屬性

	inline val now: Long
		 get() { 
		 println("Time retrieved") 
		 return System.currentTimeMillis() 
		 }
