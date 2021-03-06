# Android Screen Logger

* This lib can make ZIP file, with device data for screen
* Take screenshot
* Take device info
* Provide this from RxJava, and make operation in background thread

### Version
The dependency is available via [jitpack](a).
jCenter is the default Maven repository used by Android Studio.

[![](https://jitpack.io/v/Daniil-Pavenko/screen-dimen-logger.svg)](https://jitpack.io/#Daniil-Pavenko/screen-dimen-logger)

## Quick start

Add dependency to your project. For `build.gradle` file

```
implementation 'com.github.Daniil-Pavenko:screen-dimen-logger:<latest version>'
```

And add to root `build.gradle`
```
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```

## Method
In your activity or view, other. Call method for make screenshot with device info:
```
ScreenParamLogger.instance.logScreen(<And here, can just put activity and tag>)
    .subscribe()
```

```
fun logScreen(activity: Activity, userId: String = ScreenParamLogger.userId,
                  tag: String = activity.localClassName,
                  file: File = provideScreenshotFile(activity, provideFileName("_${tag}_$userId")),
                  checkOnceLogging: Boolean = true,
                  dateTimeFormat: SimpleDateFormat = SimpleDateFormat("HH:mm:ss dd/MM/yyyy", Locale.getDefault()),
                  infoMapData: HashMap<String, String> = hashMapOf()): Observable<PackedData> 
```

So:
`activity: Activity` - is required, other fields not required.
