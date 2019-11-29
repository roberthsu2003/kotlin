# 類別的基本知識
## java的類別定義

```java
class Person{
	
}

class Playground {
	public static void main(String[ ] args) {
	   Person person = new Person();
	}
}
```
## kotlin的類別定義
```kotlin
class Person;

fun main() {
	val person = Person();
}
```


---

## 類別屬性
### java的類別定義

```java
public class Person {
	private int age;
	private String name;
	public Person(String name, int age) {
	this.name = name;
	this.age = age;
	System.out.println("Person instance created");
}
public int getAge() {
	return age;
}
public void setAge(int age) {
	this.age = age;
}
public String getName() {
	return name;
}
public void setName(String name) {
	this.name = name;
} 
	
}

class Playground {
	public static void main(String[ ] args) {
		Person person = new Person("robert",28);
		System.out.println("person name:" + person.getName());
		System.out.println("person age:" + person.getAge());
	}
}
```
	
### kotlin的類別定義
* 類別使用次要建構構式
* constructor是class的次要建構式(secondary constructor)
* getter和setter由kotlin自動建立的

```kotlin
class Person {
	var name: String
	var age: Int			    
	constructor(name: String, age: Int) {
		this.name = name
		this.age = age
		print("person的實體被建立")
	} 
}

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}");
	println("person 年齡:${person.name}");
}
```
	
### kotlin使用主要建構式
* 主要建構式相對於次要建構式，是不可以有程式區塊，所以需要有init程式區 

```kotlin
class Person constructor(name:String, age:Int){
	var name: String
	var age: Int
	init {
		this.name = name
		this.age = age
		println("person的實體被建立");
	} 
}

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}");
	println("person 年齡:${person.name}");
}
```

### kotlin使用更簡潔的主要建構式
* 移除init區塊
* 將init的程式區塊移至constructor後
* 將參數直接給property

```kotlin
class Person constructor(name:String, age:Int){
	var name = name
	var age = age
}

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}");
	println("person 年齡:${person.name}");
}
```

### kotlin使用再簡潔的主要建構式
* 如果property沒有自訂的getter和setter可以在主要建構式上使用var,val
* 將會建立property，並且將參數值給property
* 可以省略主要建構式的程式區塊

```kotlin
class Person constructor(var name:String,var age:Int)

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}")
	println("person 年齡:${person.name}")
}
```

### kotlin省略主要建構式的constructor
* 如果沒有任何註釋(annotation)->@Inject
* 沒有任何修飾字(modifier)->public,private

```kotlin
class Person(var name:String,var age:Int)

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}")
	println("person 年齡:${person.name}")
}
```

### kotlin(增加可讀性)
* 將主要建構式的參數換行

```kotlin
class Person(
	var name:String,
	var age:Int
)

fun main() {
	val person = Person("robert",28);
	println("person 姓名:${person.name}")
	println("person 年齡:${person.name}")
}
```

---

## 可讀寫屬性vs唯讀屬性
### 使用var 和 val
* **var** name屬性是可讀寫
* **val** age屬性是只能讀

```kotlin
fun main() {
	class Person(
		var name: String,	   
		val age: Int      
	)
	
	val person = Person("Eva", 25)
	val name = person.name
	person.name = "Kate"
	val age = person.age
	person.age = 28 //錯誤,只可以讀
	}
```

### 使用var 和 val
```kotlin
fun main(){
	class Car (var speed: Double)	
	val car: Car = Car(7.4) 
	car.speed = 9.2
	val speed = car.speed
	
	val car = Car(7.0)
	println(car.speed) //prints 7.0 
	//後運算先傳出值
	car.speed++ 
	println(car.speed) //prints 8.0 
	car.speed--
	car.speed--
	println(car.speed) //prints: 6.0
}
```


