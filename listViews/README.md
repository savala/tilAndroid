# ListViews
This tutorial teaches you how to create ListViews with string objects. We'll be using ArrayAdapter<String>, ArrayList<String>, and the ListView view item.


Let's get started. Go ahead and create a new Android project in Android Studio. Make sure to choose "Empty Activity" as your activity type and leave everything as default.

## Add ListView to Layout
Remove the TextView tag and add in the ListView tag in your activity_main.xml file


```xml
<ListView
    android:id="@+id/listView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"></ListView>
```


What we're doing here is creating a ListView with a reference point of "listView" as the id. We're also setting the width and height to fill up the entire space. After adding the ListView tag, your activity_main.xml file should look like the following


```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="ssa766.myapplication.MainActivity">

    <ListView
        android:id="@+id/listView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"></ListView>
</RelativeLayout>
```

## Add Data to the ListView
Now that we have the ListView in our layout, we need to have some data to show within the ListView. To do this, first navigate to MainActivity.java


First declare the ListView, ArrayAdapter<String>, and ArrayList<String> outside of the onCreate() function


```java
ListView listView;
ArrayList<String> data;
ArrayAdapter<String> arrayAdapter;
```


Inside onCreate() add the following


```java
listView = (ListView) findViewById(R.id.listView);

data = new ArrayList<String>();

// Create some dummy data with numbers
for (int i = 0; i < 40; i++) {
    data.add(String.valueOf(i));
}

// Initialize the ArrayAdapter, set the context, layout, and data
arrayAdapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, data);

// Tell the listView what adapter it's using
listView.setAdapter(arrayAdapter);
```

## Run the App
Now run the app and if your output looks something like the below image then you're done!


<img src="https://github.com/savala/tilAndroid/blob/master/listViews/screenshots/appRun.png" width="300px" height="400px">
