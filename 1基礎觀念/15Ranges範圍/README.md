# Ranges範圍
### 一個範圍
	val intRange = 1..4 // type IntRange (i>=1&&i<=4)
	val charRange= 'b'..'g' // type CharRange 'b'to'g',使用單引號

### Int,Long和Char類型的範圍可以使用for... each巡圈
	for (i in 1..5) print(i) // Prints: 12345
	for (i in 'b'..'g') print(i) // Prints: bcdefg

### 使用in檢查是否在範圍內
	val weight = 52
	val healthy = 50..75
	if (weight in healthy)
	println("$weight is in $healthy range")
	//Prints: 52 is in 50..75 range

### 使用in檢查是否在範圍內(使用字元)
	val c = 'k' // Inferred type is Char
	val alphabet = 'a'..'z'
	if(c in alphabet)
	println("$c is character") //Prints: k is a character

### range是漸增
	for (i in 5..1) print(i) // Prints nothing
	
### 使用-1漸減
	for (i in 5 downTo 1) print(i) // Prints: 54321

### 使用 step 改變漸增值
	for (i in 3..6 step 2) print(i) // Prints: 35

### downTo 和 step 混合使用
	for (i in 9 downTo 1 step 3) print(i)