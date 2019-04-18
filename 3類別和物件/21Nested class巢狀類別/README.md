# Nested class巢狀類別
### Nested就是單一個class, 優點是它是專門應用在Outer的實體, 所以寫在一起比較容易分類。可讀性高。類似於java的static nested class
	class Outer{
	    private val bar:Int = 1
	
	    class Nested{
	        fun foo() = 2
	    }
	}
	
	fun main(){
	    val demo = Outer.Nested().foo() // ==2
	}

### inner class可以我存取outter的屬性,每個Outer class 的實體都只有一個inner的實體

	class Outer{
	    private val bar: Int = 1
	
	    inner class Inner{
	        fun foo() = bar;
	    }
	}
	
	fun main(){
	    val outer = Outer()
	    val demo = outer.Inner().foo() // ==1
	}
	
|Behavior | Class(member) | inner Class|
|---------|---------------|------------|
|Behave as a Java static member|YES|NO||
| ~~~Instance of this class can exist without an instance of enclosing class | YES | NO|
|Has Reference to outer class | No | Yes|
|Share state with outer class(can access outer class members | No | YES |
|Nuber of instance | Unlimited | One per outer class instance| 