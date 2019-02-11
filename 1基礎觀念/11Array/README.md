# 原生資料類型-Numbers
	val array = arrayOf(1,2,3) //推測為Array<Int>
	
### 明確指定類型
	val array2: Array<Short> = arrayOf(1,2,3)
	val array3: Array<Long> = arrayOf(1,2,3)

### kotlin提供提昇效能的array
	val array =  shortArrayOf(1, 2, 3)
	val array =  intArrayOf(1, 2, 3)
	val array =  longArrayOf(1, 2, 3)
	
### 有些微不一樣
	val array = arrayOf(1,2,3) // Array<Int>
	val array = longArrayOf(1, 2, 3) // LongArray

### 使用工廠function建立固定數量的array
	val array = arrayOfNulls(3) // Prints: [null, null, null]
	 println(array) // Prints: [null, null, null]

###使用Array建構式建立+lambda建立故定數量的array
	val array = Array (5) { it * 2 }
	println(array) // Prints: [0, 2, 4, 8, 10]

###存取元素
	val array = arrayOf(1,2,3)
	println(array[1]) //Prints: 2
