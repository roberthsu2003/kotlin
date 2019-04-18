# internal modifier 和java bytecode

### 透過繼承overriding減弱存取控制
	open class Person{
	    protected open fun speak(){
	
	    }
	}
	
	class Student():Person(){
	    public override fun speak() {
	        super.speak()
	    }
	}
	fun main(){
	    val person = Person()
	    // person.speak(); protected只可以使用在自已class 或子類別的class內
	    val student = Student()
	    student.speak()
	}	
	
### 同時設定class和primary constructor的存取控制必需在同一行

	internal class Fruit private constructor(){
	    var weight:Double? = null
	    companion object{
	        fun create() = Fruit()
	    }
	}
	
	fun main(){
	    var fruit:Fruit? = null
	    //fruit = Fruit(); private primary constructor
	    fruit = Fruit.create()
	}

### property的getter和setter和property的存取控制相同,也可以單獨設定

	class Car{
	    init{
	        count++;
	        println("Car created")
	    }
	    companion object{
	        init{
	            println("Car companion object created")
	        }
	
	        var count:Int = 0
	            private set
	    }
	}
	
	fun main(){
	    //Car.count += 1; //private set
	    val car1 = Car()
	    val car2 = Car()
	    print(Car.count)
	}
	
	    
	    