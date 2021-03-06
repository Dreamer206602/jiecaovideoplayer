# Jiecao Video Player  

[![Platform](https://img.shields.io/badge/platform-android-green.svg)](http://developer.android.com/index.html) 
[![Maven Central](https://img.shields.io/badge/Maven%20Central-1.9-green.svg)](http://search.maven.org/#artifactdetails%7Cfm.jiecao%7Cjiecaovideoplayer%7C1.9%7Caar) 
[![Licenses](https://img.shields.io/badge/license-MIT-green.svg)](http://choosealicense.com/licenses/mit/) 
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-jiecaovideoplayer-green.svg?style=true)](https://android-arsenal.com/details/1/3269)
[![GitHub stars](https://img.shields.io/github/stars/lipangit/jiecaovideoplayer.svg?style=social&label=Star)]()

This is the real android video player view with fullscreen function, we are dedicated to make it to be the most popular video play widget on android.  Branch develop is the latest version, although it is not stable for now.

[中文文档](README-ZH.md)

## Features
1. Launching new Fullscreen Activity when playing video in fullscreen mode
2. Even in `ListView`、`ViewPager` and `ListView`、`ViewPager` and `Fragment` and other nested fragments and views situation, it works well
3. Video will be reset(pause) when it's scrolled out of the screen in `ListView` and `ViewPager`
4. It will not disturb or change the playing state when entering or exiting fullscreen
5. Support to custom view controller's skin
6. Support to display the thumb when playing mp3 audio

## Demo Screenshot

![Demo Screenshot][1]

Demo video : http://v.youku.com/v_show/id_XMTQ2NzUwOTcyNA==.html?firsttime=0&from=y1.4-2


## Usage
1.Add the library in build.gradle
```gradle
compile 'fm.jiecao:jiecaovideoplayer:1.9'
```

2.Add JCVideoPlayer in your layout
```xml
<fm.jiecao.jcvideoplayer_lib.JCVideoPlayer
    android:id="@+id/videocontroller1"
    android:layout_width="match_parent"
    android:layout_height="200dp" />
```

3.Set the video uri, video thumb url and video title
```java
JCVideoPlayer videoController = (JCVideoPlayer) findViewById(R.id.videocontroller);
videoController.setUp("http://2449.vod.myqcloud.com/2449_43b6f696980311e59ed467f22794e792.f20.mp4",
    "http://p.qpic.cn/videoyun/0/2449_43b6f696980311e59ed467f22794e792_1/640",
    "嫂子别摸我");
```
4.Remember to invoke `JCVideoPlayer.releaseAllVideos();` in `onPause()` of `Fragment` or `Activity`

#### Other APIs

Set up the video player appearance, you can set the current video player's skin or set the global skin. Priority: some video player instance skin > global skin > default skin
```java
JCVideoPlayer.setGlobleSkin();//set up global skin
videoController.setSkin();//set up some video player instance skin
```

Modify the thumb image view's scaleType property, default value is fitCenter. There will be  black padding if the size of thumb is not compatible with screen size, try to use fitXY or other scaleType.
```java
JCVideoPlayer.setThumbImageViewScalType(ImageView.ScaleType.FIT_XY);
```

Invoke `JCFullScreenActivity.toActivity(...)` to enter fullscreen directly.
```java
JCFullScreenActivity.toActivity(this,
    "http://2449.vod.myqcloud.com/2449_43b6f696980311e59ed467f22794e792.f20.mp4",
    "http://p.qpic.cn/videoyun/0/2449_43b6f696980311e59ed467f22794e792_1/640",
    "嫂子别摸我");
```

ProGuard
```
##Eventbus
-keepclassmembers class ** {
    public void onEvent*(***);
}
# Only required if you use AsyncExecutor
-keepclassmembers class * extends de.greenrobot.event.util.ThrowableFailureEvent {
    public <init>(java.lang.Throwable);
}
# Don't warn for missing support classes
-dontwarn de.greenrobot.event.util.*$Support
-dontwarn de.greenrobot.event.util.*$SupportManagerFragment
```

## Downloads
 * **[jiecaovideoplayer-1.9-demo.apk](https://raw.githubusercontent.com/lipangit/jiecaovideoplayer/develop/downloads/jiecaovideoplayer-1.9-demo.apk)**
 * **[jiecaovideoplayer-1.9.aar](https://raw.githubusercontent.com/lipangit/jiecaovideoplayer/develop/downloads/jiecaovideoplayer-1.9.aar)**
 * **[jiecaovideoplayer-1.9-javadoc.jar](https://raw.githubusercontent.com/lipangit/jiecaovideoplayer/develop/downloads/jiecaovideoplayer-1.9-javadoc.jar)**
 * **[jiecaovideoplayer-1.9-sources.jar](https://raw.githubusercontent.com/lipangit/jiecaovideoplayer/develop/downloads/jiecaovideoplayer-1.9-sources.jar)**



[1]: ./screenshots/j1.png

