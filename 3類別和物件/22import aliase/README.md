# import aliase別名

	import com.facebook.ads.InterstitialAd
	        val fbAd = InterstitialAd(context, "...")
	        val googleAd = com.google.android.gms.ads.InterstitialAd(context) //full qualified name(namespace + class name)

### 使用as
	import com.facebook.ads.InterstitialAd as FbAd
	import com.google.android.gms.ads.InterstitialAd as GoogleAd
