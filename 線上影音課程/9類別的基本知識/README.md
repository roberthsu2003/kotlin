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

### 簡易constructor
	class Fruit(var weight: Double,
	             val fresh: Boolean,
	             val ecoRating: Int)

### 建立自訂getter 和 setter要使用在class body內建立
	class Fruit(var weight: Double, val fresh: Boolean, ecoRating: Int)
	    {
	        //propert被建立在class body內，必需要有一個初始化的值
	        var ecoRating: Int = ecoRating
	    }

### 建立有預設值的property
	class Fruit(var weight: Double, val fresh: Boolean) {
	           //propert被建立在class body內，必需要有一個初始化的值，也可以使用一個default value
	            var ecoRating: Int = 3
	}

### property在class body被建立時可以type(使用推測)
	class Fruit(var weight: Double, val fresh: Boolean) {
	           //Int被省略
	            var ecoRating = 3
	}

	
### 透過其它屬性計算出其它屬性值
	class Apple(var weight: Double, val fresh: Boolean) {
	            //透過其它屬性計算出其它屬性值
	            //不同的重量建立不同的ecoRating值
	            var ecoRating: Int = when(weight) {
	                in 0.5..2.0 -> 5
	                in 0.4..0.5 -> 4
	                in 0.3..0.4 -> 3
	                in 0.2..0.3 -> 2
	                else -> 1
	            }
	}
	
### 建立屬性getter和setter
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
	// Usage
	val fruit = Fruit(12.0)
	val ecoRating = fruit.ecoRating
	// Prints: getter value retrieved
	fruit.ecoRating = 3;
	// Prints: setter new value assigned 3
	fruit.ecoRating = -5;
	// Prints: setter new value assigned 0
	

### 建立read-only get
### heavy沒有真的值儲存，只是單獨計算
	class Fruit(var weight: Double) {
	          val heavy             // 1
	          get() = weight > 20
	      }
	//usage
	var fruit = Fruit(7.0)
	println(fruit.heavy) //prints: false
	fruit.weight = 30.5
	println(fruit.heavy) //prints: true

### 計算屬性
	class Car {
		var usable: Boolean = true 
		var inGoodState: Boolean = true
		//crashed property沒有field,囚為是計算所得的
		var crashed: Boolean 		
		get() = !usable && !inGoodState 	
		set(value) { 
			usable = false 
			inGoodState = false 
		}
	}


