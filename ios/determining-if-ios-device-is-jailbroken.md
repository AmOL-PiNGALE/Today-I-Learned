
# Determining if iOS Device is Jailbroken

[ iOS Security Suite](https://github.com/securing/IOSSecuritySuite) is an advanced and easy-to-use platform security & anti-tampering library written in pure Swift! If you are developing for iOS and you want to protect your app according to the OWASP MASVS standard, chapter v8, then this library could save you a lot of time.

What ISS detects:

- Jailbreak (even the iOS 11+ with brand new indicators! 🔥)
- Attached debugger 👨🏻‍🚀
- If an app was run in an emulator 👽
- Common reverse engineering tools running on the device 🔭

* <b>Setup</b>
There are 4 ways you can start using IOSSecuritySuite

1. Add source</br>
Add `IOSSecuritySuite/*.swift` files to your project

2. Setup with CocoaPods</br>
`pod 'IOSSecuritySuite'`

3. Setup with Carthage</br>
`github "securing/IOSSecuritySuite"`

4. Setup with Swift Package Manager</br>
```
.package(url: "https://github.com/securing/IOSSecuritySuite.git", from: "1.5.0")
```

* <b>Update Info.plist</b>
After adding ISS to your project, you will also need to update your main Info.plist. There is a check in jailbreak detection module that uses `canOpenURL(_:)` method and requires specifying URLs that will be queried.

```
<key>LSApplicationQueriesSchemes</key>
<array>
	<string>cydia</string>
	<string>undecimus</string>
	<string>sileo</string>
	<string>zbra</string>
</array>
```

* <b>How to use</b>
    - Jailbreak detector module</br>
    The simplest method returns True/False if you just want to know if the device is jailbroken or jailed

```
if IOSSecuritySuite.amIJailbroken() {
	print("This device is jailbroken")
} else {
	print("This device is not jailbroken")
}
```
