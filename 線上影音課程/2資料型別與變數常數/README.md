## 變數、不可變變數、常數的宣告
「變數」顧名思義，就是一個隨時可能改變內容的容器名稱，好像家中的收藏箱可以放入各種不同的東西。你需要多大的收藏箱呢?那就要看此收藏
箱究竟要收藏什麼東西而定。在程式中使用變數和常數也是一樣，當設計者宣告一個變數或常數時，應用程式就會配置一塊記憶體給此變數使用或常數使用，以變數名稱做為辨識此塊記憶體的標誌，系統會根據宣告時指定的資料型別決定配置的記憶體大小，如此設計者就可在程式中將各種資料存入該變數中。

#### 變數、不可變變數、常數宣告的語法
> 2種變數宣告和1種常數宣告

```
var 宣告變數(可以改變內容)

fun main() {
	       var number = 42
			  var message = "Hello"
			  number = 10
			  number += 7
			  println(number)
			  println(message + " there")
}


val 宣告不可變數(不可以改變內容)
fun main() {
        val message = "Hello"
        val number = 42
}

const val 宣告常數(不可以改變內容)
fun main() {
        const val x = 2
}

```
## 變數命名規則
為變數命名必須遵守下列規則，否則在程式編譯時會產生錯誤:  
* 變數名稱的第一個字員必須是大小寫字母、_、中文。不過，建議最好不要使用中文做為變數命名。不但在撰寫程式時輸入麻煩，而且會降低程式的可攜性。另外，如果以「 _ 」為開始字元，則第二個字元必須是歹小寫字母、數字或「 _  」字元。  
*  變數名稱不能與Kotlin的個留字相同  
*  變數名稱不能包含空白字元及特殊字元，例如:~、\、 @ 、 ? 、 % 、 & 、 #
*  變數名稱中英文字母的大小寫是有區別的。Apple,apple
*  駝峰式的命名法


## 資料型別的推測


#### 建立要求是字串的變數
	var title: String
	
#### 同時宣告變數名稱和資料類型並將內容傳給變數(明確宣告變數類型)
	var title: String = "Kotlin"

#### 宣告變數名稱和將內容傳給變數，資料類型請編譯器自行推測(不明確宣告)
	var title = "Kotlin"

#### kotlin 是 strongly type language
	var title = "Kotlin"
	title = 12 // 1, Error


#### 使用Any類型，代表可以使用任何形別

	var title: Any = "Kotlin"
	title = 12

#### 推測沒有被限定一定要是值，也可以是function
	var total = sum(10, 20)
	
#### 類型推測也可使用泛型
	var persons = listOf(personInstance1, personInstance2)
	// 推測類型為: List<Person> ()

#### 類型推測
	var pair = "Everest" to 8848 // 推測類型為: Pair<String, Int>
	
#### 類型推測
	var pair = "Everest" to 8848
	// 建立pair 使用infix function
	var pair2 = Pair("Everest", 8848)
	// 使用建構子建立 pair

#### 由內向外推測
	var map = mapOf("Mount Everest" to 8848, "K2" to 4017)
	// 推測類型為: Map<String, Int>

#### 不同資料類型，會推測Any
	var map = mapOf("Mount Everest" to 8848, "K2" to "4017")
	// 推測類型為: Map<String, Any>

#### 明確宣告
	var age: Int = 18

#### 值表達式無沒推測為正確類型時，可以使用明確宣告
	var age: Short = 18

#### 使用指定型別的值表達式
	var age: Long = 18 // 明確宣告變數
	var age = 18L //指定Long的值表達式
	
#### 錯誤的語法(無法推測)
	val title // 錯誤



## 基本(原生)資料型別

#### 整數型別
| 類型 | 位元組 | 最小值 | 最大值 |
|:----|:------|:------|:------|
| Long | 8 | -9223372036854775808 | 9223372036854775807 |
| Int | 4 | -2147483648 | 2147483647 |
| Short | 2 | -32768 | 32767 |
| Byte | 1 | -128 | 127 |

#### 整數純值表達式
```
fun main(){
	val anInt = 3
	val anotherInt = 2147483647
	val aLong = 2147483648
	val aBetterLong = 2147483649L
	val aSmallLong = 3L
	val aShort: Short = 32767
	val anotherShort = 1024.toShort()
	val aByte: Byte = 65
	val anotherByte = -32.toByte()
}
```

#### 整數/整數=整數,整數/Double = Double
```
fun main(){
	println(7 / 3)            // Prints 2
	println(7 / 3.0)          // Prints 2.3333333333333335
	val x = 3
	println(7 / x)            // Prints 2
	println(7 / x.toDouble()) // Prints 2.3333333333333335
}
```

#### 浮點數和其它型別
| 類型 | 位元組 | 說明 |
|:----|:------|:--------------|
| Double | 8 | 16-17位數 |
| Float | 4 | 6-7位數 |
| Char | 2 | UTF-16 |
| Boolean | 1 | true,false |

```

fun main() {
    val list = mutableListOf("a", "b", "c");
    list = mutableListOf("d", "e"); //錯誤
    list.remove("a");
    print(list);
}
```



###
| 定義變數和值                   | 參考改變          | 物件改變       |
|:-------------                |:---------------:|:-------------:|
| val = listOf(1,2,3)          | NO              |  NO           |
| val = mutableListOf(1,2,3)   | NO              |  YES          |
| var = listOf(1,2,3)          | YES             |  NO           |
| var = mutableListOf(1,2,3)   | YES             |  YES          |

