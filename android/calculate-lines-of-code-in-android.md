
# Calculate Lines of Code in Android

> There are multiple ways you can find the lines of code.

### Method 1

One simple way is as follows,

1. Click `Ctrl + Shift + F` to open global search
2. Use `Regex Mode` (Either there will be regex checkbox or some btn on global search)
3. In the search box you can enter `\n` | `[\n]+` | `^`
4. Enable the whole project as the scope
5. Yoc can limit the search to java and xml files, by following the mask `*.java, *.xml`
6. Hit the `Open in Find Window` button ar the bottom right or click `Ctrl + Enter`
7. If it ask whether you want to continue, click `Continue `

</br>

### Method 2

Alternative to above method is, You can use a `addon/plugin` for android studio,

Go to [http://plugins.jetbrains.com/plugin/?idea&id=4509](http://plugins.jetbrains.com/plugin/?idea&id=4509) and install the latest version

**To install**

1. Run Android Studio
2. From the menu bar, select File-->Settings
3. Under IDE Settings, click Plugins, and then click Install plugin from disk
4. Navigate to the folder where you downloaded the plugin and double-click it
5. Restart Android Studio

**To count the lines**

1. Check the statistics option that is visible after installing the plugin.
2. This option is near the run, debug, gradle console, bottom left corner of Android studio

</br>

## References

[https://stackoverflow.com/questions/37454493/how-to-get-number-of-lines-of-a-project-in-android-studio/51204230](https://stackoverflow.com/questions/37454493/how-to-get-number-of-lines-of-a-project-in-android-studio/51204230)