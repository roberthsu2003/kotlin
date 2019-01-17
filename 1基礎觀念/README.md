# kotlin基礎概念
## 變數
var 宣告變數

``` 
fun main() {
    var fruit:String = "orange";
    fruit = "banana";
    println(fruit);
}
``` 

val 宣告常數

```
fun main() {
    val fruit:String = "roange";
    //fruit = "banana"; //錯誤
}


fun main() {
    val list = mutableListOf("a", "b", "c");
    //list = mutableListOf("d", "e") // 錯誤
    list.remove("a");
}
```





## 資料類型推測
> var title:String ; //資料宣告 
  
> var title:String = "Kotlin" //沒有使用資料類型推測 
 
> var title = "Kotlin"

> var title = "Kotlin"  
>  title = 12 //錯誤

> var title:Any = "kotlin"  
> title = 12

## 嚴格的null資料型別
### 安全呼叫
### Elvis 運算子
### 非null的主張
### Let

## Null的能力對應Java

## 轉型
### 安全/不安全的轉換運算子
### 智慧型的轉換
#### 資料類型的聰明轉換
#### Non-nullable smart cast

## 原生資料類型
### Numbers
### Char
### Arrays
### Boolean Type

## Composite data types
### Strings
#### String templates

### Ranges
### Collections

## 敘述式 vs 運算式

## 流程控制
### if 敘述
### when 敘述
### 迴圈
#### for 迴圈
#### while 迴圈
#### 其它的重覆讀取
#### break和continue

## 例外
### try... catch block

## 組譯時的常數
## 委派


