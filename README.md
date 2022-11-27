# Google Advertising ID

A convinient way to retrieve 'Advertising ID' and 'Is Tracking Enabled' flag without any Play Services dependencies in Android applications.

## Usage

### Basic

Simply invoke static `GaidUtil.getAdInfo(Context, GaidUtil.GaidListener)` while supplying application context and a listener object.
Be aware that listener's methods will be invoked on UI thread.

```java
GaidUtil.getAdInfo(getApplicationContext(), new GaidUtil.GaidListener() {
            @Override
            public void onSuccess(GaidUtil.AdIdInfo info) {
                String adId = info.getAdId();
                boolean adTrackingEnabled = info.isAdTrackingEnabled();
                Log.v(tag, "Gaid: "+adId+" & isAdTrackingEnabled: "+adTrackingEnabled);
            }

            @Override
            public void onException(Exception exception) {
                Log.e(tag, exception.getMessage());
                exception.printStackTrace();
            }
        });
```

### Advanced

Simply invoke static `GaidUtil.getAdInfo(Context, boolean, GaidUtil.GaidListener)` to use predefined thread to invoke listener's methods:
* boolean = true for UI thread
* boolean = false for current thread 

Simply invoke static `GaidUtil.getAdInfo(Context, IExecutor, GaidUtil.GaidListener)` to use your own IExecutor implementation.
