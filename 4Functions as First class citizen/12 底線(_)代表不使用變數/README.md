# 底線(_)代表不使用變數
### 沒有使用的lambda運算式的value參數
	list.filterIndexed { index, value -> index % 2 == 0 }

### 使用_取代
 	list.filterIndexed { index, _ -> index % 2 == 0 }
 






