# 巢狀類別

	class Outer {
	            private val bar: Int = 1
	            
	            class Nested {
	                fun foo() = 2
	            }
	}
	
	val demo = Outer.Nested().foo() // == 2

### inner可以我存取outter的屬性
	class Outer {
	            private val bar: Int = 1
	            
	            inner class Inner {
	                fun foo() = bar
	            } 
	}
	        val outer = Outer()
	        val demo = outer.Inner().foo() // == 1