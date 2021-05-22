
# Alternative to IntentService

* Normally we all come across lot of applications, which works in background. This background functionality is implemented using the Service or IntentService.

### Service
* You can think `Service` as an Android component that is used to perform some long-running operations in the background like that in the Music app, where we run the app in the background and use other applications of the mobile parallelly.

### IntentService
* The `Service` is the base class for the `IntentService`. Basically, it uses “work queue process” pattern where the `IntentService` handles the on-demand requests (expressed as Intents) of clients. So, whenever a client sends a request then the Service will be started and after handling each and every Intent, the Service will be stopped.
* To use `IntentService` you have to extend the `IntentService` and implement the `onHandleIntent(android.content.Intent)`.

* Example of How IntentService works

```java
/**
 * Example implementation of a IntentService.
 */

public class SimpleIntentService extends IntentService {
    public static final String PARAM_IN_MSG = "imsg";
    public static final String PARAM_OUT_MSG = "omsg";
 
    public SimpleIntentService() {
        super("SimpleIntentService");
    }
 
    @Override
    protected void onHandleIntent(Intent intent) {
 
        String msg = intent.getStringExtra(PARAM_IN_MSG);
        SystemClock.sleep(30000); // 30 seconds
        String resultTxt = msg + " "
            + DateFormat.format("MM/dd/yy h:mmaa", System.currentTimeMillis());
    }
}
```

- You need to start the service from the app activity.
- The code for the service method of processing is pretty straightforward. First, an Intent instance is generated and any data (like the message text) is packaged in the intent using the extras. Finally, the IntentService is started with a call to startService().

```java
EditText input = (EditText) findViewById(R.id.txt_input);
String strInputMsg = input.getText().toString();

Intent msgIntent = new Intent(this, SimpleIntentService.class);
msgIntent.putExtra(SimpleIntentService.PARAM_IN_MSG, strInputMsg);
startService(msgIntent);
```



> <b>The IntentService is deprecated in Android 11 (R), so we will be using JobIntentService as an alternative for it.</b>

```java
/**
 * Example implementation of a JobIntentService.
 */
 
public class SimpleIntentService extends JobIntentService {
    public static final String PARAM_IN_MSG = "imsg";
    public static final String PARAM_OUT_MSG = "omsg";
 
    // convenient method for starting the service.
    static void enqueueWork(Context context, Intent work) {
        enqueueWork(context, SimpleJobIntentService.class, JOB_ID, work);
    }
 
    // This method is called when service starts instead of onHandleIntent
    @Override
    protected void onHandleWork(@NonNull Intent intent) {
        onHandleIntent(intent)
    }

    // remove override and make onHandleIntent private.
    private void onHandleIntent(Intent intent) {
 
        String msg = intent.getStringExtra(PARAM_IN_MSG);
        SystemClock.sleep(30000); // 30 seconds
        String resultTxt = msg + " "
            + DateFormat.format("MM/dd/yy h:mmaa", System.currentTimeMillis());
    }
}
```

You can start the service as

```java
Intent msgIntent = new Intent(this, SimpleIntentService.class);
SimpleIntentService.enqueueWork(this, msgIntent)
```

Important:  
You need to add permissions to manifest.

`<uses-permission android:name="android.permission.WAKE_LOCK" />` // needed for pre-oreo devices

also

```xml
<service
    android:name=".FetchAddressIntentService"
    android:permission="android.permission.BIND_JOB_SERVICE" // needed for oreo and above
    android:exported="true"/>
```


### References

1. [Service vs IntentService](https://blog.mindorks.com/service-vs-intentservice-in-android)
2. [IntentService](https://developer.android.com/reference/android/app/IntentService)
3. [JobIntentService](https://developer.android.com/reference/androidx/core/app/JobIntentService)
4. [IntentService is deprecated, how do I replace it with JobIntentService](https://stackoverflow.com/questions/62138507/intentservice-is-deprecated-how-do-i-replace-it-with-jobintentservice)
