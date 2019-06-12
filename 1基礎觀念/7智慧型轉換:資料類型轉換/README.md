# 智慧型轉換(smart casting)/資料類型轉換(Type Smart Cast)
相對於安全性轉換(as?), 使用智慧型轉換後就不需使用 as, as?
### java沒有智慧型轉換
	//Java
	if (animal instanceof Fish){
	    Fish fish = (Fish) animal;
	    fish.isHungry();
	    //or
	    ((Fish) animal).isHungry();
	}
	
### kotlin有智慧型轉換
	if(animal is Fish) {
		animal.isHungry()
		animal.isHungry() //不需要再用 as 或 as?
	}
	
	//demo1 (在{}限定範圍內的智慧型轉換)
	fun demo(x: Any) {
	    if (x is String) {
	        print(x.length) // x is automatically cast to String
	    }
	}
	
	//demo2
	fun demo(x: Any) {
    if (x !is String) return //在下方全部都已智慧型轉換
    
    print(x.length) // x is automatically cast to String
    
    }
    
    // ||右邊自動轉型
    // && 右邊自動轉型
	// x is automatically cast to string on the right-hand side of `||`
	if (x !is String || x.length == 0) return
	
	// x is automatically cast to string on the right-hand side of `&&`
	if (x is String && x.length > 0) {
	    print(x.length) // x is automatically cast to String
	}
### 智慧型轉換是有範圍限制的
	if(animal is Fish) {
	            animal.isHungry() //1
	 }
	 animal.isHungry() //錯誤

### 擴大智慧型轉換的範圍
	 if (animal !is Fish) //1
	           return
	 animal.isHungry() //
	 
### 利用if的延遲判斷
	if (animal is Fish && animal.isHungry()) {
	   println("Fish is hungry")
	}
	  
