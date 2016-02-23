# Intents and Passing Data between Multiple Activities
This tutorial teaches you about Intents which is a fundamental concept in Android App development for message passing. In this tutorial we'll be using Intents, EditText, Button, TextView, and send a message between two activities: MainActivity.java and SecondActivity.java.

Let's get started. Go ahead and create a new Android project in Android Studio. Make sure to choose "Empty Activity" as your activity type and leave everything as default.

## activity_main.xml
Remove the default TextView tag in activity_main.xml and add in EditText and Button tags like so

```xml
<EditText
    android:id="@+id/inputEditText"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Enter some text!"/>
<Button
    android:id="@+id/submitBtn"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_below="@id/inputEditText"
    android:text="@string/submit"/>
```


What we're doing here is creating an EditText field with a reference point of "inputEditText" and a Button with a reference point of "submitBtn". After adding the two tags, your activity_main.xml file should look like the following


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

    <EditText
        android:id="@+id/inputEditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter some text!"/>
    <Button
        android:id="@+id/submitBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/inputEditText"
        android:text="@string/submit"/>

</RelativeLayout>
```


## Update strings.xml
Notice you might have an error with the Button tag. That's because we need to declare a string called "submit". Open up strings.xml which is in res/values and update strings.xml


```xml
<string name="submit">Submit</string>
```


Your strings.xml file should end up looking like this


```xml
<resources>
    <string name="app_name">My Application</string>
    <string name="submit">Submit</string>
</resources>
```


## Update MainActivity.java
Declare the EditText and Button outside of the onCreate() function


```java
EditText inputEditText;
Button submitBtn;
```


Initialize the views inside the onCreate() function, and override the submitBtn so that when you click on it, it gets the message inside of the EditText object and send it over to SecondActivity.java


```java
inputEditText = (EditText) findViewById(R.id.inputEditText);
submitBtn = (Button) findViewById(R.id.submitBtn);

submitBtn.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        String input = inputEditText.getText().toString();
        if (input != null && !input.equals("")) {
            Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
            intent.putExtra("inputText", input);
            startActivity(intent);
        }
    }
});
```


Notice the Intent object. We're initalizing the intent object with the current application context and then the Activity that we want to send our message to. In order to send the data from the EditText object, we use the putExtra() function, specify the "key" and the value (the input message). The key is what we'll use in SecondActivity in order to retreive the value.


After doing all of that, our MainActivity.java file should look like the following:


```java
package ssa766.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText inputEditText;
    Button submitBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        inputEditText = (EditText) findViewById(R.id.inputEditText);
        submitBtn = (Button) findViewById(R.id.submitBtn);

        submitBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String input = inputEditText.getText().toString();
                if (input != null && !input.equals("")) {
                    Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
                    intent.putExtra("inputText", input);
                    startActivity(intent);
                }
            }
        });

    }
}
```

Now that we have this, let's create the SecondActivity


## Create Second Activity and layout file
Go to the left hand side of the screen and create the SecondActivity. To do this right click on the project package inside the java/ folder, go to new -> Activity -> Empty Activity. Change the activity name to be SecondActivity. This will automatically change the layout name to activity_second.xml as well.


## Add a TextView to activity_second.xml
Open up activity_second.xml and add in a TextView tag like so


```xml
<TextView
    android:id="@+id/sentText"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:textSize="40sp"/>
```

Your activity_second.xml file should end up looking like this:


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
    tools:context="ssa766.myapplication.SecondActivity">

    <TextView
        android:id="@+id/sentText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="40sp"/>

</RelativeLayout>
```


## Display the message in SecondActivity.java
You're almost there! Open up SecondActivity and declare a TextView object outside of the onCreate() function


```java
TextView sentTextView;
```


Now inside the onCreate() function, get the Intent (comes from MainActivity), initialize the TextView, get the message and set it as the text for the TextView.


```java
Intent intent = getIntent();

sentTextView = (TextView) findViewById(R.id.sentText);
sentTextView.setText(intent.getStringExtra("inputText"));
```


Your SecondActivity.java file should end up looking like so:


```java
package ssa766.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

    TextView sentTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        Intent intent = getIntent();

        sentTextView = (TextView) findViewById(R.id.sentText);
        sentTextView.setText(intent.getStringExtra("inputText"));
    }
}
```


## Running the Application
Now run the app! If all goes well then you should see the following screens / set of actions.

<img src="https://github.com/savala/tilAndroid/blob/master/intentsPassingDataMultipleActivities/screenshots/appRun.gif" width="350px">