---
## java和kolin整合運用
### kotlin環境呼叫java
```java
//Java class declaration
public class Fish {
	private int size;
	private boolean hungry;
	public Fish(int size, boolean isHungry) {
		this.size = size;
		this.hungry = isHungry;
	}
	public int getSize() {
		return size;
	}
	public void setSize(int size) {
		this.size = size;
	}
	public boolean isHungry() {
		return hungry;
	}
	public void setHungry(boolean hungry) {
		this.hungry = hungry;
	} 
}
```
```kotlin
//Kotlin class usage
fun main(){
	val fish = Fish(12, true)
	fish.size = 7
	println(fish.size) // Prints: 7
	fish.isHungry = true
	println(fish.isHungry) // Prints: true
}
```

### java環境呼叫kotlin
```kotlin
//Kotlin class declaration
class Fish(var size: Int, var hungry: Boolean)
```
```	java
//class usage in Java
Fish fish = new Fish(12, true);
fish.setSize(7);
System.out.println(fish.getSize());
fish.setHungry(false);
System.out.println(fish.getHungry());
```

### kotlin 呼叫 android java api
Java method access syntax    | Kotlin property access syntax 
|----------------------------|-----------------------------|
activity.getFragmentManager() | activity.fragmentManager
view.setVisibility(Visibility.GONE) | view.visibility = Visibility.GONE 
context.getResources().getDisplayMetrics().density | activity.fragmentManager                

### 有一些android java api使用is來操作

```kotlin
class MainActivity : AppCompatActivity() {
	override fun onDestroy() { 
		super.onDestroy()
		isFinishing() // method access syntax
		isFinishing // property access syntax
		finishing // error
	} 
}
```	
### kotlin沒有支援write only(setter)

```kotlin
fragment.setHasOptionsMenu(true)
fragment.hasOptionsMenu = true // Error!
```


---
## 自訂的getter和setter

### 建立一個Fruit的class
class Fruit(
	var weight: Double,
	val fresh: Boolean,
	val ecoRating: Int
)

### 建立自訂屬性的getter 和 setter
* 必需移除參數內的var
* 必需建立class body區塊

```kotlin
class Fruit(var weight: Double, val fresh: Boolean, ecoRating: Int)
{
	//propert被建立在class body內，必需要有一個初始化的值
	var ecoRating: Int = ecoRating
}
```

### 建立有預設值的property
* property被建立在class body內,必需要有一個初始化的值
* 可以使用default value

```kotlin
class Fruit(var weight: Double, val fresh: Boolean) {
	//default
	var ecoRating: Int = 3
}
```

### property在class body被建立時可以省略型別(使用推測)
	
```kotlin
class Fruit(var weight: Double, val fresh: Boolean) {
	//Int被省略
	var ecoRating = 3
}
```

	
### 透過其它屬性計算出其它屬性值
* 透透過其它屬性計算出其它屬性值
* 不同的重量建立不同的ecoRating值

```kotlin
class Apple(var weight: Double, val fresh: Boolean) {
	var ecoRating: Int = when(weight) {
		in 0.5..2.0 -> 5
		in 0.4..0.5 -> 4
		in 0.3..0.4 -> 3
		in 0.2..0.3 -> 2
		else -> 1
	}
}
```	

### 建立屬性get()和set(value)
* 在get()和set(value)內使用field，代表這個property
* 有自訂的getter和setter，要使用var

```kotlin
class Fruit(var weight: Double) {
	var ecoRating: Int = 3
	get() {
		println("getter value retrieved")
		return field //使用field 代表自已這個property
	}
	set(value) {
		field = if (value < 0) 0 else value
		println("setter new value assigned $field")
	}
}

fun main(){
	val fruit = Fruit(12.0)
	val ecoRating = fruit.ecoRating
	// Prints: getter value retrieved
	fruit.ecoRating = 3;
	// Prints: setter new value assigned 3
	fruit.ecoRating = -5;
	// Prints: setter new value assigned 0	
}
```
	

### 使用val和get()建立read-only的屬性
* heavy沒有真的值儲存，只是單獨計算

```kotlin
class Fruit(var weight: Double) {
	val heavy
	get() = weight > 20
}
//usage
var fruit = Fruit(7.0)
println(fruit.heavy) //prints: false
fruit.weight = 30.5
println(fruit.heavy) //prints: true
```

