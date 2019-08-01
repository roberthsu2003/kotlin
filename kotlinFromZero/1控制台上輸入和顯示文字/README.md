# 在控制台上顯示文字
    fun main(){
        /*
            多行程式執行程式的註解
         */
    
        println("第一個kotlin程式") // 單行程式註解
        println("輸出至畫面");
    }

```
當行註解 
//

多行註解
/*

*/
```

 
    //main function是kotlin的程式執行的進入點
    fun main(){
        
    }

```
print() --> 不換行
println() --> 換行

fun main(){
    print("晚安!")
    println(" 吃晚餐沒?")
}
```

```
print("晚安!" + " 吃晚餐沒?")
字串的連結 --> +
```

```
//換行字元
print("\n晚安!\n吃晚餐沒?");
```

```
//自由格式敘述
1.單字中間不可插入空白
錯誤:print ln(" 吃晚餐沒?")

2.字串值不可中途換行
錯誤:println(" 吃晚
            餐沒?")


```