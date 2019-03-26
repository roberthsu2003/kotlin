# 遞增運算子和遞減運算子
### 使用 ++ 和 --
	++speed //pre increment再傳出值
	--speed //pre decrement
	speed++ //先傳出值後post increment
	speed-- //先傳出值後post decrement

### 先運算再傳出值
	var speed = 1.0
	println(++speed) // Prints: 2.0
	println(speed)   // Prints: 2.0

### 先傳出值後運算
	var speed = 1.0
	println(speed++) // Prints: 1.0
	println(speed) // Prints: 2.0

### kotlin 環境呼叫java
	//Java class declaration
	        public class Fish {
	            private int size;
	            private boolean hungry;
	            public Fish(int size, boolean isHungry) {
	                this.size = size;
	                this.hungry = isHungry;
	}
	            public int getSize() {
	                return size;
	}
	            public void setSize(int size) {
	                this.size = size;
	}
	            public boolean isHungry() {
	                return hungry;
	}
	            public void setHungry(boolean hungry) {
	                this.hungry = hungry;
	} }

	//Kotlin class usage
	        val fish = Fish(12, true)
	        fish.size = 7
	        println(fish.size) // Prints: 7
	        fish.isHungry = true
	        println(fish.isHungry) // Prints: true

### kotlin 環境呼叫java
	//Kotlin class declaration
		class Fish(var size: Int, var hungry: Boolean)
		
	//class usage in Java
		Fish fish = new Fish(12, true);
		fish.setSize(7);
		System.out.println(fish.getSize());
		fish.setHungry(false);
		System.out.println(fish.getHungry());

### kotlin 呼叫 android java api
Java method access syntax                                  | Kotlin property access syntax           |
-----------------------------------------------------------|-----------------------------------------|
activity.getFragmentManager()                              | activity.fragmentManager                |
view.setVisibility(Visibility.GONE)                        | view.visibility = Visibility.GONE       |
context.getResources().getDisplayMetrics().density         | activity.fragmentManager                |

### 有一些android java api使用is來操作

	class MainActivity : AppCompatActivity() {
	            override fun onDestroy() { // 1
	                super.onDestroy()
	                isFinishing() // method access syntax
	                isFinishing // property access syntax
	                finishing // error
	} }
	
	
### kotlin沒有支援write only(setter)
	fragment.setHasOptionsMenu(true)
	fragment.hasOptionsMenu = true // Error!