# 類別的陪同物件

###語法
	class ProductDetailsActivity {
	            companion object {
	            } 
	}


###實作
	//ProductDetailsActivity.kt
	        class ProductDetailsActivity : AppCompatActivity() {
	            override fun onCreate(savedInstanceState: Bundle?) {
	                super.onCreate(savedInstanceState)
	                val product = intent.getParcelableExtra<Product>
	                    (KEY_PRODUCT) // 3
	                //...
	            }
	            companion object {
	                const val KEY_PRODUCT = "product" // 1
	                fun start(context: Context, product: Product) { // 2
	                    val intent = Intent(context,
	                        ProductDetailsActivity::class.java)
	                    intent.putExtra(KEY_PRODUCT, product) // 3
	                    context.startActivity(intent)
	                 } 
	        }
	}
	        // Start activity
	        ProductDetailsActivity.start(context, productId) // 2
###        
	class Car(var count:Int) {
	            init {
	                count++; 
	             }
	            companion object {
	                var count:Int = 0	                
	            }
	}
	
	println(Car.count) // Prints 0
	Car()
	Car()
	println(Car.count) // Prints: 2