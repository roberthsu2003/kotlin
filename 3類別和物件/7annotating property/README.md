# Annotating property

	@Rule
        val activityRule = ActivityTestRule(MainActivity::class.Java)
        
###   
     
	@JvmField @Rule
	        val activityRule = ActivityTestRule(MainActivity::class.Java)
	        
###

	val activityRule
	        @Rule get() = ActivityTestRule(MainActivity::class.java)

###

	@get:Rule
	        val activityRule = ActivityTestRule(MainActivity::class.Java)