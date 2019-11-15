## 集合物件
### Array
```
語法:Array(size: Int, init: (Int) -> T) 
```

#### kotlin 陣列可以使用下面方法建立:  
* arrayOf()  
* intArrayOf()  
* charArrayOf()  
* booleanArrayOf()  
* longArrayOf()  
* shortArrayOf()  
* bytenArrayOf()  

#### 沒有做用陣列的統計分數

```
fun main(){
    //不使用Array統計學生的分數
    //輸入5位學生的分數，並且求出其「總和」與 「平均」
    var sum = 0
    println("請輸入5位學生的分數")

    print("1號的分數:")
    val stu1 = readLine()?.toIntOrNull() ?: 0
    sum += stu1;

    print("2號的分數:")
    val stu2 = readLine()?.toIntOrNull() ?: 0
    sum += stu2;

    print("3號的分數:")
    val stu3 = readLine()?.toIntOrNull() ?: 0
    sum += stu3;

    print("4號的分數:")
    val stu4 = readLine()?.toIntOrNull() ?: 0
    sum += stu4;

    print("5號的分數:")
    val stu5 = readLine()?.toIntOrNull() ?: 0
    sum += stu5;

    println("總分為:${sum}分")
    println("平均為:${sum/5.0}")
}
```

```
kotlin 陣列的建立使用arrayOf()和使用set

fun main() {
    val array1 = arrayOf(1,2,3,4)
    val array2 = arrayOf<Long>(11,12,13,14)
    array1.set(0,5)
    array1[2] = 6

    array2.set(2,10)
    array2[3] = 8

    for(element in array1){
        println(element)
    }
    println()
    for(element in array2){
        println(element)
    }
}

```

```
kotlin 陣列的建立使用和使用get
fun main() {
    val array1 = arrayOf(1,2,3,4)
    val array2 = arrayOf<Long>(11,12,13,14)
    println(array1.get(0))
    println(array1[2])
    println()
    println(array2.get(2))
    println(array2[3])

}
```

```
//使用建構式建立陣列
fun main(args: Array<String>){
    var myArray = Array<Int>(5){0}

    for(element in myArray){
        println(element)
    }

    myArray[1]= 10
    myArray[3]= 15

    for(element in myArray){
        println(element)
    }
}
```

```
//使用intArray function

fun main(){
    val name = arrayOf<String>("Ajay","Prakesh","Michel","John","Sumit")
    var myArray2 = arrayOf<Int>(1,10,4,6,15)
    var myArray3 = arrayOf(5,10,20,12,15)
    var myArray4= arrayOf(1,10,4, "Ajay","Prakesh")
    var myArray5: IntArray = intArrayOf(5,10,20,12,15)


    for(element in name){
        println(element)
    }

    println()
    for(element in myArray2){
        println(element)
    }
    println()
    for(element in myArray3){
        println(element)
    }
    println()
    for(element in myArray4){
        println(element)
    }
    println()
    for(element in myArray5){
        println(element)
    }
}


```
```
//array是固定大小
fun main(args: Array<String>){
    var myArray5: IntArray = intArrayOf(5,10,20,12,15)

    myArray5[6]=18 // ArrayIndexOutOfBoundsException
    for(element in myArray5){
        println(element)
    }
}
```

```
//使用Range
fun main(args: Array<String>){
    var myArray5: IntArray = intArrayOf(5,10,20,12,15)

    for (index in 0..4){
        println(myArray5[index])
    }
    println()
    for (index in 0 until myArray5.size){
        println(myArray5[index])
    }
}
```

```
fun main(){
    //使用Array統計學生的分數
    //輸入5位學生的分數，並且求出其「總和」與 「平均」
    var sum = 0
    val count = 5
    //建立空陣列
    val stus = Array<Int>(5){0}
    println("請輸入5位學生的分數")
    for(index in stus.indices){
        print("${index+1}號的分數:")
        stus[index] = readLine()?.toIntOrNull() ?: 0
        sum += stus[index]
    }
    println("總分為:${sum}分")
    println("平均為:${sum/5.0}")
}


```

```
fun main(){
    //輸入分數並顯示最高分
    //使用Array統計學生的分數
    //輸入5位學生的分數，並且求出其最高分和最低分
    var sum = 0
    val count = 5
    //建立空陣列
    val stus = Array<Int>(5){0}
    println("請輸入5位學生的分數")
    for(index in stus.indices){
        print("${index+1}號的分數:")
        stus[index] = readLine()?.toIntOrNull() ?: 0
        sum += stus[index]
    }

    var max = stus[0]
    var min = stus[0]
    for(index in 1 until stus.size){
        if(stus[index] > max)
            max = stus[index]
        else if (stus[index] < min)
            min = stus[index]
    }
    println("總分為:${sum}分")
    println("平均為:${sum/5.0}")
    println("最高分為:${max}")
    println("最低分為:${min}")
}
```

```
package lesson7

import kotlin.random.Random

fun main(){
    //線性搜尋
    val randomValues = Array<Int>(12){ Random.nextInt(0,100)}
    for ((index,value) in randomValues.withIndex()){
        println("index${index}:value${value}")
    }

    outer@ do {
        print("請輸入猜測內容值，直到猜中為止:")
        val guess = readLine()?.toIntOrNull() ?: 0
        for (value in randomValues){
            if(value == guess) {
                println("猜中,離開")
                break@outer
            }

        }
        println("沒有猜中")

    }while(true)
}
```




	
