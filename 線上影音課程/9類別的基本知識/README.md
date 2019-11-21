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

## 可讀寫屬性vs唯讀屬性
### 使用var 和 val
	fun main() {
	    class Person(
	            var name: String,
	            // Read-write property (generated getter and setter)
	            val age: Int      // Read-only property (generated getter)
	        )
	        //usage
	        val person = Person("Eva", 25)
	        val name = person.name
	        person.name = "Kate"
	        val age = person.age
	        person.age = 28 //error: read-only property
	}

### 
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
