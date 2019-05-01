# Nullability

~~~
如果定義一個type parameter,我們可以使用non-nullable,nullable的type
~~~

### 使用non-nullable的typ當作type parameter
	class Action(val name:String)
	class ActionGroup<T:Action>
	
	
	fun main(){
	
	  //non-nollable 類型當作上介限
	  
	    var actionGrounpA = ActionGroup<Action>()
	    var actionGrounpB = ActionGroup<Action?>() //錯誤
	
	}

### 如果last(),但list沒有任何東西,會crash
	class Action(val name:String)
	class ActionGroup<T:Action>(private val list:List<T>){
	    fun last():T = list.last()
	
	}
	
	
	fun main(){
	    val actionGroup = ActionGroup<Action>(listOf())
	    val action = actionGroup.last() //錯誤 crash
	    println(action.name) // 錯誤
	
	}

### 解決last()的問題,做用標準資料庫內的lastOrNull(),還是錯誤的，因為傳出來的是nullable Action
	class Action(val name:String)
	class ActionGroup<T:Action>(private val list:List<T>){
	    fun last():T = list.lastOrNull(); //T錯誤
	
	}
	
	
	fun main(){
	    val actionGroup = ActionGroup<Action>(listOf())
	    val action = actionGroup.last()
	    println(action.name)
	
	}

### 不管type argument是不是non-nullable,在內部使用時, 可以強制使用nullable,在內部使用時稱為(site-use),定義的地方稱為declaration-site

	class Action(val name:String)
	class ActionGroup<T:Action>(private val list:List<T>){ //稱為declaration-site
	    fun last():T? = list.lastOrNull(); //T改為T? //稱為user-site
	
	}
	
	
	fun main(){
	    val actionGroup = ActionGroup<Action>(listOf())
	    val action = actionGroup.last()
	    println(action?.name)
	
	}
	
### 即使用declaration-site定義nullable,在use-size一樣要強迫使用nullable type (T?)
	open class Action
	class ActionGroup<T:Action?>(private val list:List<T?>){
	    fun lastOrNull():T? = list.lastOrNull();
	
	}
	
	
	fun main(){
	    val actionGroup = ActionGroup<Action>(listOf(Action(),null))
	    print(actionGroup.lastOrNull())
	}
