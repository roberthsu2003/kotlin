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

