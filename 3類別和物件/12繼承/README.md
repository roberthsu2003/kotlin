# 繼承

### 明確宣告和不明確宣告
	class Plant // Implicitly extends Any
	class Plant : Any // Explicitly extends Any
	

### 預設class是final-不能繼承, method也是final-不能override
	class Plant
	class Tree : Plant() // Error

### final的相反是open
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
	            final override fun grow(height: Int) {
	                this.height += height
	            }
	}
	        class Oak : Tree() {
	            // 1
	}


### abstract class,method
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
	  