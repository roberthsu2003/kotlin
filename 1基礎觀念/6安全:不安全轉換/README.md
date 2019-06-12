# 安全/不安全轉型運算(safe/unsafe cast operator)

### kotlin的2種轉換
> 明確轉換到不同類型->安全轉換運算子(safe cast operator)  
> 轉換到不同類型或nullable 轉換到 non-nullable -> 智慧型轉換機制(smart cast mechanism)

	//java
	Fragment fragment = new ProductFragment();
	ProductFragment productFragment = (ProductFragment) fragment;

### 不安全轉換運算子 as
	val fragment: Fragment = ProductFragment()
	val productFragment: ProductFragment =  fragment as ProductFragment

### 不安全轉換造成錯誤
	val fragment : String = "ProductFragment"
	val productFragment : ProductFragment =  fragment as ProductFragment
	\\ 錯誤例外 Exception: ClassCastException
	
### 安全轉換(nullable cast) as?
	val fragment: String = "ProductFragment"
	val productFragment: ProductFragment? =  fragment as? ProductFragment

### 也可使用不安全轉換成為安全轉換
	val fragment: String = "ProductFragment"
	val productFragment: ProductFragment? =  fragment as ProductFragment?

### 也可以配合Elvis operator
	val fragment: String = "ProductFragment"
	val productFragment: ProductFragment = fragment as? ProductFragment ?: ProductFragment()
	
```
不安全轉換(as):轉換失敗會丟出ClassCastException
安全轉換(as?):轉換失敗傳出null
```

### android應用
	var productFragment: ProductFragment? = supportFragmentManager.findFragmentById(R.id.fragment_product) as? ProductFragment
	
### 原生型別轉換可使用內建方法
	val name: String
	val age: Int = 12
	name = age.toString(); // Converts Int to String