### 計算屬性
* crashed沒有實際儲存值

```kotlin
class Car {
	var usable: Boolean = true 
	var inGoodState: Boolean = true
	//crashed property沒有field,因為是計算所得的
	var crashed: Boolean 		
	get() = !usable && !inGoodState 	
	set(value) { 
		usable = false 
		inGoodState = false 
	}
}
```

---
## 延遲初始化的屬性(lateinit)
* 我們知道有一個屬性將不會是null,但一開始不會有值,在初始化後一定會有值

### 一個android範例屬性button延後給值(不切實際的方法)


```kotlin
class MainActivity : AppCompatActivity() {
	private var button: Button? = null
	override fun onCreate(savedInstanceState: Bundle?) {
	   super.onCreate(savedInstanceState)
	   button = findViewById(R.id.button) as Button
	}
}
```
	

### 一個android範例屬性button延後給值(正確的使用方法)
* 必需是var
* 必需是non-nullable
*不行是primitive type

```kotlin
class MainActivity : AppCompatActivity() {
	private lateinit var button: Button
	override fun onCreate(savedInstanceState: Bundle?) {
		button = findViewById(R.id.button) as Button
		button.text = "Click Me"
	} 
}
```


---
## inline 屬性

```kotlin
//inline是為了提升效能
//限制只可以使用在沒有backing filed的property

inline val now:Long
 get() { 
 println("Time retrieved") 
 return System.currentTimeMillis() 
}
```
	
### inline compiler完後的bytecode
```kotlin
println("Time retrieved") 
return System.currentTimeMillis() 
```

## 9 constructors(建構式)
### kotlin允許不用有任何的建構式
```kotlin
class Fruit(val weight:Int)
```
	
### 一個主要建構式加上多個次要建構式, 次要建構式一定要委派給主要(this(weight))
```
//---------錯誤的-----
//fresh是區域變數，不是property
class Fruit1(val weight:Int){
	constructor(weight:Int, fresh:Boolean):this(weight){
		val fresh = fresh
	}
}
//-----------------

//--------正確的-----
class Fruit(val weight: Int) {
	constructor(weight: Int, fresh: Boolean) : this(weight) { }
}
//class instantiation
val fruit1 = Fruit(10)
val fruit2 = Fruit(10, true)
```

### 次要建構式內不可以建立屬性，一定要在類別的body區建立, 如果使用主建構式，fresh屬性一定要有值,

```kotlin
class Fruit(val weight: Int) {
	var fresh: Boolean? = null
	//define fresh property in class body
	constructor(weight: Int, fresh: Boolean) : this(weight) {
		this.fresh = fresh
		//assign constructor parameter to fresh property
	}
 }

val fruit = Fruit(10)
println(fruit.weight) // prints: 10
println(fruit.fresh) // prints: null
```
	

### 如果要fresh是non-nullable,必需提供default value
	
```kotlin
class Fruit(val weight: Int) {
	var fresh: Boolean = true
	constructor(weight: Int, fresh: Boolean) : this(weight) {
		this.fresh = fresh
	} 
}
val fruit = Fruit(10)
println(fruit.weight) // prints: 10
println(fruit.fresh) // prints: true
```
	
### 當有主要建構式，次要建構式一定要call主要建構式(明確的)，(不明確的)次建構式呼叫其它次建構式
```kotlin
class Fruit(val weight: Int) {
	val fresh:Boolean = false;
	var color:String = "red";
	constructor(weight: Int, fresh: Boolean) : 
		this(weight) // 明確的
	constructor(weight: Int, fresh: Boolean, color: String) :
		this(weight, fresh) // 不明確的
}
```


### 如果沒有主要建構式但有父類別，必需使用super()呼叫父類別的建構式
```kotlin
class ProductView : View {
	constructor(ctx: Context) : super(ctx)
	constructor(ctx: Context, attrs : AttributeSet) :
		super(ctx, attrs)
}
```

### default是public,有private,protected必需要有constructor()
```kotlin
class Fruit private constructor()
```
	
