# 參數
  
	fun findDuplicates(list:List<Int>):Set<Int>{
    var list = list.sorted();
	}

### 參數名稱和引數名稱

	fun printSum(a1:Int, a2:Int){
	   print(a1 + a2);
	}
		
	add(3,5)
### 多個參數名稱

	fun printSum(a1:Int, a2:Int){
	   val sum = a + b
	   print(sum)
	}
### 引數可以使用子類別
	fun main() {
	    presentGently("Robert")
	    presentGently(42)
	}
	
	fun presentGently(v:Any){
	    println("Hello. I would like to present you : $v");
	}