
# Admob Implementation

How do you show ads in your app ? Here is the step by step guide


## Configure your App In Four Step

#### Step 1 : 

```java
  dependencies {

      implementation 'com.google.android.gms:play-services-ads:23.3.0'

  }
```

#### Step 2 :
```xml
  <manifest>

        <uses-permission android:name="android.permission.INTERNET"/>
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
        <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>

  <application>

  </application>

</manifest>
```

#### Step 3 :
```java
<manifest>
  <application>

    <meta-data
        android:name="com.google.android.gms.ads.APPLICATION_ID"
        android:value="ca-app-pub-3940256099942544~3347511713"/>

  </application>
</manifest>
```

#### Step 4 ( This Code Write After : [ setContentView(R.layout.activity_main); ] ):
```java
MobileAds.initialize(MainActivity.this, new OnInitializationCompleteListener() {
    @Override
    public void onInitializationComplete(@NonNull InitializationStatus initializationStatus) {

        }
    });
AdRequest adRequest = new AdRequest.Builder().build();
```

## Now Implementation Banner Ads :
#### XML Code :
```xml
    <com.google.android.gms.ads.AdView
        xmlns:ads="http://schemas.android.com/apk/res-auto"
        android:id="@+id/adView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_alignParentBottom="true"
        ads:adSize="BANNER"
        ads:adUnitId="ca-app-pub-3940256099942544/6300978111"
        android:layout_marginBottom="5dp"
        >
    </com.google.android.gms.ads.AdView>
```
#### In Java Code [ Declaration Variable ] :
```java
public class MainActivity extends AppCompatActivity {

    private AdView adView;
    
    @Override
    protected void onCreate(Bundle savedInstanceState){
        .
        .
    }
}
```
#### Java Code :
```java
        adView = findViewById(R.id.adView);

        // ======== Check that you wrote this code in step 4 Start Here =======
        MobileAds.initialize(MainActivity.this, new OnInitializationCompleteListener() {
            @Override
            public void onInitializationComplete(@NonNull InitializationStatus initializationStatus) {

            }
        });
        AdRequest adRequest = new AdRequest.Builder().build();
        // ======== Check that you wrote this code in step 4 End Here =======

        adView.loadAd(adRequest);
```
## Now Implements Interstitial Ads Or Full Screen Ads
#### In Java Code [ Declaration Variable ] :
```java
public class MainActivity extends AppCompatActivity {

    private InterstitialAd mInterstitialAd;
    
    @Override
    protected void onCreate(Bundle savedInstanceState){
        .
        .
    }
}
```

#### Java Code [ Step 1 ] [ Looks like you did it in first step 4... Check ]:
#### [ মনে হয় আপনি এটি প্রথমের স্টেপ ৪ এ করেছেন... চেক করুন ]:
```java
    // ======== Check that you wrote this code in step 4 Start Here =======

    MobileAds.initialize(MainActivity.this, new OnInitializationCompleteListener() {
            @Override
            public void onInitializationComplete(@NonNull InitializationStatus initializationStatus) {

            }
    });
    AdRequest adRequest = new AdRequest.Builder().build();

    // ======== Check that you wrote this code in step 4 End Here =======
```

#### Java Code [ Step 2 ]:
```java
    InterstitialAd.load(this,"ca-app-pub-3940256099942544/1033173712", adRequest, new InterstitialAdLoadCallback() {
                    @Override
                    public void onAdLoaded(@NonNull InterstitialAd interstitialAd) {
                        mInterstitialAd = interstitialAd;
                    }
                    @Override
                    public void onAdFailedToLoad(@NonNull LoadAdError loadAdError) {
                        mInterstitialAd = null;
                    }
        });
```

#### Java Code [ Step 3 ] [ Where you want to see this ads this code paste there ]:
```java
    if (mInterstitialAd != null) {
        mInterstitialAd.show(MainActivity.this);
    }
```

## Now Implementation Rewarded Or Video Ads :
#### In Java Code [ Declaration Variable ] :
```java
public class MainActivity extends AppCompatActivity {

    private RewardedAd rewardedAd;
    
    @Override
    protected void onCreate(Bundle savedInstanceState){
        .
        .
    }
}
```
#### Java Code [ Step 1 ] [ Looks like you did it in first step 4... Check ]:
#### [ মনে হয় আপনি এটি প্রথমের স্টেপ ৪ এ করেছেন... চেক করুন ]:
```java
    // ======== Check that you wrote this code in step 4 Start Here =======

    MobileAds.initialize(MainActivity.this, new OnInitializationCompleteListener() {
            @Override
            public void onInitializationComplete(@NonNull InitializationStatus initializationStatus) {

            }
    });
    AdRequest adRequest = new AdRequest.Builder().build();

    // ======== Check that you wrote this code in step 4 End Here =======
```

#### Java Code [ Step 2 ]:
```java
    RewardedAd.load(this, "ca-app-pub-3940256099942544/5224354917",
                adRequest, new RewardedAdLoadCallback() {
                    @Override
                    public void onAdLoaded(@NonNull RewardedAd ad) {
                        rewardedAd = ad;
                    }
                    @Override
                    public void onAdFailedToLoad(@NonNull LoadAdError loadAdError) {
                        rewardedAd = null;
                    }
        });
```

#### Java Code [ Step 3 ] [ Where you want to see this ads this code paste there ]:
```java
    if (rewardedAd != null) {
        rewardedAd.show(MainActivity.this, new OnUserEarnedRewardListener() {
            @Override
            public void onUserEarnedReward(@NonNull RewardItem rewardItem) {
                int rewardAmount = rewardItem.getAmount();
                String rewardType = rewardItem.getType();
            }
        });
    }
```
## Screenshots

![BannerAds](https://github.com/user-attachments/assets/4643938e-7af3-43ed-b514-691af4c1ea3e)
![FullScreenAds](https://github.com/user-attachments/assets/eaa6f93c-2cc7-4b54-80dd-2b9066b5dfc9)
![VideoAds](https://github.com/user-attachments/assets/ee9841f1-65c4-454f-81e8-ab8986e95dab)

## Google Admob Official Link

- [Google Admob](https://developers.google.com/admob/android/quick-start)
- [Banner Ads](https://developers.google.com/admob/android/banner)
- [Interstitial Ads](https://developers.google.com/admob/android/interstitial)
- [Rewarded Ads](https://developers.google.com/admob/android/rewarded)
## Author

[Prothes Barai](https://prothes-asp.github.io/prothes/)

