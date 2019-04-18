# infix calls for name method
~~~
infix呼叫,更可讀,更接近人類語言
~~~

###infix呼叫
	fun main(){
	  val mountain = "Everest"
	  //var pair = mountain.to(8846) //method call
	    var pair = mountain to 8846 //infix call ,傳回Pair
	    println(pair)
	    println(pair.first)
	    println(pair.second)
	}

### 定義infix的name method的條件是，只可以有單一參數,必需是member function(method)
	data class Point(val x:Int, val y:Int){
	    infix fun moveRight(shift:Int) = Point(x + shift, y)
	}
	
	fun main(){
	  val pointA = Point(1, 4)
	  val pointB = pointA moveRight 2;
	  println(pointB)
	}
	
### 一般的enum
	enum class Suit{
	    HEARS,
	    SPADES,
	    CLUBS,
	    DIAMONDS
	}
	
	enum class Rank{
	    TWO, THREE, FOUR, FIVE,
	    SIX, SEVEN, EIGHT, NINE,
	    TEN, JACK, QUEEN, KING, ACE
	}
	
	data class Card(val rank:Rank, val suit:Suit);
	
	fun main(){
			//一般的初始化建立
	    val card = Card(rank=Rank.NINE, suit=Suit.HEARS)
	}
	
### infix 配合enum
	enum class Suit{
	    HEARS,
	    SPADES,
	    CLUBS,
	    DIAMONDS;
	}
	
	enum class Rank{
	    TWO, THREE, FOUR, FIVE,
	    SIX, SEVEN, EIGHT, NINE,
	    TEN, JACK, QUEEN, KING, ACE;
	
	    infix fun of(suit:Suit) = Card(this,suit)
	}
	
	data class Card(val rank:Rank, val suit:Suit);
	
	fun main(){
	    val card = Rank.KING of Suit.HEARS
	    print(card)
	}

### 更簡潔寫法
	import Rank.KING
	import Suit.HEARTS
	
	val card = KING of HEARTS