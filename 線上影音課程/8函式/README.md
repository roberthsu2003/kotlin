# 函式(Function)
## 基本function定義與使用
``` kotlin
fun main() {
	 println("Hello,World");
}
```

```kotlin
fun main(){
    //範例
    //輸入姓名，上下行要印出20個「-」符號
    print("請輸入您的姓名:")
    val name = readLine() ?: ""
    printStart()
    println("您的姓名是:$name")
    printStart()
}

fun printStart(){
    for (index in 1..20){
        print("-")
    }
    println();
}

```
### 可以傳出值的function
``` kotlin
fun double():Int
{
	return 2 * 2
}
```

### 呼叫function

```kotlin
val a = double(5);
```

```kotlin
fun main(){
    //範例
    //輸入姓名，上下行要印出20個「-」符號
    print("請輸入您的姓名:")
    val name = readLine() ?: ""
    println(outPutStart())
    println("您的姓名是:$name")
    println(outPutStart())
}

fun outPutStart():String{
    var symbol = ""
    for (index in 1..20){
        symbol += "-"
    }
    return symbol
}
```

## 參數
* 必需有明確的參數名稱和類形
* 所有的參數是唯讀的   

### 可以定義和區域變數相同的參數名稱，但這是不好的習慣 

```kotlin
fun findDuplicates(list:List<Int>):Set<Int>{
	var list = list.sorted();
}
```

### 參數名稱和引數

* 引數名稱一個真實的值，傳遞給function。
* 參數名稱是一個變數名稱，使用在定義function時  

```kotlin
fun printSum(a1:Int, a2:Int){
	print(a1 + a2);
}
		
add(3,5)
```		
### 多個參數名稱

```kotlin
fun printSum(a1:Int, a2:Int){
	val sum = a + b
	print(sum)
}
```
	
### 引數可以使用參數定義時的子類別  

```kotlin
fun main() {
	 presentGently("Robert")
	 presentGently(42)
}
	
fun presentGently(v:Any){ //使用Any類別，可以使用所有non-nullable的類別
	 println("Hello. I would like to present you : $v");
}
```
### 參數可以定義是nullable. 

```kotlin
fun presentGently(v: Any?) {
	 println("Hello. I would like to present you: $v")
}
presentGently(null)
// Prints: Hello. I would like to present you: null
presentGently(1)
// Prints: Hello. I would like to present you: 1
presentGently("Str")
// Prints: Hello. I would like to present you: Str
```

```kotlin


fun main(){
    //列印出2數相加
    print("請輸入第一個值:")
    val f = readLine()?.toIntOrNull() ?: 0
    print("請輸入第二個值:")
    val s = readLine()?.toIntOrNull() ?: 0
    printAdd(f,s)
}

fun printAdd(first:Int, second:Int){
    print("$first + $second = ${first + second}")
}
```

# 傳回值
*  所有function都有傳回值  
*  沒有傳回值，可以省略，也可以明確傳回Unit類型 

``` kotlin
fun main() {
	printSum(3, 5);
}
	
fun printSum(a: Int, b:Int):Unit{
	 val sum = a + b;
	 print(sum);
}
```	
### kotlin Unit相等於 Java的void, Unit是物件，可以被儲存. 

```kotlin
fun main() {
	val p = printSum(3, 5)
	println(p is Unit)
}
	
fun printSum(a: Int, b:Int):Unit{
	 val sum = a + b
	 println(sum)
}
```	
### kotlin建議是Unit就省略  

```kotlin
fun printSum(a: Int, b:Int){
	 val sum = a + b
	 println(sum)
}
```

### 當傳出Unit時，可以使用return，不用帶任何值  
 
```kotlin
fun main() {
	val p = printSum(3, 5)    
}
	
fun printSum(a: Int, b:Int){
	if(a<0 || b<0){
	   return
	}	   
	val sum = a + b;
	print(sum)
}
```

### 當傳出傳出值時，實作一定要明確傳出 

