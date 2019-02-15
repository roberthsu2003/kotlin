# 例外

### kotlin可以不處理exception
	fun foo() {
	     throw IOException()
	}
	fun bar() {
	      foo () //不需要使用try...catch包圍foo()
	 }
