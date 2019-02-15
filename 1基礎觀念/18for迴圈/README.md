# for迴圈
	//Java
        String str = "Foo Bar";
        for(int i=0; i<str.length(); i++)
        System.out.println(str.charAt(i));
### 
	var array = arrayOf(1, 2, 3)
	for (item in array) {
	      print(item)
	}
	
###不需要block
	for (item in array)
	     print(item)

### 自動轉型
	var array = arrayOf(1, 2, 3)
	for (item in array)
	     print(item) // item is Int
### 取得索引
	for (i in array.indices)
	    print(array[i])

### 使用withIndex()
	for ((index, value) in array.withIndex()) {
	      println("Element at $index is $value")
	      }