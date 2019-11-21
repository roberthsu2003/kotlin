# 延遲初始化的屬性

### 一定要是var, non-nullable,不行是primitive type

### 一個android範例屬性button延後給值(不切實際的方法)

	class MainActivity : AppCompatActivity() {
	           private var button: Button? = null
	           override fun onCreate(savedInstanceState: Bundle?) {
	               super.onCreate(savedInstanceState)
	               button = findViewById(R.id.button) as Button
	           }
	}
	

### 一個android範例屬性button延後給值(正確的使用方法)
	class MainActivity : AppCompatActivity() {
	            private lateinit var button: Button
	            override fun onCreate(savedInstanceState: Bundle?) {
	                button = findViewById(R.id.button) as Button
	                button.text = "Click Me"
	            } 
	}




