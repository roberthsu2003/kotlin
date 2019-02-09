# 重新定義運算子

	data class Point(var x: Double, var y: Double) {
	       operator fun plus(point: Point) = Point(x + point.x, y+ point.y)
	       operator fun times(other: Int) = Point(x * other, y * other)
	}
	    //usage
	    var p1 = Point(2.9, 5.0)
	    var p2 = Point(2.0, 7.5)
	    println(p1 + p2)     // prints: Point(x=4.9, y=12.5)
	    println(p1 * 3)      // prints: Point(x=8.7, y=21.0)

###也可以這樣寫
	p1.plus(p2)
	p1.times(3)

### 運算子沒有繼承，可以overload
	data class Point(var x: Double, var y: Double) {
	       operator fun plus(point: Point) = Point(x + point.x, y +point.y)
	       operator fun plus(vector:Double) = Point(x + vector, y + vector)
	    }
	    var p1 = Point(2.9, 5.0)
	    var p2 = Point(2.0, 7.5)
	    println(p1 + p2) // prints: Point(x=4.9, y=12.5)
	    println(p1 + 3.1) // prints: Point(x=6.0, y=10.1)

### 支援組合運算子
	var p1 = Point(2.9, 7.0)
	var p2 = Point(2.0, 7.5)
	p1 += p2
	println(p1) // prints: Point(x=4.9, y=14.5)