```kotlin
fun sumPositive(a:Int, b:Int):Int{
	if(a > 0 && b > 0){
	  eturn a + b; //在if	單行選項內,有可能不被執行
	}
	  //error
}
	
fun sumPositive(a:Int, b:Int):Int{
if(a > 0 && b > 0){
    return a + b;
 }
    
return 0;
}
	
```	

# 參數vararg
### 有vararg代表充許function接收任何數量的參數

```kotlin
fun main() {
	 printSum(1,2,3,4,5)
	 printSum();	    
}
	
fun printSum(vararg numbers:Int){
	 val sum = numbers.sum()
	 println(sum);
}  
```
### vararg傳入的參數是Array<T>

```kotlin
fun main() {
	 printAll("A", "B", "C");	    
}
	
fun printAll(vararg texts:String){
	 //推測這texts的資料類型是Array<String>
	 val allTexts = texts.joinToString(",")
	 println("Texts are $allTexts");
}
```	

### 可以在vararg前或後加入更多參數
```kotlin
fun main() {
	 printAll("All texts: ", "!");
	 printAll("All texts: ", "!", "Hello",  "World");
}
	
fun printAll(prefix:String, postfix:String, vararg texts:String){
	 val allTexts = texts.joinToString(", ")
	 println("$prefix$allTexts$postfix");
}
```
### vararg引數可以使用該型別的子類別

```kotlin
fun main() {	    
	 printAll("A", 1, 'c');
}
	
fun printAll(vararg texts:Any){
	 val allTexts = texts.joinToString(", ");
	 println(allTexts);
}
```

### 使用*符號+陣列，代表每個元素當作參數

```kotlin
fun main(){
	val texts = arrayOf("B", "C", "D")
	printAll(*texts) // Prints: Texts are: B,C,D
	printAll("A", *texts, "E") // Prints: Texts are: A,B,C,D,E
}

fun printAll(vararg texts:Any){
	 val allTexts = texts.joinToString(", ");
	 println(allTexts);
}
	
```

## 單行運算式的function(single-expression Funciton)
### 傳統單行運算式function

```kotlin
fun square(x:Int):Int{
	 //這是單行運算式function
	 return x * x
} 
	
//andorid 內容
fun getEmail():String{
   return emailView.text.toStirng()
}
```

### 單行運算式有使用區塊符號

```kotlin
fun square(x:Int):Int{
	    //這是單行運算式function
	 return x * x
} 
```	
		
### 單行運算式可以省略區塊符號和return, 也可以省略定義傳回值，因為kotlin會自我推測

```kotlin
fun square(x:Int) = x * x

fun hello() : String = "hello world"

fun hello(name: String, location: String): String = "hello to you  $name at $location"

fun concat1(a: String, b: String) = a + b
```	


### 在andoird內的應用
```kotlin
class AddressAdapter : ItemAdapter<AddressAdapter.ViewHolder>() {
	   override fun getLayoutId() = R.layout.choose_address_view
	   override fun onCreateViewHolder(itemView: View) = ViewHolder(itemView)
	        // Rest of methods
 }
```
### 單行運算式搭配when判斷式

```kotlin
fun valueFromBooking(key: String, booking: Booking?) = when(key) {
	        "patient.nin" -> booking?.patient?.nin
	        "patient.email" -> booking?.patient?.email
	        "patient.phone" -> booking?.patient?.phone
	        "comment" -> booking?.comment
				else -> null 
	}
```

### 單行運算式搭配多重串接運算

```kotlin
fun textFormatted(text: String, name: String) = text
	                          .trim()
	                          .capitalize()
	                          .replace("{name}", name)
val formatted = textFormatted("hello, {name}", "Marcin")
println(formatted) // Hello, Marcin

```
### 和android 的activity onOptionsItemSelected method 整合

```kotlin
override fun onOptionsItemSelected(item: MenuItem): Boolean = when
{
	        item.itemId == android.R.id.home -> {
	            onBackPressed()
					 true 
				}
	        else -> super.onOptionsItemSelected(item)
}
```

# 尾部遞迴function
* 自已呼叫自已  

