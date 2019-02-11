# 原生資料類型
原生效能比組合類型效能好，由其在使用array時。
### kotlin沒有原生資料類型, 但可以將Numbers(Int,Long,Char,Short,Boolean,Float,Double)當作原生資料類型
	var code: Int = 75
	code.toChar()

###如果原生類型被成為可null，可以當作被箱子包裹，成為有特別的功能
	var weight: Int = 12 // 當作原生類型
	var weight: Int? = null // 被箱子包裹成為組合類型
	
###
	var a: Int = 1 // 原生類型
	var b: Int? = null // 組合類型
	b = 12 // 一樣是組合類型
	

