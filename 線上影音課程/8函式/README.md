# 函式(Function)
## 基本function定義與使用
``` kotlin
fun main() {
	 println("Hello,World");
}
```
### 可以傳出值的function
```
fun double(i:Int):Int
{
	return 2 * i
}
```
### 呼叫function
```
val a = double(5);
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

### 參數名稱和引數名稱

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