### 傳統遞迴--太多會throw statkOverflowError  
```kotlin
fun getState(state: State, n: Int): State =
      if (n <= 0) state 
      else 
      getState(nextState(state), n - 1)
 	
//other
fun fact(k: Int): Int {
    if (k == 0) return 1
    else 
    return k * fact(k - 1)
}
```	
	
   
   
   

### 傳統解決方案--不好了解  
```kotlin
fun getState(state: State, n: Int): State {
	    var state = state
	    for (i in 1..n) {
	      state = state.nextState()
		}
	  return state
 }
```
### 最佳解決方案 尾部遞迴
```kotlin
tailrec fun getState(state:State, n:Int):State =if (n <=0 ){ 
	state
	}else{
	getState(state.nextState(), n-1)
}
```

### 尾部遞迴相似java程式碼

```kotlin
public static final State getState(@NotNull State state, int n)
	  {
	     while(true) {
	         if(n <= 0) {
	            return state;
	         }
	         state = state.nextState();
				 n = n - 1; 
		}
}
```

## 引數預設值

```kotlin
fun main() {
	 printValue("robert",true,"","")
	 printValue("jenny")
	 printValue("alice",false)
}
	
fun printValue(value:String,inBracket:Boolean=true,prefix:String="",suffix:String=""){
	  print(prefix)
	  if(inBracket){
	      print("${value}")
	   }else{
	      print(value)
	   }
	   println(suffix)
}
```

## 引數標籤名稱語法

```kotlin
fun main() {
	 printValue("robert",true,"","!")
	 printValue("jenny",suffix = "!",prefix="--")
}
	
fun printValue(value:String,inBracket:Boolean=true,prefix:String="",suffix:String=""){
	print(prefix)
	if(inBracket){
	    print("${value}")
	}else{
	    print(value)
	}
	println(suffix)
}
```
### 可讀性更高

```kotlin
fun main() {
	printValue("str", inBracket=true)
	printValue("str", prefix = "Value is")
	printValue("str",prefix = "Value is", suffix = "!!")    
}

```	
### 使用引數標籤，可以不依照順序

```kotlin
fun main() {
	printValue("str", inBracket=true, prefix = "value is")
	printValue("str", prefix = "Value is", inBracket=true)  
}
```	
### 前面使用引數位置，後面使用引數標籤(不可以顛倒)

```kotlin
fun main() {
	 printValue("str",true,"")
	 printValue("str", true, prefix = " ")
	 printValue("str", inBracket = true, prefix = "")
	 printValue("str",inBracket=true, "") //錯誤
}
```
* 呼叫java function不可以使用引數名稱

## 頂層函式

### 放在kt檔內，不在class內 

```kotlin
// Test.kt
package com.example
fun printTwo() {
	    print(2)
}
```

### 必需明確的import

```kotlin
// Test.kt
package com.example
fun printTwo() {
	print(2)
}
// Main.kt
import com.example.printTwo
fun main(args: Array<String>) {
	 printTwo()
}
```

## 頂層函式在java內的使用

### android runtime virtual Machine只能執行在 class內的code

```kotlin
// Printer.kt
fun printTwo() {
	 print(2) 
}

//Java
public final class PrinterKt { // 1
	 public static void printTwo() { // 2
	   System.out.print(2); // 3
	 }
}
	
//Java file, call inside some method
    PrinterKt.printTwo()
```
 
### 在java內更方便使用kotlin的頂層函數
```kotlin
在kotlin最上層，import上方
//kotlin
@file:JvmName("Printer")
	
	
//Java
Printer.printTwo()
```  	
### 在不同kt檔案內的頂層函式，可讓轉成相同java class內的靜態方法

```kotlin
// Max.kt
	 @file:JvmName("Math")
	 @file:JvmMultifileClass
	 package com.example.math
	 fun max(n1: Int, n2: Int): Int = if(n1 > n2) n1 else n2
	        
// Min.kt
	 @file:JvmName("Math")
	 @file:JvmMultifileClass
	 package com.example.math
	 fun min(n1: Int, n2: Int): Int = if(n1 < n2) n1 else n2
	 
// java
	Math.min(1, 2)
	Math.max(1, 2)	
```	 

  


