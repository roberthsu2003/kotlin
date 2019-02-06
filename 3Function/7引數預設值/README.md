# 引數預設值

	fun main() {
	    printValue("robert",true,"","")
	    printValue("jenny")
	    printValue("alice",false)
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

