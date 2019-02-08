# 物件運算式(暱名class)

	//java
	ServiceConnection serviceConnection = new ServiceConnection() {
	            @Override
	            public void onServiceDisconnected(ComponentName name) {
	                ...
	}
	            @Override
	            public void onServiceConnected(ComponentName name,
	                IBinder service)
	            {
	... }
	}
	
	
	//kotlin
	val serviceConnection = object: ServiceConnection {
	         override fun onServiceDisconnected(name: ComponentName?) { }
	         override fun onServiceConnected(name: ComponentName?,
	             service: IBinder?) { }
	}
	
### 介面
	interface Player {
	            fun play()
	}
	fun playWith(player: Player) {
	            print("I play with")
	            player.play()
	}
	
	open class VideoPlayer {
            fun play() {
                println("Play video")
            }
	}

	val player = object: VideoPlayer(), Player { }
	playWith(player)
	
###整合
	open class VideoPlayer {
	            fun play() {
	                println("Play video")
	            }
	}
	        interface Player{
	            fun play()
	fun stop() }
	        //usage
	        val player = object: VideoPlayer(), Player {
	            var duration:Double = 0.0
	            fun stop() {
	                println("Stop  video")
	} }
	        player.play() // println("Play video")
	        player.stop() // println("Stop  video")
	        player.duration = 12.5