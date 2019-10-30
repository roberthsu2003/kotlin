# 嚴格的null安全保護

為避免產生NullPointerException，使用可null能力的安全保護機制(類型加入可null參考, 不可null參考) 

不可null       | 可null
------------- | -------------
 Int          | Int?
String        | String?
Float         | Float?
 

```
錯誤的方法
var str: String = "JournalDev Kotlin Archives"
str= null //compilation error
var a : String = null // compilation error.

使用類型+?定義nullable的變數
var a : String? = null
var newStr : String? = "Kotlin Null Safety"
newStr = null
```
### 不可使用-可null變數-直接呼叫方法，必需先使用null檢查

```
val name: String? = null
name.toUpperCase() //錯誤
```

## 使用if檢查null
```
var a : String? = null
if(a!=null)
{
	print("The value of a is $a")
}
else{
	print("Sorry a is null")
}
```


```
	var nullableInt: Int? = 5
	var anInt = 6
	nullableInt= anInt // 正確
	anInt = nullableInt // 錯誤
```

### 比較集合物件的可null的表示法

類型定義          | 本身           | 元素
-----------------| ------------- | -------------
ArrayList<Int>   | NO            | NO 
ArrayList<Int>?  | YES           | NO
ArrayList<Int?>  | NO            | YES
ArrayList<Int?>? | YES           | YES

	
## 使用安全呼叫運算子(?.)
```	
//一般類型的呼叫
var a : String = "Hello"
print(a.length)

//這些編譯將不會執行
var a : String? = "Hi"
print(a.length) //prints 2

a = null
print(a.length) // compilation error


//安全呼叫運算子就是只有值不是null時才會執行
fun main() {
	 val a = "Kotlin"
	 val b: String? = null
	 println(b?.length)
	 println(a?.length) // 一般變數不需要使用安全呼叫
	 
	 var b1: String? = "Hi !" // variable is declared as nullable
    var len: Int?
    len = b1?.length
    println("b1 is : $b1")
    println("length is : $len")
    
    b1 = null
    len = b?.length
    println("b is : $b")
    println("length is : $len")
}
```	
### 使用安全呼叫運算子+let()
```
只有當裏面的值不是null時，才會執行let的運算
var newString : String?  = "JournalDev.com"
newString = " Kotlin from Android"
newString?.let { println("The string value is: $it") }
newString = null
newString?.let { println("The string value is: $it") }


fun main() {
	val listWithNulls: List<String?> = listOf("Kotlin", null)
	for (item in listWithNulls) {
	    item?.let { println(it) } // prints A and ignores null
	}
}	
```

## Elvis operator(貓王運算子)
#### 語法
	first operand ?: second operand
	
#### 傳統使用
	fun main() {
	    var b: String? = null   
	    val l: Int = if (b != null) b.length else -1
	    println(l);
	}

#### 使用 Elvis operator
	fun main() {
	    var b: String? = null   
	    val l:Int = b?.length ?: -1
	    println(l);
	}
#### 使用 Elvis operator 加上 throw 或 return
	fun foo(node: Node): String? {
	    val parent = node.getParent() ?: return null
	    val name = node.getName() ?: throw IllegalArgumentException("name expected")
	    // ...
	}
#### 使用安全呼叫運算子 + Elvis運算子
	override fun onCreate(savedInstanceState: Bundle?) {
	            super.onCreate(savedInstanceState)
	            val locked: Boolean = savedInstanceState?.getBoolean("locked") ?: false
	}


#### 使用安全呼叫串接運算子 + Elvis運算子
	val correct = quiz.currentQuestion?.answer?.correct ?: false


## 保證不是null(not null assertion)

### 語法
	變數!!
	
### 使用方法
```
var y: String? = "foo"
var size: Int = y!!.length

fun main(args: Array<String>) {
    //Declaring boxed String
    var name: String? = "Little Drops"
    //Printing the length of the asserted value
    println("Length of $name is ${name!!.length}")
    //Setting null to the name variable
    name = null
    //This statement will create Null Pointer Exception
    println("Length of $name is ${name!!.length}")
}
```

## 智慧型轉型
```
var string: String? = "Hello!"  
print(string.length) // Compile error 

fun main(){  
	var string: String? = "Hello!"  
	if(string != null) { // smart cast  
		print(string.length) // It works now!  
	}  
}  
```

#### 智慧型轉換可以利用return,讓function剩下範圍都有智慧型轉換
	fun main() {
	    val name:String? = "robert";
	    if (name == null) return
	    println(name.length);
	}

### 智慧型轉換可以利用return,讓function剩下範圍都有智慧型轉換
	fun main() {
	    var name:String? = "robert";
	    name ?: return
	    println(name.length);
	}

### 智慧型轉換可以利用throw,讓function剩下範圍都有智慧型轉換
	fun setView(view: View?){
	    view ?: throw RuntimeException("View is empty")
	    
	    view.isShown() //view被轉換為不可null類型
	 }


