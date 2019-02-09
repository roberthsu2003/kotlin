# lambda當作最後一個的引數

	fun longOperationAsync(a: Int, callback: ()->Unit) {
	            // ...
	}
	
	 longOperationAsync(10) {
            hideProgress()
	}

###實例運用
	public fun thread(
	            start: Boolean = true,
	            isDaemon: Boolean = false,
	            contextClassLoader: ClassLoader? = null,
	            name: String? = null,
	            priority: Int = -1,
	            block: () -> Unit): Thread {
	                // implementation
	            }
	thread { /* code */ }

	thread (name = "SomeThread") { /*...*/ }
	thread (false, false) { /*...*/ }
