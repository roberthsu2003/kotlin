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


###使用Any類型，代表可以使用任何形別

	var title: Any = "Kotlin"
	title = 12




