# Sample

Sample to reproduce an error when try to use Compose Multiplatform with new multiplatform android library plugin.

Steps to reproduce:
1. Clone this repository.
2. Open it in Android Studio latest preview version or build it on terminal.
   
Using terminal:
```
./gradlew app:assembleDebug
```
3. Let it sync and build the project.
4. Observe the error in the build output.

```
Unable to find method ''void com.android.build.api.variant.KotlinMultiplatformAndroidComponentsExtension.onVariant(kotlin.jvm.functions.Function1)''
'void com.android.build.api.variant.KotlinMultiplatformAndroidComponentsExtension.onVariant(kotlin.jvm.functions.Function1)'
```

If you comment the following line in `build.gradle.kts` of the `shared` module:
```kotlin
    // alias(libs.plugins.kotlin.compose)
    // alias(libs.plugins.composeMultiplatform)
```
and sync again, the error disappears.

This project is built with Kotlin 2.3.0-Beta2 and AGP 9.0.0-alpha13

I'm not sure if it a bug in Compose Multiplatform or AGP, but I wanted to share this sample to help investigate the issue.