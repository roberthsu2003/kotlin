# Generic
~~~
將討論generic type 和 generic function,為何要有泛型? 如何使用它? 如何定義泛型類別, 介面, 和涵式。
在執行階段如何處理泛型, 和泛型子類別的關係, 泛型和可null能力處理。
~~~

### 沒有generic時,所有取出的值都必需轉型
	java
	public class need {
	    public static void main(String[] args){
	        ArrayList list = new ArrayList();
	        list.add(1);
	        list.add(2);
	        int first = (int)list.get(0); //轉型
	        int second = (int)list.get(1); //轉型
	    }
	}


### type parameter

	class SimpleList<T> //T就是type parameter
	
	//意思是T是一個資料類型，但要在建立實體時，才確認資料類型
	
### 使用generic
	//SimpleList可以存放不同的資料類型
	
	var intlist:SimpleList<Int>
	var studentList:SimpleList<Student>
	var carList:SimpleList<Car>

