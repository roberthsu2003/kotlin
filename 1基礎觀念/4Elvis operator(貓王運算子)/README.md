# Elvis operator(貓王運算子)

### 語法
	first operand ?: second operand
	
### 傳統使用
	fun main() {
	    var b: String? = null   
	    val l: Int = if (b != null) b.length else -1
	    println(l);
	}

### 使用 Elvis operator
	fun main() {
	    var b: String? = null   
	    val l:Int = b?.length ?: -1
	    println(l);
	}
### 使用 Elvis operator 加上 throw 或 return
	fun foo(node: Node): String? {
	    val parent = node.getParent() ?: return null
	    val name = node.getName() ?: throw IllegalArgumentException("name expected")
	    // ...
	}
### 使用安全呼叫運算子 + Elvis運算子
	override fun onCreate(savedInstanceState: Bundle?) {
	            super.onCreate(savedInstanceState)
	            val locked: Boolean = savedInstanceState?.getBoolean("locked") ?: false
	}


### 使用安全呼叫串接運算子 + Elvis運算子
	val correct = quiz.currentQuestion?.answer?.correct ?: false

### 貓王運算子

![Elvis operator](pic1.png)