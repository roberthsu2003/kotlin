# 引數標籤名稱語法

	fun main() {
	    printValue("robert",true,"","!")
	    printValue("jenny",suffix = "!",prefix="--")
	    
	    
	}
	
	fun printValue(value:String,inBracket:Boolean=true,prefix:String="",suffix:String=""){
	    print(prefix)
	    if(inBracket){
	        print("${value}")
	    }else{
	        print(value)
	    }
	    println(suffix)
	}

### 可讀性更高
	fun main() {
	   printValue("str", inBracket=true)
	   printValue("str", prefix = "Value is")
	   printValue("str",prefix = "Value is", suffix = "!!")    
	}
	
### 使用引數標籤，可以不依照順序
	fun main() {
	   printValue("str", inBracket=true, prefix = "value is")
	   printValue("str", prefix = "Value is", inBracket=true)  
	    
	}
	
### 前面使用引數位置，後面使用引數標籤(不可以顛倒)
	fun main() {
	   printValue("str",true,"")
	   printValue("str", true, prefix = " ")
	   printValue("str", inBracket = true, prefix = "")
	   printValue("str",inBracket=true, "") //錯誤	    
	}
