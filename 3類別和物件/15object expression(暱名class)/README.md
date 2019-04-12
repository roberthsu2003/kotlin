# object expression(暱名class)

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
	
### 使用object expression
~~~
快速建立一個暱名class並且立刻建一個實體
~~~
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
	//object被建立於暱名class，這暱名class繼承VideoPlayer和實作Player介面
	val player = object: VideoPlayer(), Player { }
	playWith(player)
	
### 使用object expression 快速建立暱名class繼承Any
~~~
快速建立一個實體，有自訂property和自訂的method(無法使用java,因為java一定要有一個自訂的interface)
~~~
	fun main(){
	    val data = object{
	        var size = 1
	        fun update(){
	            print("update的size是$size")
	        }
	
	    }
	
	    data.size = 2
	    data.update()
	
	}
	
### 有自訂interface, java才可以使用
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