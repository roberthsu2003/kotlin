# 強制執行(not null assertion)
風險高,就和java語言一樣,除非保証值非null,不然要使用安全呼叫(?.)+let,會使用智慧型轉換( != nil)

### 語法
	變數!!
	
### 使用方法
	var y: String? = "foo"
	var size: Int = y!!.length

### android
	override fun onCreate(savedInstanceState: Bundle?) {
	        super.onCreate(savedInstanceState)
	        val locked: Boolean = savedInstanceState!!.getBoolean("locked")
	        
	}

### 使用let
	override fun onCreate(savedInstanceState: Bundle?) { 
	     super.onCreate(savedInstanceState)
	     savedInstanceState?.let{ 
	                         println(it.getBoolean("isLocked")) 
	                         }
	     // let()使用的是lambda
	}

### java API 轉過來的Type, 如果是可能為null,將轉換為platform types(平台類型)(類型名稱+!)
```
View! //View defined as platform type
我可以將平台類型看成none-nullable,或nullable
T! = T or T?

val textView = findViewById(R.id.textView) as TextView //1
val textView = findViewById(R.id.textView) as TextView //2
```