# RecyclerView
RecyclerViews the new way and improved way to do ListViews. This tutorial assumes that you know how to use ListViews, that you're comfortable with layouts, and can create an "empty" project

# Getting Started
Go ahead and create a new Android Studio project. Set your activity type that's generated to be an Empty Activity.


Once that's done open up `build.gradle (Module: app)` and enter in the following inside of the `dependencies` section


```gradle
    compile 'com.android.support:recyclerview-v7:23.0.1'
```


If you did that correctly your gradle file should like the one below and should sync up correctly


```gradle
apply plugin: 'com.android.application'

android {
    compileSdkVersion 23
    buildToolsVersion "23.0.1"

    defaultConfig {
        applicationId "ssa766.myapplication"
        minSdkVersion 16
        targetSdkVersion 23
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    testCompile 'junit:junit:4.12'
    compile 'com.android.support:appcompat-v7:23.0.1'
    compile 'com.android.support:recyclerview-v7:23.0.1'
}
```
