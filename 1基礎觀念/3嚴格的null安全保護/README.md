# 嚴格的null安全保護

為避免產生NullPointerException，使用可null能力的安全保護機制(類型加入可null參考, 不可null參考)

	val age: Int = null //錯誤不可null
	val name: String? = null //可null

### 不可使用-可null-直接呼叫方法，必需先使用null檢查
	val name: String? = null
	name.toUpperCase() //錯誤

不可null       | 可null
------------- | -------------
 Int          | Int?
String        | String?
Float         | Float?

### 
	var nullableVehicle: Vehicle?
	var vehicle: Vehicle
	nullableVehicle = vehicle // 正確
	vehicle = nullableVehicle // 錯誤


### 比較集合物件的可null的表示法

類型定義          | 本身           | 元素
-----------------| ------------- | -------------
ArrayList<Int>   | NO            | NO 
ArrayList<Int>?  | YES           | NO
ArrayList<Int?>  | NO            | YES
ArrayList<Int?>? | YES           | YES

### java android 和 kotlin android的比較
	//Java
	 @Override
	 public void onCreate(Bundle savedInstanceState) {
	        super.onCreate(savedInstanceState);
	        savedInstanceState.getBoolean("locked");//執行階段錯誤
	  }
	  
	  
	        
	//kotlin
	override fun onCreate(savedInstanceState: Bundle?) { //1
	    super.onCreate(savedInstanceState)
	    savedInstanceState.getBoolean("key") //編譯錯誤
	 }
	 
	 
	 
	//kotlin
	
	override fun onCreate(savedInstanceState: Bundle?) {
	         super.onCreate(savedInstanceState)
	         val locked: Boolean
	          if(savedInstanceState != null)
	              locked = savedInstanceState.getBoolean("locked")
	          else
	              locked = false
	}
	
### 使用安全呼叫運算子
	//kotlin
		override fun onCreate(savedInstanceState: Bundle?) { //1
		    super.onCreate(savedInstanceState)
		    savedInstanceState?.getBoolean("key") //安全呼叫 -- ?.
		 }
		 
	