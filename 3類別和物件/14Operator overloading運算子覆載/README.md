# 14 Operator overloading運算子覆載

####內建方法呼叫，取代運算子

| operatior token | corresponding method |
| ----------- | ------------- |
| a + b | a.plus(b) |
| a - b | a.minus(b) |
| a * b | a.times(b) |
| a / b | a.div(b) |
| a % b | a.rem(b) |
| a..b | a.rangeTo(b) |
| a += b | a.plusAssign(b) |
| a -= b | a.minusAssign(b) |
| a *= b | a.timesAssign(b) |
| a /= b | a.divAssign(b) |


	data class Point(var x: Double, var y: Double) {
	       operator fun plus(point: Point) = Point(x + point.x, y+ point.y)
	       operator fun times(other: Int) = Point(x * other, y * other)
	}
	    //usage
	    var p1 = Point(2.9, 5.0)
	    var p2 = Point(2.0, 7.5)
	    println(p1 + p2)     // prints: Point(x=4.9, y=12.5)
	    println(p1 * 3)      // prints: Point(x=8.7, y=15.0)

### 也可以這樣寫
	p1.plus(p2)
	p1.times(3)

### 運算子沒有繼承，可以overload
~~~
* 運算子method不是override父類別的運算子，所以沒有固定的參數和資料類型。而是overload. 只需要對應的運算子method名稱和前面加一個關鍵字operator

* 事實上，我們也可以定義多個相同的運算子method，但使用不同的參數類型
~~~
	data class Point(var x: Double, var y: Double) {
	       operator fun plus(point: Point) = Point(x + point.x, y +point.y)
	       operator fun plus(vector:Double) = Point(x + vector, y + vector)
	    }
	    var p1 = Point(2.9, 5.0)
	    var p2 = Point(2.0, 7.5)
	    
	    println(p1 + p2) // prints: Point(x=4.9, y=12.5)
	    println(p1 + 3.1) // prints: Point(x=6.0, y=10.1)
	    //compiler可以自動找適合的overload的運算子

### 如果有定義 + 運算子method, 則就同的支援 += 組合運算子method

	var p1 = Point(2.9, 7.0)
	var p2 = Point(2.0, 7.5)
	p1 += p2
	println(p1) // prints: Point(x=4.9, y=14.5)
	

### 會錯誤
~~~
同時定義 plus and plus method , 並且使用相的的參數類型將會出錯
~~~
	data class Point(var x:Double, var y:Double){
	       init{
	           println("PLoint created $x.$y");
	       }
	       
	       operator fun plus(point:Point) = Point(x + point.x, y + point.y);
	       operator fun plusAssign(point:Point){
	           x += point.x;
	           y += point.y;
	       }
	   }
	   
	   var p1 = Point(2.9, 7.0);
	   var p2 = Point(2.0, 7.5);
	   val p3 = p1 + p2;
	   println("$p1, $p2, $p3");
	    
	   //p1 += p2 ;錯誤

### 使用 object declarations 定義singleton的 class 簡單好用
~~~
object declarations是lazy initialize，它可以巢狀在其它的object declaration內或 non-inner class.它們不可以指定給變數
~~~



	
