# 參數
* 必需有明確的參數名稱和類形
* 所有的參數是唯讀的   

### 可以定義和區域變數相同的參數名稱，但這是不好的習慣
		fun findDuplicates(list:List<Int>):Set<Int>{
			 var list = list.sorted();
		}

### 參數名稱和引數名稱
* 引數名稱一個真實的值，傳遞給function。
* 參數名稱是一個變數名稱，使用在定義function時  

		fun printSum(a1:Int, a2:Int){
		   print(a1 + a2);
		}
		
		add(3,5)
		
### 多個參數名稱

	fun printSum(a1:Int, a2:Int){
	   val sum = a + b
	   print(sum)
	}
	
### 引數可以使用參數定義時的子類別
	fun main() {
	    presentGently("Robert")
	    presentGently(42)
	}
	
	fun presentGently(v:Any){ //使用Any類別，可以使用所有non-nullable的類別
	    println("Hello. I would like to present you : $v");
	}

### 參數可以定義是nullable
	fun presentGently(v: Any?) {
	       println("Hello. I would like to present you: $v")
	}
	presentGently(null)
	// Prints: Hello. I would like to present you: null
	presentGently(1)
	// Prints: Hello. I would like to present you: 1
	presentGently("Str")
	// Prints: Hello. I would like to present you: Str
