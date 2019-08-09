# 原生資料類型-Numbers
類型           | bit
------------- | -------------
Double        | 64
Float         | 32
Long          | 64
Int           | 32
Short         | 16
Byte          | 8

### kotlin和java有一點不一樣，小的資料類型不能隱式轉換為大的資料類型
	var weight : Int = 12
	var truckWeight: Long = weight // 錯誤

### 需要明確轉換為目同資料類型
	var weight:I nt = 12
	var truckWeight: Long = weight.toLong()
### 數值可以轉換的方法
~~~
> toByte():Byte
> toShort():Short
> toInt():Int
> toLong():Long
> toFloat():Float
> toDouble():Double
> toChar():Char
~~~
### 可以用數值來改變推測
	val a: Int = 1
	val b = a + 1 // 推測Int
	val b = a + 1L // 推測為Long

### kotlin數值表示
~~~
> 27 //Int
> 27L //Long
> 0x1B //16進位數值
> 0b11011 //2進位
~~~

### 浮點數值
~~~
> 27.5 //Double
> 27.5F //Float
~~~






