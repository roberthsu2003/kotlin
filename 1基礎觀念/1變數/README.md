# 2種變數宣告

###var 宣告變數(可以改變內容)
	fun main(args: Array<String>) {
	       var fruit:String =  "orange" 
	       fruit  = "banana" 
	}

###val 宣告變數(不可以改變內容)
	fun main(args: Array<String>) {
	        val fruit:String= "orange"
	        a = "banana" //錯誤
	}


### val 
	fun main() {
	    val list = mutableListOf("a", "b", "c");
	    list = mutableListOf("d", "e"); //錯誤
	    list.remove("a");
	    print(list);
	}
###
| 定義變數和值    | 參考改變          | 物件改變       |
|:------------- |:---------------:| -------------:|
| col 3 is      | some wordy text |         $1600 |
| col 2 is      | centered        |           $12 |
| zebra stripes | are neat        |            $1 |






