
# Setup ADB on macOS 

**Note for zsh users: replace all references to `~/.bash_profile` with `~/.zshrc`.**

## Option 1 - Using Homebrew

This is the easiest way and will provide automatic updates.

1. Install the homebrew package manager
```
 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

2. Install adb
```
 brew install android-platform-tools
```

3. Start using adb
```
 adb devices
```

## Option 2 - Manually (just the platform tools)

This is the easiest way to get a manual installation of ADB and Fastboot.

1. Delete your old installation (optional)
```
 rm -rf ~/.android-sdk-macosx/
```

2. Navigate to [https://developer.android.com/studio/releases/platform-tools.html](https://developer.android.com/studio/releases/platform-tools.html) and click on the `SDK Platform-Tools for Mac` link.

3. Go to your Downloads folder
```
 cd ~/Downloads/
```

4. Unzip the tools you downloaded
```
 unzip platform-tools-latest*.zip 
```

5. Move them somewhere you won't accidentally delete them
```
 mkdir ~/.android-sdk-macosx
 mv platform-tools/ ~/.android-sdk-macosx/platform-tools
```

6. Add platform-tools to your path
```
 echo 'export PATH=$PATH:~/.android-sdk-macosx/platform-tools/' >> ~/.bash_profile
```

7. Refresh your bash profile (or restart your terminal app)
```
 source ~/.bash_profile
```

8. Start using adb
```
 adb devices
```

## Option 3 - Manually (with SDK Manager)

1. Delete your old installation (optional)
```
 rm -rf ~/.android-sdk-macosx/
```

2. Download the Mac SDK Tools from the Android developer site under "Get just the command line tools". Make sure you save them to your Downloads folder.

3. Go to your Downloads folder
```
 cd ~/Downloads/
```

4. Unzip the tools you downloaded
```
 unzip tools_r*-macosx.zip 
```

5. Move them somewhere you won't accidentally delete them
```
 mkdir ~/.android-sdk-macosx
 mv tools/ ~/.android-sdk-macosx/tools
```

6. Run the SDK Manager
```
 sh ~/.android-sdk-macosx/tools/android
```

7. Uncheck everything but Android SDK Platform-tools (optional)

8. Click Install Packages, accept licenses, click Install. Close the SDK Manager window.

9. Add platform-tools to your path
```
 echo 'export PATH=$PATH:~/.android-sdk-macosx/platform-tools/' >> ~/.bash_profile
```

10. Refresh your bash profile (or restart your terminal app)
```
 source ~/.bash_profile
```

11. Start using adb 
```
 adb devices
```

**Note: Sometimes the path to adb should already present in the bash, So just refresh the bash using `source ~/.bash_profile` and run `adb`**

</br>

## References

1. [https://stackoverflow.com/questions/17901692/set-up-adb-on-mac-os-x](https://stackoverflow.com/questions/17901692/set-up-adb-on-mac-os-x)
2. [https://stackoverflow.com/questions/10303639/adb-command-not-found](https://stackoverflow.com/questions/10303639/adb-command-not-found)