# 9 constructors(建構式)
### kotlin允許不用有任何的建構式
	class Fruit(val weight:Int)
	
### 一個主要建構式加上多個次要建構式, 次要建構式一定要委派給主要(this(weight))
	//---------錯誤的-----
	//fresh是區域變數，不是property
	class Fruit1(val weight:Int){
    constructor(weight:Int, fresh:Boolean):this(weight){
        val fresh = fresh
	}
	//-----------------
	
	//--------正確的-----
	class Fruit(val weight: Int) {
	            constructor(weight: Int, fresh: Boolean) : this(weight) { }
	}
	 //class instantiation
	  val fruit1 = Fruit(10)
	  val fruit2 = Fruit(10, true)

### 次要建構式內不可以建立屬性，一定要在類別的body區建立, 如果使用主建構式，fresh屬性一定要有值,

	class Fruit(val weight: Int) {
	            var fresh: Boolean? = null
	            //define fresh property in class body
	            constructor(weight: Int, fresh: Boolean) : this(weight) {
	                this.fresh = fresh
	                //assign constructor parameter to fresh property
	            }
	 }

	val fruit = Fruit(10)
	println(fruit.weight) // prints: 10
	println(fruit.fresh) // prints: null
	

### 如果要fresh是non-nullable,必需提供default value
	class Fruit(val weight: Int) {
	            var fresh: Boolean = true
	            constructor(weight: Int, fresh: Boolean) : this(weight) {
	                this.fresh = fresh
	            } 
	}
	val fruit = Fruit(10)
	println(fruit.weight) // prints: 10
	println(fruit.fresh) // prints: true
	
### 當有主要建構式，次要建構式一定要call主要建構式(明確的)，(不明確的)次建構式呼叫其它次建構式
	class Fruit(val weight: Int) {
           val fresh:Boolean = false;
    	      var color:String = "red";
	        constructor(weight: Int, fresh: Boolean) : this(weight) // 明確的
	        constructor(weight: Int, fresh: Boolean, color: String) :
	                    this(weight, fresh) // 不明確的
	}


### 如果沒有主要建構式但有父類別，必需使用super()呼叫父類別的建構式
	class ProductView : View {
	       constructor(ctx: Context) : super(ctx)
	       constructor(ctx: Context, attrs : AttributeSet) :
	                   super(ctx, attrs)
	}

### default是public,有private,protected必需要有constructor()
	class Fruit private constructor()
	
### 有annotation也必需明確的有constructor()
	class Fruit @Inject constructor()

### 有annotation和visibility modifier
	class Fruit @Inject private constructor {
	            var weight: Int? = null
	}