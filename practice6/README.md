# ch06 類別和物件

> 類別的定義

### Person.java
> java的類別定義

	class Person{
	    
	}
	
	class Playground {
	    public static void main(String[ ] args) {
	       Person person = new Person();
	    }
	}

### Person.kt
> kotlin的類別定義

	class Person;
	
	fun main() {
	    val person = Person();
	}

### Playground.java
> java的類別定義，包含2個field，一個建構式和2個private field的getter和setter


	 class Person {
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
		
		public class Playground {
		    public static void main(String[ ] args) {
		       Person person = new Person("robert",28);
		       System.out.println("person name:" + person.getName());
		       System.out.println("person age:" + person.getAge());
		    }
		}

### PlayGround.kt
> kotlin的類別定義，包含2個property，一個次要建構式   
> property的getter和setter由compiler自動建立

	class Person{
	    var name:String
	    var age:Int
	
	    constructor(name:String, age:Int){
	        this.name = name
	        this.age = age
	        print("person的實體被建立")
	    }
	}
	fun main(){
	    val person = Person("robert", 28)
	    println("person 姓名:${person.name}")
	    println("preson 年齡:${person.age}")
	}

### PlayGround1.kt
> kotlin的類別定義，包含2個property  
> 使用主要建構式   
> 主要建構式不可以有程式區塊，必需建立init程式區塊   
> property的getter和setter由compiler自動建立 

	class Person1 constructor(name:String, age:Int){
	    var name:String
	    var age:Int
	
	    init {
	        this.name = name
	        this.age = age
	    }
	}
	
	fun main(){
	    val person1 = Person1("robert", 28)
	    println("person 姓名:${person1.name}")
	    println("preson 年齡:${person1.age}")
	}


### PlayGround2.kt
> kotlin的類別定義，包含2個property  
> 使用主要建構式   
> 不使用init程式區塊，直接在default value時給值   
> property的getter和setter由compiler自動建立 

	class Person2 constructor(name:String, age:Int){
	    var name:String = name
	    var age:Int = age
	}
	
	fun main(){
	    val person2 = Person2("robert", 28)
	    println("person 姓名:${person2.name}")
	    println("preson 年齡:${person2.age}")
	}

### PlayGround3.kt
> 如果property沒有自訂的getter和setter,可以在主建構式內定義 

	class Person3 constructor(var name:String, var age:Int)
	fun main(){
	    val person2 = Person2("robert", 28)
	    println("person 姓名:${person2.name}")
	    println("preson 年齡:${person2.age}")
	}

	//如果沒有修飾字public,private ..或沒有標示@inject
	class Person3 (var name:String, var age:Int)
	
	class Person3 (
    var name:String,
    var age:Int)
    
### ReadWriteProperty.kt
> property的可讀寫
> property的read-only 

	class Person4(
	    var name:String, //自動產生getter和setter
	    val age:Int //只有產生setter
	)
	
	fun main(){
	    val person = Person4("Eva", 25)
	    val name = person.name
	    person.name = "Kate"
	
	    val age = person.age
	    // person.age = 28 ->錯誤，沒有setter
	}


### java and Kotlin

	//Fish.java
	//要建立package資料夾  
	

	package com;
	
	public class Fish {
	    private int size;
	    private boolean hungry;
	
	    public Fish(int size, boolean isHungry){
	        this.size = size;
	        this.hungry = isHungry;
	    }
	
	    public int getSize(){
	        return  size;
	    }
	
	    public void setSize(int size){
	        this.size = size;
	    }
	
	    public boolean isHungry(){
	        return hungry;
	    }
	
	    public void setHungry(boolean hungry){
	        this.hungry = hungry;
	    }
	}

	//JavaKotlin.kt
	//要import com.Fish
	
	import com.Fish
	
	fun main(){
	    val fish = Fish(12, true)
	    fish.size = 7
	    println(fish.size)
	    fish.isHungry = true;
	    println(fish.isHungry)
	}


### kotlin and Java
	//Fish.kt
	//建立package com.kotlin
	package com.kotlin
	
	class Fish(var size:Int, var hungry:Boolean)

	//KotlinJava.java
	//要import com.kotlin.Fish
	import  com.kotlin.Fish;
	
	public class KotlinJava {
	    public static void main(String[] args){
	        Fish fish = new Fish(12, true);
	        fish.setSize(7);
	        System.out.println(fish.getSize());
	        fish.setHungry(false);
	        System.out.println(fish.getHungry());
	    }
	}

### GetterSetter.kt
	//compiler自動建立getter和setter
	class Fruit(
	    var weight:Double,
	    val fresh:Boolean,
	    val ecoRating:Int)
	 
	
	//使用建構式建立ecoRating的值	
	class Fruit(var weight:Double, val fresh:Boolean, ecoRating:Int){
	    var ecoRating:Int = ecoRating
	}
	
	
	//ecoRating使用預設值	
	class Fruit(var weight:Double, val fresh:Boolean){
	    var ecoRating:Int = 3
	}
	
	
	//ecoRating的值，可以由其計算其它值而取得
	class Fruit(var weigth:Double, val fresh:Boolean){
	    var ecoRating :Int = when(weigth){
	        in 0.5..2.0 -> 5
	        in 0.4..2.0 -> 4
	        in 0.3..0.4 -> 2
	        else -> 1
	    }
	}
	
	
	//自訂的getter和setter
	class Fruit(var weight:Double){
	    var ecoRating:Int = 3
	    get() {
	        println("getter正在傳出值")
	        return  field
	    }
	    set(value){
	        field = if (value < 0) 0 else value
	        println("設定完value後的新值是$field")
	    }
	}
	
	fun main(){
	    val fruit = Fruit(12.0)
	    val ecoRating = fruit.ecoRating
	    fruit.ecoRating = 3
	    fruit.ecoRating = -5
	}
	


### Constructors.kt
	class Fruit(val weight:Int){
	    var fresh:Boolean? = null;
	    //次要建構式可以以建立property
	    //使用this(weight)作為委派給主要
	    constructor(weight: Int, fresh:Boolean):this(weight){
	        this.fresh = fresh
	    }
	}
	
	//也可以指定fresh有default值
	class Fruit(val weight:Int){
    var fresh:Boolean = true    
    constructor(weight: Int, fresh:Boolean):this(weight){
        this.fresh = fresh
    }
	}
	//所有次要建構式，最後一定要呼叫主要建構式
	class Fruit(val weight:Int){
    var fresh:Boolean = true
    var color:String = "blue"
    
    constructor(weight: Int, fresh:Boolean):this(weight){
        this.fresh = fresh
     }
    
    constructor(weight: Int, fresh:Boolean,color:String):this(weight,fresh){
        this.color = color
     }
	}
	
	fun main(){
	    val fruit = Fruit(10)
	    println(fruit.weight)
	    println(fruit.fresh)
	
	}

### 有val,var是類別實體屬性,沒有就是建構式參數
	class Fruit(var weight:Double, fresh:Boolean)
	val fruit = Fruit(12.0, true)
	println(fruit.weight)
	println(fruit.fresh) // error


### ConstructorDefaultarguments.kt
	class Fruit(var weight:Int=0, var fresh:Boolean = true, var color:String = "Green")
	
	fun main(){
	    val fruit1 = Fruit()
	    val fruit2 = Fruit(7, false)
	    val fruit3 = Fruit(fresh = false, color = "Blue", weight = 5)
	}

###　inheritance.kt
	//所有class和method預設是final,所以代表class不可以繼承,method不可以override
	class Plant
	class Tree:Plant();//有錯
	
	//使用open來解決
	open class Plant
	class Tree:Plant()
	
	
	//method也要使用open
		open class Plant{
	    var height:Int = 0
	    open fun grow(height:Int){
	
	    }
	}
	
	class Three:Plant(){
	    override  fun grow(height:Int){
	        this.height += height
	    }
	}
	
	//property override 
	open class Plant{
    open var height:Int = 0
    open fun grow(height:Int){

     }
	}
	
	class Three:Plant(){
	    override var height:Int = super.height
	    get() = super.height
	    set(value){
	        field = value
	    }
	    override  fun grow(height:Int){
	        this.height += height
	    }
	}
	
	
		//Three要可被繼承必需加上open,而如果要關閉 grow(), 必需加上final,因為父類別是open
		open class Plant{
	     var height:Int = 0
	    open fun grow(height:Int){
	
	    }
	}
	
	open class Three:Plant(){
	
	    final override fun grow(height:Int){
	        this.height += height
	    }
	}
	
	class Oak:Three(){
	    //error
	    override fun grow(height:Int){
	        this.height += height
	    }
	}
	
	
	//抽象類別和方法只可以繼承,被override 實作
	abstract class Plant{
     var height:Int = 0
    abstract fun grow(height:Int)
	}
	
	open class Three:Plant(){
	
	    override fun grow(height:Int){
	        this.height += height
	    }
	}
	
	class Oak:Three(){
	    
	    override fun grow(height:Int){
	        this.height += height
	    }
	}
	
	
	
		//data Class, 有多幾個功能,equals,hashCode,toString,copy,componentN
		//data Class不可以是 abstract, inner和 sealed
		
		data class Product(var name:String, var price:Double)