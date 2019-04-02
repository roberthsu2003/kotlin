# 類別屬性
### java的類別定義

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
	
### kotlin的類別定義
> 類別使用次要建構構式

	class Person {
	            var name: String
				  var age: Int			    
	            constructor(name: String, age: Int) {
	                this.name = name
	                this.age = age
	                print("person的實體被建立");
				     } 
	}
	
	fun main() {
	    val person = Person("robert",28);
	    println("person 姓名:${person.name}");
	    println("person 年齡:${person.name}");
	}
	
### kotlin使用主要建構式
>主要建構式相對於次要建構式，是不可以有程式區塊，所以需要有init程式區塊

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

### kotlin使用更簡潔的主要建構式
>移除init區塊，將參數直接給property

	class Person constructor(name:String, age:Int){
	            var name = name
				var age = age
	}
	
	fun main() {
	    val person = Person("robert",28);
	    println("person 姓名:${person.name}");
	    println("person 年齡:${person.name}");
	}

### kotlin使用再簡潔的主要建構式
> 如果property沒有自訂的getter和setter可以將使用在主要建構式上使用var,val,同時建立property，並且將參數值給property

	class Person constructor(var name:String,var age:Int)
	
	fun main() {
	    val person = Person("robert",28);
	    println("person 姓名:${person.name}");
	    println("person 年齡:${person.name}")
	}

### kotlin使用再簡潔的主要建構式(不使用public,private)
	class Person(var name:String,var age:Int)
	
	fun main() {
	    val person = Person("robert",28);
	    println("person 姓名:${person.name}");
	    println("person 年齡:${person.name}");
	}

### kotlin使用再簡潔的主要建構式(不使用public,private)(增加可讀性)
	class Person(
	    var name:String,
	    var age:Int
	    )
	
	fun main() {
	    val person = Person("robert",28);
	    println("person 姓名:${person.name}");
	    println("person 年齡:${person.name}");
	}