### 在畫面上顯示文字
```
package lesson1
fun main(){
	println("第一個java程式")
	println("輸出至畫面")
}
```


### 讓使用者輸入文字
```
fun main(){
    print("請輸入姓名:")
    val name = readLine()!!
    print("歡迎" + name + "加入學習kotlin")
}
``` 