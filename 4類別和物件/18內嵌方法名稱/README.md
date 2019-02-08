# 內嵌方法名稱

###infix呼叫,更可讀,更接近人類語言
	var pair = "Everest" to 8848
	public data class Pair<out A, out B>( // 1
	           public val first: A,
	           public val second: B
	        ) : Serializable {
	           public override fun toString(): String = "($first, $second)"
	// 2 }
###
	val mountain = "Everest";
	var pair = mountain.to(8848)

### infix只可以有單一參數
	data class Point(val x: Int, val y: Int) {
	            infix fun moveRight(shift: Int) = Point(x + shift, y)
	}
	
	val pointA = Point(1,4)
	val pointB = pointA moveRight 2
	println(pointB) //prints: Point(x=3, y=4)
	
### infix配合enum
	val card = KING of HEARTS
	enum class Suit {
	            HEARTS,
	            SPADES,
	            CLUBS,
	            DIAMONDS
	}
	enum class Rank {
	            TWO, THREE, FOUR, FIVE,
	            SIX, SEVEN, EIGHT, NINE,
	            TEN, JACK, QUEEN, KING, ACE;
	            
	            infix fun of(suit: Suit) = Card(this, suit)
	}
	
	data class Card(val rank: Rank, val suit: Suit)
	val card = Card(Rank.KING, Suit.HEARTS)
	
###
	val card = Rank.KING of Suit.HEARTS

###
	import Rank.KING
	import Suit.HEARTS
	
	val card = KING of HEARTS