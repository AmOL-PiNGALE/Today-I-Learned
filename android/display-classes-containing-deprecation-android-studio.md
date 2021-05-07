
# Display Classes Containing Deprecation Android Studio

Looking at How to recompile with -Xlint:deprecation, add into root build.gradle:

```
allprojects {
	repositories {
		...
	}
    ...
    
    gradle.projectsEvaluated {
        tasks.withType(JavaCompile) {
            options.encoding = 'UTF-8'
            options.compilerArgs << "-Xlint:deprecation"
        }
    }
}
```

and start in Terminal:

```
./gradlew lint
```

or in Gradle menu:

gradle > app > Tasks > verification > lint

You can check the warning/errors in Gradle-Console/Run/Build tab


Some useful resouces
------------------------------------
1. [https://stackoverflow.com/questions/34807147/display-classes-containing-deprecation-android-studio](https://stackoverflow.com/questions/34807147/display-classes-containing-deprecation-android-studio)
2. [https://stackoverflow.com/questions/49711773/how-to-recompile-with-xlintdeprecation](https://stackoverflow.com/questions/49711773/how-to-recompile-with-xlintdeprecation)
3. [https://dominoc925.blogspot.com/2016/08/identifying-deprecated-classes-and.html](https://dominoc925.blogspot.com/2016/08/identifying-deprecated-classes-and.html)