### 有annotation也必需明確的有constructor()
```kotlin
class Fruit @Inject constructor()
```

### 有annotation和visibility modifier
```
class Fruit @Inject private constructor {
	var weight: Int? = null
}
```
### property對constructor parameter

### 有val,var是類別實體屬性,沒有就是建構式參數
```kotlin
class Fruit(var weight:Double, fresh:Boolean)

fun main(){
	val fruit = Fruit(12.0, true)
	println(fruit.weight)
	// fresh是constructor parameter
	//println(fruit.fresh) error,不是property
}
```
	

Class declaration  | Getter generated | Setter generated | Type
------------- | ------------- | --------- | ------
class Fruit(name:String) | NO | NO | Constructor parameter
class Fruit (val name:String)  | YES | NO | Property
class Fruit (var name:String) | YES | YES | Property

## Constructor with default arguments(建構式使用預設引數值)

### 有val,var是類別實體屬性,沒有就是建構式參數
```kotlin
class Fruit(var weight:Double, fresh:Boolean)
val fruit = Fruit(12.0, true)
println(fruit.weight)
println(fruit.fresh) // error
```
	
### 有default value
	
```kotlin
package lesson3_11

class Fruit(var weight:Int=0, var fresh:Boolean=true, val color:String="green")

fun main(){
	val fruit = Fruit()
	println(fruit.weight)
	println(fruit.fresh)
	println(fruit.color)

	val fruit1 = Fruit(7, false)
	println(fruit1.weight)
	println(fruit1.fresh)
	println(fruit1.color)

	val fruit2 = Fruit(weight = 7, color = "Yellow", fresh = true)
	println(fruit2.weight)
	println(fruit2.fresh)
	println(fruit2.color)
}	
```
<br/><br/>
--- 
# Inheritance繼承
### 明確宣告繼承和不明確宣告繼承

- kotlin的原始父類別為Any,java的原始父類別為object。所有kotlin的類別預設皆繼承Any  
  
- kotlin就像java一樣，只支援單一繼承，所以每個類別只可以有一個父類別。但是可以實作多個介面


### 明確宣告繼承和不明確宣告繼承

- class Plant // 不明確宣告繼承Any

- class Plant : Any // 不明確宣告繼承Any


### 預設class是final不能繼承, method也是final不能override

- 不同於java, kotlin的每個class和method，預設是final


```kotlin
class Plant
class Tree : Plant() // 繼承錯誤,kotlin的class預設是final
```

### final的相反是open

- kotlin的繼承是使用冒號字元.java是使用extends or implements
- 
```kotlin
- open class Plant
- class Tree : Plant()
```

### final method不可以override

```kotlin
//class明確使用open才可以被繼承
open class Plant {
	var height: Int = 0
	fun grow(height: Int) {}
}

class Tree : Plant() {
	override fun grow(height: Int) { // 出錯:Plant內的fun grow預設是final 
		this.height += height
	}
}
```	

### 可以override

```kotlin
open class Plant {
	 var height: Int = 0
	 open fun grow(height: Int) {}
 }
 
class Tree : Plant() {
	  override fun grow(height: Int) {
	      this.height += height
	  }
}
```

### 可以override height屬性

```kotlin
open class Plant {
	open var height: Int = 0
	open fun grow(height: Int) {}
}

class Tree : Plant() {
	override var height: Int = super.height
	get() = super.height
	set(value) { field = value}
	
	override fun grow(height: Int) {
		this.height += height
	} 
}
```

### 使用final

```kotlin
open class Plant {
	var height: Int = 0
	open fun grow(height: Int) {}
}

open class Tree : Plant() { //class 的open要明確的宣告
	//使用final關閉open,如果沒有宣告,未來所有繼承的子類別都可以override
	final override fun grow(height: Int) { 
		this.height += height
	}
}

class Oak : Tree() { //
	// 不行再override fun grow
}
```

### abstract class,method

