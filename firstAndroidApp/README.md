# Creating your first Android App
This tutorial is to get your started with loading up a default Android App and being able to run the application. Note this assumes that you have the sdk installed. If not please feel free to check out the [getting started tutorial](../gettingStarted/README.md).

## Getting Started
When you first open up Android Studio, you'll be presented with a welcome screen like so
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/welcomeScreen.png "Welcome Screen")


Go ahead and click on "Start a new Android Studio project" and then you will be presented with a screen that tells you to choose the target Android devices that you want your app to be compatible with
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/targetDevice.png "Target Devices")


Click next and then you'll see a screen that asks you to add a new activity
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/chooseDefault.png "Choose Activity")


Choose Empty Activity and then proceed further and define the Activity Name and Layout Name. Go ahead and leave the default values
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/emptyActivityName.png "Main Activity Name")


Click finish and you'll then see Android Studio do a bunch of stuff and you'll be presented with all the code and goodies to get going with your Android App!

## Quick Description everything
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/mainScreen.png "Main Screen")


Take a look at the left side of the screen. You'll see a list of all the files that make up your Android App on the left. You'll notice AndroidManifest.xml, java folder, and the res folder. Don't worry about everything yet, I'll go into more details about these in later tutorials. For now understand that the AndroidManifest is where you'll declare your activities and various permissions that your app has. The java/ folder will contain all your java code haha. The res/ folder contains your images, layouts, strings, styles, and various other files that will help you define your UI.


Now take a look at the editor. You'll notice MainActivity.java and activity_main.xml. In android you'll define your layouts and "views" within xml. You can avoid doing this in xml, but for now go ahead with this. The way I like to think about it is: define your layouts / UI in xml, and then use Java to go and maninpulate them.

## activity_main.xml
![alt text](https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/layout.png "Layout")


This might look kind of confusing at first, but don't worry about it. What this is doing here is setting the type of layout you want (RelativeLayout) and then putting a TextView tag. In Android, the various elements that you see on screen are "views". There's TextView (show plain text), Button, EditText (input box), ListView (show lists), and much more.

## MainActivity.java
Now that you kinda know what the layout file does, how can we manipulate it? Well this is where MainActivity.java comes in. Notice here you'll see
```java
public void onCreate(Bundle savedInstanceState) {
    ...
}
```

onCreate() is essentially like the main() function in java. This is the function that's called when you launch your app. If you were wondering how this java file knows to interact with the layout file, notice in the onCreate() function there's a line that says

```java
setContentView(R.layout.activity_main);
```


What is R? Well when your app is built, any references that you have defined in xml and such can be referred using the R.java file. So if I create more layouts like "xyz.xml" I can refer to it by using R.layout.xyz. As this  


With the above line you're essentially enabling the MainActivity.java access to manipulate the ui elements that you've defined in activity_main.xml

## Running the App
Go ahead and press the green "play" button in Android studio. If you have the Android sdk installed and have a virtual device created, then the app should build and then launch. If successful you should see something like this:

<img src="https://github.com/savala/tilAndroid/blob/master/firstAndroidApp/screenshots/appRun.png" width="300px" height="300px">

And you've just run your first Android App!
