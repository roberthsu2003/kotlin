# 單行運算式的function
### 傳統單行運算式function
	fun square(x:Int):Int{
	    //這是單行運算式function
	    return x * x
	} 
	
	//andorid 內容
	fun getEmail():String{
    	return emailView.text.toStirng()
	}


### 單行運算式有使用區塊符號
	fun square(x:Int):Int{
	    //這是單行運算式function
	    return x * x
	} 
	
		
### 單行運算式可以不使用傳回值，因為kotlin會自我推測
	fun square(x:Int) = x * x
	


### 在andoird內的應用
	class AddressAdapter : ItemAdapter<AddressAdapter.ViewHolder>() {
	        override fun getLayoutId() = R.layout.choose_address_view
	        override fun onCreateViewHolder(itemView: View) = ViewHolder(itemView)
	        // Rest of methods
	    }

###單行運算式搭配when判斷式
	fun valueFromBooking(key: String, booking: Booking?) = when(key) {
	        "patient.nin" -> booking?.patient?.nin
	        "patient.email" -> booking?.patient?.email
	        "patient.phone" -> booking?.patient?.phone
	        "comment" -> booking?.comment
	else -> null }

###單行運算式搭配多重串接運算
	fun textFormatted(text: String, name: String) = text
	                          .trim()
	                          .capitalize()
	                          .replace("{name}", name)
	        val formatted = textFormatted("hello, {name}", "Marcin")
	        println(formatted) // Hello, Marcin


###和android 的activity onOptionsItemSelected method 整合
	override fun onOptionsItemSelected(item: MenuItem): Boolean = when
	    {
	        item.itemId == android.R.id.home -> {
	            onBackPressed()
	true }
	        else -> super.onOptionsItemSelected(item)
	    }



