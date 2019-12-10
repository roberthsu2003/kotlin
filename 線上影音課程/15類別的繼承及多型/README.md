# 類別的繼承和多型
### 明確宣告繼承和不明確宣告繼承

- kotlin的原始父類別為Any,java的原始父類別為object。所有kotlin的類別預設皆繼承Any  
  
- kotlin就像java一樣，只支援單一繼承，所以每個類別只可以有一個父類別。但是可以實作多個介面


### 明確宣告繼承和不明確宣告繼承

- class Plant // 不明確宣告繼承Any

- class Plant : Any // 不明確宣告繼承Any


### 預設class是final不能繼承, method也是final不能override

- 不同於java, kotlin的每個class和method，預設是final


```kotlin
class Plant
class Tree : Plant() // 繼承錯誤,kotlin的class預設是final
```

### final的相反是open

- kotlin的繼承是使用冒號字元.java是使用extends or implements
- 
```kotlin
- open class Plant
- class Tree : Plant()
```

### final method不可以override

```kotlin
//class明確使用open才可以被繼承
open class Plant {
	var height: Int = 0
	fun grow(height: Int) {}
}

class Tree : Plant() {
	override fun grow(height: Int) { // 出錯:Plant內的fun grow預設是final 
		this.height += height
	}
}
```	

### 可以override

```kotlin
open class Plant {
	 var height: Int = 0
	 open fun grow(height: Int) {}
 }
 
class Tree : Plant() {
	  override fun grow(height: Int) {
	      this.height += height
	  }
}
```

### 可以override height屬性

```kotlin
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
```

### 使用final

```kotlin
open class Plant {
	var height: Int = 0
	open fun grow(height: Int) {}
}

open class Tree : Plant() { //class 的open要明確的宣告
	//使用final關閉open,如果沒有宣告,未來所有繼承的子類別都可以override
	final override fun grow(height: Int) { 
		this.height += height
	}
}

class Oak : Tree() { //
	// 不行再override fun grow
}
```

