# 9建構式
### 主要建構式加上次要建構式, 次要建構式一定要委派給主要(this(weight))
	class Fruit(val weight: Int) {
	            constructor(weight: Int, fresh: Boolean) : this(weight) { }
	}
	        //class instantiation
	        val fruit1 = Fruit(10)
	        val fruit2 = Fruit(10, true)

### 次要不可建立屬性，一定要在類別的body區建立, 如果使用主建構式，fresh屬性一定要有值,

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
	

### fresh也可以是non-nullable
	class Fruit(val weight: Int) {
	            var fresh: Boolean = true
	            constructor(weight: Int, fresh: Boolean) : this(weight) {
	                this.fresh = fresh
	            } 
	}
	val fruit = Fruit(10)
	println(fruit.weight) // prints: 10
	println(fruit.fresh) // prints: true
	
### 當有主要建構式，次要建構式一定要call主要建構式
	class Fruit(val weight: Int) {
           val fresh:Boolean = false;
    	      var color:String = "red";
	        constructor(weight: Int, fresh: Boolean) : this(weight) // 1
	        constructor(weight: Int, fresh: Boolean, color: String) :
	                    this(weight, fresh) // 2
	}


### 如果沒有主要建構式，父類別有建構式，必需使用super()
	class ProductView : View {
	       constructor(ctx: Context) : super(ctx)
	       constructor(ctx: Context, attrs : AttributeSet) :
	                   super(ctx, attrs)
	}

### default是public,有private,protected必需要有constructor()
	class Fruit private constructor()
	
### 有annotation
	class Fruit @Inject constructor()

### 有annotation和modifier
	class Fruit @Inject private constructor {
	            var weight: Int? = null
	}