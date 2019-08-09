# 2在控制輸入文字
## Kotlin Input
> **使用readLine()輸入字串** 

```
fun main(args: Array<String>) {
    print("Enter text: ")
    val stringInput = readLine()!!
    println("You entered:" + stringInput)
}
```

> **使用java的標準資料庫Scanner取得其它的資料類型** 
  
```
> import java.util.Scanner  
> val reader = Scanner(System.`in`)
> reader.nextInt(),reader.nextLong(),nextFloat(), nextDouble(),nextBoolean
```

```
import java.util.Scanner

fun main(args: Array<String>) {
    // Creates an instance which takes input from standard input (keyboard)
    val reader = Scanner(System.`in`)
    print("Enter a number: ")
    // nextInt() reads the next integer from the keyboard
    var integer:Int = reader.nextInt()
    println("You entered: $integer")
}
```

