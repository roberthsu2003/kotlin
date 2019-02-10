# Elvis operator(貓王運算子)

### 語法
	first operand ?: second operand

### 使用安全呼叫運算子 + Elvis運算子
	override fun onCreate(savedInstanceState: Bundle?) {
	            super.onCreate(savedInstanceState)
	            val locked: Boolean = savedInstanceState?.getBoolean("locked") ?: false
	}


### 使用安全呼叫串接運算子 + Elvis運算子
	val correct = quiz.currentQuestion?.answer?.correct ?: false

