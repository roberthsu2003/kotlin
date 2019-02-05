# 尾部遞迴function
### 傳統遞迴
	fun getState(state: State, n: Int): State =
            if (n <= 0) state // 1
            else getState(nextState(state), n - 1)


