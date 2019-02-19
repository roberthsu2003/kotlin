# 參數vararg
### 有vararg代表充許function接收任何數量的參數
	fun main() {
	    printSum(1,2,3,4,5)
	    printSum();
	    
	}
	
	fun printSum(vararg numbers:Int){
	    val sum = numbers.sum()
	    println(sum);
	}  

### vararg傳入的參數是Array<T>
	fun main() {
	    printAll("A", "B", "C");
	    
	}
	
	fun printAll(vararg texts:String){
	    //推測這texts的資料類型是Array<String>
	    val allTexts = texts.joinToString(",")
	    println("Texts are $allTexts");
	}
	
### 可以在vararg前或後加入更多參數
	fun main() {
	    printAll("All texts: ", "!");
	    printAll("All texts: ", "!", "Hello",  "World");
	    
	}
	
	fun printAll(prefix:String, postfix:String, vararg texts:String){
	    val allTexts = texts.joinToString(", ")
	    println("$prefix$allTexts$postfix");
	}
### vararg引數可以使用該型別的子類別
	fun main() {
	    
	    printAll("A", 1, 'c');
	}
	
	fun printAll(vararg texts:Any){
	    val allTexts = texts.joinToString(", ");
	    println(allTexts);
	}

### 使用*符號+陣列，代表每個元素當作參數

	val texts = arrayOf("B", "C", "D")
	printAll(*texts) // Prints: Texts are: B,C,D
	printAll("A", *texts, "E") // Prints: Texts are: A,B,C,D,E