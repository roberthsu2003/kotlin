# Inheritance繼承
~~~
* kotlin的原始父類別為Any,java的原始父類別為object。所有kotlin的類別預設皆繼承Any  
   
* kotlin就像java一樣，只支援單一繼承，所以每個類別只可以有一個父類別。但是可以實作多個介面
~~~

### 明確宣告繼承和不明確宣告繼承
	class Plant // Implicitly extends Any
	class Plant : Any // Explicitly extends Any
	

### 預設class是final-不能繼承, method也是final-不能override
~~~
* 不同於java, kotlin的每個class和method，預設是final
~~~
	class Plant
	class Tree : Plant() // Error

### final的相反是open
~~~
* kotlin的繼承是使用冒號字元.java是使用extends or implements
~~~

	open class Plant
	class Tree : Plant()

### final method不可以override
	open class Plant {
	           var height: Int = 0
	           fun grow(height: Int) {}
	}
	class Tree : Plant() {
	      override fun grow(height: Int) { // Error
	            this.height += height
	      }
	}
	
### 可以override
	open class Plant {
	     var height: Int = 0
	     open fun grow(height: Int) {}
	 }
	 
	class Tree : Plant() {
	      override fun grow(height: Int) {
	          this.height += height
	      }
	}

### 可以override height屬性
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

### 使用final
	open class Plant {
	            var height: Int = 0
	            open fun grow(height: Int) {}
	        }
	        class Tree : Plant() {
	            //使用final關閉open
	            final override fun grow(height: Int) {
	                this.height += height
	            }
	}
	        class Oak : Tree() {
	            // 1
	}


### abstract class,method
~~~
抽象類別不充許實體化，只可以被繼承。預設自已是open，裏面所有的member預設也是open
抽象metho不充許實作body。只充許子類別使用override實作
~~~
	abstract class Plant {
	            var height: Int = 0
	            abstract fun grow(height: Int)
	        }
	        class Tree : Plant() {
	            override fun grow(height: Int) {
	                this.height += height
	            }
	        }
	        val plant = Plant()
	        // error: abstract class can't be instantiated
	        val tree = Tree()
	  