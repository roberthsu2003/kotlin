# 保證不是null

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

###使用let
	override fun onCreate(savedInstanceState: Bundle?) { 
	     super.onCreate(savedInstanceState)
	     savedInstanceState?.let{ 
	                         println(it.getBoolean("isLocked")) 
	                         }
	}

