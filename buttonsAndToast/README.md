# Buttons and Toast
This tutorial teaches you about how to add buttons in your Android App and then manipulate them using java. This tutorial assumes that you know how to create a base project. So go ahead and create a new Android project, make sure to choose Empty Activity as the activity type, and then leave the defaults for everything else.

## Add a button to your layout
The default activity_main.xml file looks like this:

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
    tools:context="saiavala.myapplication.MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!" />
</RelativeLayout>
```


Go ahead and remove the TextView tag and add in the Button tag as below:

```xml
<Button
    android:id="@+id/toastBtn"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="Click Me!" />
```

Notice here we are setting the width, height, and the text label that the button displays to the user. The "id" field is essentially the "name" of the button. The "id" field is what you'll use to reference the button and manipulate its actions in java.

After this, your activity_main.xml file should finally end up looking like this

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
    tools:context="saiavala.myapplication.MainActivity">

    <Button
        android:id="@+id/toastBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Click Me!"/>
</RelativeLayout>
```

## Manipulate the button
Now let's have handle the button actions! Go to MainActivity.java.

Outside of onCreate() declare the button

```java
Button toastButton;
```

Now instantiate the button within onCreate()

```java
toastButton = (Button) findViewById(R.id.toastBtn);
```

The above line creates a button object which references the Button tag in activity_main.xml whose id is "toastBtn"

Now lets create the button handler to show a toast message! While still in onCreate() and below the toastButton instantiation add in the following line.

```java
toastButton.setOnClickListener(new View.onClickListener() {
    @Override
    public void onClick(View v) {
        Toast.makeText(getApplicationContext(), "Hey Android!", Toast.LENGTH_LONG).show();
    }
});
```

In a button, you set the OnClickListener and override the onClick() function. The onClick() function does what like it sounds, it defines what the button does when you click on the button! What we're doing here is creating a Toast message which takes three parameters: context, message, and the length. Go ahead and mess around with the message that you want to display. If you want to change the length of time the message will show you've got two options: Toast.LENGTH_LONG and Toast.LENGTH_SHORT. Once you've defined your mesage and time, then use .show() to display the message.

Your final MainActivity.java should look like following

```java
package saiavala.myapplication;

import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    Button toastButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        toastButton = (Button) findViewById(R.id.toastBtn);

        toastButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(getApplicationContext(), "Hey Android!", Toast.LENGTH_LONG).show();
            }
        });
    }
}
```

## Running the app
Hit run, and click on the button and you should get the following message. If so, then you're done!

<img src="https://github.com/savala/tilAndroid/blob/master/buttonsAndToast/screenshots/appRun.png" width="300px" height="400px">
