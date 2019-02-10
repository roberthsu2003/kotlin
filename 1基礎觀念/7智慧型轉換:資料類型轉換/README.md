# 智慧型轉換/資料類型轉換
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
	}
	
###智慧型轉換是有範圍限制的
	if(animal is Fish) {
	            animal.isHungry() //1
	 }
	 animal.isHungry() //錯誤

###擴大智慧型轉換的範圍
	 if (animal !is Fish) //1
	           return
	 animal.isHungry() //
	 
###利用if的延遲判斷
	if (animal is Fish && animal.isHungry()) {
	            println("Fish is hungry")
	}
	  
