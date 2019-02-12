# Strings 樣板
### java字串使用+運算子
	//Java
	String name = "Eva";
	int age = 27;
	String message = "My name is" + name + "and I am" + age + "years old";
	
###  kotlin string template, 使用$
	val name = "Eva"
	val age = 27
	val message = "My name is $name and I am $age years old"
	println(message)
	//Prints: My name is Eva  and I am 27 years old
	
### otlin string template, 使用${}
	val name = "Eva"
	val message = "My name has ${name.length} characters"
	println(message) //Prints: My name has 3 characters

