# 類型推測

### 建立要求是字串的變數
	var title: String
	
### 同時宣告變數名稱和資料類型並將內容傳給變數(明確宣告變數類型)
	var title: String = "Kotlin"

### 宣告變數名稱和將內容傳給變數，資料類型請編譯器自行推測(不明確宣告)
	var title = "Kotlin"

### kotlin 是 strongly type language
	var title = "Kotlin"
	title = 12 // 1, Error


### 使用Any類型，代表可以使用任何形別,java的是primitive類型

	var title: Any = "Kotlin"
	title = 12

### 推測沒有被限定一定要是值，也可以是function(mac 使用control+shift+p 可以檢查資料類型)
	var total = sum(10, 20)
	
### 類型推測也可推測泛型
	var persons = listOf(personInstance1, personInstance2)
	// 推測類型為: List<Person> ()

### 類型推測
	var pair = "Everest" to 8848 // 推測類型為: Pair<String, Int>
	
### 類型推測
	var pair = "Everest" to 8848
	// 建立pair 使用infix function
	var pair2 = Pair("Everest", 8848)
	// 使用建構子建立 pair

### 由內向外推測
	var map = mapOf("Mount Everest" to 8848, "K2" to 4017)
	// 推測類型為: Map<String, Int>

### 不同資料類型，會推測Any
	var map = mapOf("Mount Everest" to 8848, "K2" to "4017")
	// 推測類型為: Map<String, Any>

### 明確宣告
	var age: Int = 18

### 值表達式無沒推測為正確類型時，可以使用明確宣告
	var age: Short = 18

### 使用指定型別的值表達式
	var age: Long = 18 // 明確宣告變數
	var age = 18L //指定Long的值表達式
	
### 錯誤的語法(無法推測)
	val title // 錯誤







