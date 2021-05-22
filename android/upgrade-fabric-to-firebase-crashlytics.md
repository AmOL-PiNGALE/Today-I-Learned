
## Upgrade Fabric to Firebase Crashlytics

Normally apps have some kind of Crashlytics or Analytics tools to monitor the crashes and events from the app. One such tool was `Fabric SDK` which was used to report crashes.

But as of March 31, 2020, the `Fabric SDK` got retired and instead of it we can migrate to `Firebase Crashlytics`. 

So in recent days, I came across a project where I need to migrate the `Fabric` to `Firebase Crashlytics`, this post walkthrough the steps required for it.

So let's get started...

### Before you begin

The `Firebase Crashlytics SDK` uses `AndroidX` as a dependency, so if your app uses older versions of the App Support Library, first migrate your app to `AndroidX`.


### Step 1: Add a Firebase configuration file
Add the Firebase Android configuration file to your app:

    1. Open your Project Settings. In the Your apps card, select the package name of the app for which you need a config file.
    2. Click `Download google-services.json` to obtain your Firebase Android config file.
        * You can download your Firebase Android config file again at any time.
        * Make sure the config file is not appended with additional characters, like (2).
    3. Move your config file into the module (app-level) directory of your app

### Step 2: Add the Firebase Crashlytics SDK

    1. In your app's root-level (project-level) build.gradle:
        * Replace Fabric's Maven repository with Google's Maven repository.
        * Replace the Fabric Gradle plugin with the Firebase Crashlytics Gradle plugin. If you're using Android Studio 4.1 Canary, be sure to add the Crashlytics Gradle plugin version 2.0.0 or later.

        ```groovy
        buildscript {
            // ...

            repositories {
                // ...

                // Remove Fabric's Maven repository.
                ~~maven { url 'https://maven.fabric.io/public' }~~

                // Add Google's Maven repository (if it's not there already).
                google()
            }

            dependencies {
                // ..

                // Add the Google Services Gradle plugin (if it's not there already).
                classpath 'com.google.gms:google-services:4.3.8'

                // Remove the Fabric Gradle plugin.
                ~~classpath 'io.fabric.tools:gradle:1.31.2'~~

                // Add the Crashlytics Gradle plugin (use v2.0.0+ if you built
                // your app with Android Studio 4.1).
                classpath 'com.google.firebase:firebase-crashlytics-gradle:2.6.1'
            }
        }
        ```
    2. In your app-level build.gradle, replace the Fabric plugin with the Firebase Crashlytics plugin:

        ```groovy
        apply plugin: 'com.android.application'

        // Apply the Google Services plugin (if it's not there already).
        apply plugin: 'com.google.gms.google-services'

        // Remove the Fabric plugin.
        ~~apply plugin: 'io.fabric'~~

        // Add the Firebase Crashlytics plugin.
        apply plugin: 'com.google.firebase.crashlytics'
        ```
    3. Finally, add the Firebase Crashlytics SDK. In your app-level `build.gradle`, replace the legacy Fabric Crashlytics SDK with the new Firebase Crashlytics SDK. Make sure you add version 17.0.0 or later (beginning November 15, 2020, this is required for your crash reports to appear in the Firebase console).

        ```groovy
        dependencies {
            // Remove the Fabric Crashlytics SDK.
            ~~implementation 'com.crashlytics.sdk.android:crashlytics:2.10.1'~~

            // Add the Firebase Crashlytics SDK.
            implementation 'com.google.firebase:firebase-crashlytics:18.0.0'

            // Recommended: Add the Google Analytics SDK.
            implementation 'com.google.firebase:firebase-analytics:19.0.0'
        }
        ```

### Step 3: Update your code

Review the following SDK changes and make the appropriate updates to your code:

#### The new package and classname for Crashlytics is com.google.firebase.crashlytics.FirebaseCrashlytics.

    * You can now invoke Crashlytics features using instance methods in the FirebaseCrashlytics singleton instead of static functions in the FirebaseCrashlytics class. The FirebaseCrashlytics singleton is globally accessible via the getInstance() static function.

    <b>Fabric SDK</b>

    ```java
    import com.crashlytics.android.Crashlytics;

    // Operations on Crashlytics.
    Crashlytics.someAction()
    ```

    <b>Firebase Crashlytics SDK</b>

    ```java
    import com.google.firebase.crashlytics.FirebaseCrashlytics;

    // Operations on FirebaseCrashlytics.
    FirebaseCrashlytics crashlytics = FirebaseCrashlytics.getInstance();
    crashlytics.someAction();
    ```

#### FirebaseCrashlytics no longer works with the Fabric SDK.

    * Now, Crashlytics starts up automatically using a ContentProvider defined in the new Firebase Crashlytics SDK, which no longer uses the Fabric API key. Crashlytics now uses your app’s `google-services.json` file to associate the app with your Firebase project and retain your historic crash data.

    If you have the Fabric API key (io.fabric.ApiKey) declared in your AndroidManifest.xml file, remove it:

    ```xml
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
        package="com.example.your_app_package">

        <application>
            <activity android:name=".MainActivity"/>

            <!-- Remove this line if it exists -->
            <meta-data android:name="io.fabric.ApiKey"
                android:value="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" />

        </application>
    </manifest>
    ```

    * By default, Crashlytics automatically collects and reports crashes for all instances of your app, but you can choose to enable it only for users who opt in. To turn off automatic crash reporting, in the `<application>` block of your `AndroidManifest.xml file`, set `firebase_crashlytics_collection_enabled` to false:

    ```xml
    <meta-data
        android:name="firebase_crashlytics_collection_enabled"
        android:value="false" />
    ```
#### Crashlytics.log is now an instance method.

    * The new SDK no longer includes a static Crashlytics.log method. To add custom log messages, use the new instance method crashlytics.log instead. Note that the new method no longer echoes to logcat.

    <b>Fabric SDK</b>

    ```java
    Crashlytics.log("my message");

    Crashlytics.log(Log.ERROR, "TAG", "my message");
    ```

    <b>Firebase Crashlytics SDK</b>

    ```java
    FirebaseCrashlytics crashlytics = FirebaseCrashlytics.getInstance();

    crashlytics.log("my message");

    // To log a message to a crash report, use the following syntax:
    crashlytics.log("E/TAG: my message");
    ```


### References

1. [https://firebase.google.com/docs/crashlytics/upgrade-sdk?platform=android](https://firebase.google.com/docs/crashlytics/upgrade-sdk?platform=android)
2. [https://medium.com/velos/fabric-to-firebase-migration-2020-c5dbb2e60128](https://medium.com/velos/fabric-to-firebase-migration-2020-c5dbb2e60128)