### abstract class,method

- 抽象類別不充許實體化，只可以被繼承。預設自已是open，裏面所有的member預設也是open
- 抽象method不充許實作body。只充許子類別使用override實作

```kotlin
abstract class Plant {
	var height: Int = 0
	abstract fun grow(height: Int)
}
class Tree : Plant() {
	override fun grow(height: Int) {
		this.height += height
	}
}

val plant = Plant() // 錯誤:抽象類別不可以被實體化
val tree = Tree()
```	      
