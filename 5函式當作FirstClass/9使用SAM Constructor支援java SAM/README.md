# 使用SAM Constructor支援java SAM
###java7語法
	//Java
	 button.setOnClickListener(new OnClickListener() {
	            @Override public void onClick(View v) {
	                // Operation
	            } 
	});

###kotlin SAM Constructor
	button.setOnClickListener(OnClickListener {
	            /* ... */
	})


###暱名function和lambda語法
	val a = fun() {} // Anonymous function
	val b = {} // Lambda expression


###還可以更簡易
	button.setOnClickListener {
	            // Operations
	}
	
###在kotlin使用interface不行這樣呼叫
	interface OnClick {
	            fun call()
	}
	
	fun setOnClick(onClick: OnClick) {
	 //...
	}
	
	setOnClick {  } //  Error

###在kotlin只有使用Function type的方式才可以呼叫
	fun setOnClick(onClick: ()->Unit) {
	            //...
	}
	setOnClick {  } // Works


###僅限定在java設定的SAM,才可以使用
	// Java, inside View class
	public interface OnClickListener {
	       void onClick(View v);
	 }
	 
	 //使用kotlin語法:
	 val onClick = View.OnClickListener { toast("Clicked") }

###更多android內使用java SAM constructor語法 
	view.setOnLongClickListener { /* ... */; true }
	view.onFocusChange { view, b -> /* ... */ }
	val callback = Runnable { /* ... */ }
	view.postDelayed(callback, 1000)
	view.removeCallbacks(callback)