- 抽象類別不充許實體化，只可以被繼承。預設自已是open，裏面所有的member預設也是open
- 抽象method不充許實作body。只充許子類別使用override實作

```kotlin
abstract class Plant {
	var height: Int = 0
	abstract fun grow(height: Int)
}
class Tree : Plant() {
	override fun grow(height: Int) {
		this.height += height
	}
}

val plant = Plant() // 錯誤:抽象類別不可以被實體化
val tree = Tree()
```	      
### data class
- 使用data class會讓kotlin的compiler自動幫class產一些methods(equals,hasCode,toString,copy,componentN)
- data class不可以是inner,abstract,sealed class

```kotlin
data class Product(var name:String, var price:Double)


fun main(){
	val productA = Product("spoon",30.2)
	val productB = Product("spoon",30.2)
	val productC = Product("Fork",17.4)

	println(productA == productA)  // prints: true
	println(productA == productB)  // prints: true
	println(productA == productC)  // prints: false
	println(productA) //Product(name=Spoon, price=30.2)
	println(productC) // Product(name="Fork",price=17.4)		
}
```

- copy

```kotlin
data class Product(var name:String, var price:Double)


fun main(){
	val productA = Product("spoon",30.2)
	val productB = Product("spoon",30.2)
	val productC = Product("Fork",17.4)

	val productA = Product("Spoon", 30.2) 
	print(productA) // prints: Product(name=Spoon, price=30.2)
	
	val productB = productA.copy() 
	print(productB) // prints: Product(name=Spoon, price=30.2)
	
	val productB = Product(productA)			
}
```

- Mutable object - modify object state

```kotlin
data class Product(var name:String, var price:Double)
var productA = Product("Spoon", 30.2) 
productA.name = "Knife"
```
- Immutable object
```kotlin
Product(val name:String, val price:Double)
var productA = Product("Spoon", 30.2) 
productA = productA.copy(name = "Knife")
```

# Destructive declaration 拆解的宣告

## data class 的拆解宣告
- 將物件的property拆解出來成為變數

```kotlin
data class Person(val firstName: String, val lastName: String,val height: Int)
val person = Person("Igor", "Wojda", 180)
var (firstName, lastName, height) = person
println(firstName) // prints: "Igor"
println(lastName) // prints: "Wojda"
println(height) // prints: 180
```

### 使用componentN()拆解

```kotlin
val person = Person("Igor", "Wojda", 180)
var firstName = person.component1()
var lastName = person.component2()
var height = person.component3()
```
	

### 使用底線省略
	
```kotlin
val person = Person("Igor", "Wojda", 180)
var (firstName, _, height) = person
println(firstName) // prints: "Igor"
println(height) // prints: 180
```
	
### 拆解字串
```kotlin
val file = "MainActivity.kt"
val (name, extension) = file.split(".", limit = 2)
```
	
### 拆解和for一起使用
```kotlin
val authors = listOf(
	       Person("Igor", "Wojda", 180),
	       Person("Marcin", "Moskała", 180)
)
println("Authors:")
for ((name, surname) in authors) {
	 println("$name $surname")
}
```

# Operator overloading運算子覆載

- 內建方法呼叫，取代運算子

| operatior token | corresponding method |
| ----------- | ------------- |
| a + b | a.plus(b) |
| a - b | a.minus(b) |
| a * b | a.times(b) |
| a / b | a.div(b) |
| a % b | a.rem(b) |
| a..b | a.rangeTo(b) |
| a += b | a.plusAssign(b) |
| a -= b | a.minusAssign(b) |
| a *= b | a.timesAssign(b) |
| a /= b | a.divAssign(b) |


```kotlin
data class Point(var x: Double, var y: Double) {
	operator fun plus(point: Point) = Point(x + point.x, y+ point.y)
	operator fun times(other: Int) = Point(x * other, y * other)
}

//usage
var p1 = Point(2.9, 5.0)
var p2 = Point(2.0, 7.5)
println(p1 + p2)     // prints: Point(x=4.9, y=12.5)
println(p1 * 3)      // prints: Point(x=8.7, y=15.0)
```

