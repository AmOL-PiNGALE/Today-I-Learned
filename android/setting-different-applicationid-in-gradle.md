
# Setting different ApplicationId in Gradle 

For one scenario I need to set two **totally different ApplicationId's (packages)** for a different Build Types / Product Flavors. So using solution for `applicationIdSuffix` was not enough for me.

So I came across the [Stackoveflow post](https://stackoverflow.com/questions/51765667/setting-the-applicationid-in-gradle-for-a-combined-product-flavor), but this code was not working for me as I was using Build types, so later by reading official doc for the `ApplicationVariant` and related classes found some solution which specific to Build types

```groovy
// This code snippet is used for dynamically selecting the ApplicationId
// Based on Build Types 

android.applicationVariants.all { variant ->
    def mergedFlavor = variant.mergedFlavor
    switch (variant.buildType.name) {
        case "release":
            mergedFlavor.setApplicationId("com.application.id.release")
            break
        default:
            mergedFlavor.setApplicationId("com.application.id.random")
            break
    }
}
```

and we can use following code snippet for different product flavors,

```groovy
// This code snippet is used for dynamically selecting the ApplicationId
// Based on Product Flavors

android.applicationVariants.all { variant ->
    def mergedFlavor = variant.mergedFlavor
    switch (variant.flavorName) {
        case "freeUs":
            mergedFlavor.setApplicationId("com.application.id.freeUs")
            break
        case "freeDe":
            mergedFlavor.setApplicationId("com.application.id.freeDe")
            break
    }
}
```