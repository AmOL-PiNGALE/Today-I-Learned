
# Determining if an Android Device is Rooted Pprogrammatically

Rooting detection is a cat and mouse game and it is hard to make rooting detection that will work on all devices for all cases.

See [Android Root Beer](https://github.com/scottyab/rootbeer) for advanced root detection which also uses JNI and native CPP code compiled into .so native library.

If you need some simple and basic rooting detection check the code below:

```
/**
* Checks if the device is rooted.
*
* @return <code>true</code> if the device is rooted, <code>false</code> otherwise.
*/

public static boolean isRooted() {

    // get from build info
    String buildTags = android.os.Build.TAGS;
    if (buildTags != null && buildTags.contains("test-keys")) {
      return true;
    }

    // check if /system/app/Superuser.apk is present
    try {
      File file = new File("/system/app/Superuser.apk");
      if (file.exists()) {
        return true;
      }
    } catch (Exception e1) {
      // ignore
    }

    // try executing commands
    return canExecuteCommand("/system/xbin/which su")
        || canExecuteCommand("/system/bin/which su") || canExecuteCommand("which su");
}

// executes a command on the system
private static boolean canExecuteCommand(String command) {
	boolean executedSuccesfully;
	try {
  		Runtime.getRuntime().exec(command);
  		executedSuccesfully = true;
	} catch (Exception e) {
  		executedSuccesfully = false;
	}

	return executedSuccesfully;
}
```

1. [StackOveflow](https://stackoverflow.com/questions/3424195/determining-if-an-android-device-is-rooted-programmatically)
2. [Medium Blog](https://medium.com/@scottyab/detecting-root-on-android-97803474f694)