### 也可以這樣寫

```kotlin
p1.plus(p2)
p1.times(3)
```

### 運算子沒有繼承，可以overload
- 運算子method不是override父類別的運算子，所以沒有固定的參數和資料類型。而是overload. 只需要對應的運算子method名稱和前面加一個關鍵字operator
- 事實上，我們也可以定義多個相同的運算子method，但使用不同的參數類型

```kotlin
data class Point(var x: Double, var y: Double) {
	operator fun plus(point: Point) = Point(x + point.x, y +point.y)
	operator fun plus(vector:Double) = Point(x + vector, y + vector)
}
var p1 = Point(2.9, 5.0)
var p2 = Point(2.0, 7.5)

//compiler可以自動找適合的overload的運算子
println(p1 + p2) // prints: Point(x=4.9, y=12.5)
println(p1 + 3.1) // prints: Point(x=6.0, y=10.1)

```

### 如果有定義 + 運算子method, 則就同的支援 += 組合運算子method

```kotlin
	var p1 = Point(2.9, 7.0)
	var p2 = Point(2.0, 7.5)
	p1 += p2
	println(p1) // prints: Point(x=4.9, y=14.5)
```

### 會錯誤
- 同時定義 plus and plus method , 並且使用相的的參數類型將會出錯

```kotlin
data class Point(var x:Double, var y:Double){
	init{
	   println("PLoint created $x.$y");
	}
	
	operator fun plus(point:Point) = Point(x + point.x, y + point.y);
	operator fun plusAssign(point:Point){
	   x += point.x;
	   y += point.y;
	}
}
   
var p1 = Point(2.9, 7.0);
var p2 = Point(2.0, 7.5);
val p3 = p1 + p2;
println("$p1, $p2, $p3");
//p1 += p2 ;錯誤
```

### 使用 object declarations 定義singleton的 class 簡單好用
- object declarations是lazy initialize
- 它可以巢狀在其它的object declaration內或 non-inner class - 
- 它們不可以指定給變數

```kotlin
object SQLiteSingleton {
	fun getAllUsers(): List<Int> { 
	 return listOf(3, 4, 5, 6)
	}
}

fun main() {
    print(SQLiteSingleton.getAllUsers())
}
```
---
# Object expression(暱名class)
- Object expression 等同是 Java's anonymous class
```kotlin
//java
ServiceConnection serviceConnection = new ServiceConnection() {
	@Override
	public void onServiceDisconnected(ComponentName name) {
	...
	}
	@Override
	public void onServiceConnected(ComponentName name,IBinder service){
	... 
	}

}

//kotlin
val serviceConnection = object: ServiceConnection {
	     override fun onServiceDisconnected(name: ComponentName?) { }
	     override fun onServiceConnected(name: ComponentName?, service: IBinder?) { }
}
```
	
### 使用object expression
- 快速建立一個暱名class並且立刻建一個實體

```kotlin
interface Player {
	fun play()
}

fun playWith(player: Player) {
	print("I play with")
	player.play()
}

open class VideoPlayer {
	fun play() {
	    println("Play video")
	}
}

//object被建立於暱名class，這暱名class繼承VideoPlayer和實作Player介面

val player = object: VideoPlayer(), Player { }
playWith(player)
```
	
### 使用object expression 快速建立暱名class繼承Any
- 快速建立一個實體，有自訂property和自訂的method(無法使用java,因為java一定要有一個自訂的interface)

```kotlin

fun main(){
	val data = object{
		var size = 1
		fun update(){
			print("update的size是$size")
		}		
	}
	
	data.size = 2
	data.update()
}
```
	
### 有自訂interface, java才可以使用

```kotlin
open class VideoPlayer {
	fun play() {
		println("Play video")	
}
interface Player{
	fun play()
	fun stop() 
}
//usage
val player = object: VideoPlayer(), Player {
	var duration:Double = 0.0
	fun stop() {
		println("Stop  video")
	} 
}
player.play() // println("Play video")
player.stop() // println("Stop  video")
player.duration = 12.5
```
   