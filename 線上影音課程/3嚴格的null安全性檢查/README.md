# 嚴格的null安全保護

為避免產生NullPointerException，使用可null能力的安全保護機制(類型加入可null參考, 不可null參考) 

不可null       | 可null
------------- | -------------
 Int          | Int?
String        | String?
Float         | Float?
 

```
fun main(){
    var str:String = "學習kotlin"
    //這是一般變數(none-nullable), 不可以有null
    //str = null;
    //var a:String = null;

    //使用類型+?定義nullable的變數
    var a:String? = null;
    var newStr:String? = "Kotlin null safety"
    newStr = null;

    //不可以使用可null變數直接呼叫方法，必需先使用null檢查
    var name:String? = null
    //name.toUpperCase() //編譯錯誤
}
```

## 使用if檢查null
```
fun main(){
    //使用if檢查null
    var a1:String? = null;
    if(a1 != null){
        println("這a的值是$a1");
    }else{
        println("這個值是null");
    }

    //nullable型別和none-nullable不是同一個型別, nullable是父類別, non-nullable是子類別
    var nullableInt:Int? = null
    var anInt = 6

    //正確
    nullableInt = anInt;
    println("nullableInt是$nullableInt");

    //錯誤的寫法
    anInt = nullableInt;
    println("anInt是$anInt")
}

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
fun main(){
    var newString:String? = "pcschools.com"
    newString = "kotlin from Android"
    //使用let方法來檢查和執行
    //只有當裏面的值不是null時，才會執行let的運算
    newString?.let {
        println("這個newString的值是:$it")
    }



    newString = null

    //使用 ?: run方法來判斷 如果值是 null要執行的動作
    newString?.let{
        println("這個newString的值是:$it")
    } ?: run {
        println("newString是null");
    }

    val listWithNulls: List<String?> = listOf("Kotlin", null, "android")

    //使用let()來檢查不是null
    for (item in listWithNulls) {
        item?.let { println(it) }
    }


}
```

## Elvis operator(貓王運算子)
#### 語法
	first operand ?: second operand
	
```
fun main(){
    //傳統使用if檢查是不是null的方法
    var a:String? = null;
    val l:Int = if (a != null) a.length else -1
    println("l的類型是none-nullable的型態，值是:$l")

    //使用 ?: (Elvis operator(貓王運算子))
    var b:String? = null
    val len:Int  = b?.length ?: -1
    println("len的類型是none-nullable的型態，值是:$len")

    //呼叫會傳出nullable的function
    println("傳出的值是:${stringToInt("123") ?: "無法轉換"}")

    //同時使用多個安全呼叫運算子 + Elvis運算子
    val intString:String? = "abc"
    val secondInt = intString?.toIntOrNull()?.and(3) ?: 0
    println("secondLen:$secondInt")

}

//使用貓王運算子 + return 或 throw打造出安全的function
fun stringToInt(string:String):Int? {
    val anInt = string.toIntOrNull() ?: return null
    val anotherInt = string.toIntOrNull() ?: throw IllegalArgumentException("無法轉換")
    return  anInt
```
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


