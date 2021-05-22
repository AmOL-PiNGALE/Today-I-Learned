
# Code Formatting in Kotlin using ktlint

Kotlin is a very cool language and to keep the coolness of the language you need to write the codes in the desired format. But if you are not familiar with how to write clean code using Kotlin then don’t worry you need not learn something to achieve this, instead, you just have to use ktlint that is used for the same purpose.


What is ktlint?
If we look at the definition of ktlint from its website then it says that:
  - ktlint is an anti-bikeshedding Kotlin linter with built-in formatter.

In simpler words, we can think of ktlint as a static code analysis tool that is used to analyze the Kotlin code for you. It will check if you have written the code by following the Kotlin code guidelines or not. If not, then it will suggest some changes for you.

ktlint does the following tasks:
  1. can lint your code and suggest some changes that can be made to have the code according to the Kotlin guidelines.
  2. can format your code (if some formatting is needed).
  3. you can define your rules for a particular coding style

The whole ktlint process can be divided into two parts:
  1. Linting: It checks if your code is written according to the Kotlin code guidelines or not. If not then it will show the changes that can be made to bring the code to the preferred style.
  2. Formatting: If your code is not written according to the Kotlin code guidelines then you can use the formatting option to auto-format the code for you to match to the desired code guidelines.

There are three different approaches to include ktlink
To use ktlint from gradle, you can add following snippet to build.gradle

```groovy
apply plugin: "java"

repositories {
    jcenter()
}

configurations {
    ktlint
}

dependencies {
    ktlint "com.pinterest:ktlint:0.41.0"
    // additional 3rd party ruleset(s) can be specified here
    // just add them to the classpath (ktlint 'groupId:artifactId:version') and 
    // ktlint will pick them up
}

task ktlint(type: JavaExec, group: "verification") {
    description = "Check Kotlin code style."
    main = "com.pinterest.ktlint.Main"
    classpath = configurations.ktlint
    args "src/**/*.kt"
    // to generate report in checkstyle format prepend following args:
    // "--reporter=plain", "--reporter=checkstyle,output=${buildDir}/ktlint.xml"
    // see https://github.com/pinterest/ktlint#usage for more
}
check.dependsOn ktlint

task ktlintFormat(type: JavaExec, group: "formatting") {
    description = "Fix Kotlin code style deviations."
    main = "com.pinterest.ktlint.Main"
    classpath = configurations.ktlint
    args "-F", "src/**/*.kt"
}

```


To check if your code has some formatting errors or not, open the terminal of your Android studio and write the below command:
```
./gradlew ktlint
```
This will start running the ktlintCheck task and it will show some build failed error if your code has some formatting errors. Not only that, it will show you the exact error that is being encountered i.e. unexpected indentation or unexpected blank line.

Here, some lines can be auto-corrected while some lines can’t be auto-corrected. So, to fix the line that can be auto-corrected, you can use the below command in the terminal:
```
./gradlew ktlintFormat
```

To fix the error that cannot be fixed automatically, you have to fix it manually.


Some more useful resouces
------------------------------------
1. [https://ktlint.github.io/](https://ktlint.github.io/)
2. [https://github.com/pinterest/ktlint](https://github.com/pinterest/ktlint)
3. [https://blog.mindorks.com/code-formatting-in-kotlin-using-ktlint](https://blog.mindorks.com/code-formatting-in-kotlin-using-ktlint)