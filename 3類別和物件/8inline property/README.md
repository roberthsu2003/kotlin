# inline property

	//inline是為了提升效能
	//限制只可以使用在沒有backing filed的property
	
	inline val now:Long
		 get() { 
		 println("Time retrieved") 
		 return System.currentTimeMillis() 
	}
	
### inline compiler完後的bytecode
	println("Time retrieved") 
	return System.currentTimeMillis() 
