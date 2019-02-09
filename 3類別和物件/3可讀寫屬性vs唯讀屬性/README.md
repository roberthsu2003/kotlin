# 可讀寫屬性vs唯讀屬性
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

