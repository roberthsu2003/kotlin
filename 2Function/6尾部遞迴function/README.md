# 尾部遞迴function
> ### 自已呼叫自已  

### 傳統遞迴--太多會throw statkOverflowError
	fun getState(state: State, n: Int): State =
            if (n <= 0) state // 1
            else getState(nextState(state), n - 1)
 	
 	//other
 	fun fact(k: Int): Int {
         if (k == 0) return 1
         else return k * fact(k - 1)
	}
	
	
   
   
   

### 傳統解決方案--不好了解
	fun getState(state: State, n: Int): State {
	            var state = state
	            for (i in 1..n) {
	                state = state.nextState()
				}
	            return state
	        }
### 最佳解決方案 尾部遞迴

	tailrec fun getState(state:State, n:Int):State =
		if (n <=0 ) state
		else getState(state.nextState(), n-1)

### 尾部遞迴相似java程式碼
	public static final State getState(@NotNull State state, int n)
	        {
	            while(true) {
	                if(n <= 0) {
	                    return state;
	                }
	                state = state.nextState();
					n = n - 1; 
				}
	}
