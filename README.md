# Ex.No:3 Create Your Own Content Providers to get Contacts details.


## AIM:

To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min. required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “Ex03″ and click Next. 

Step 3: Then select the Empty Activity and click Next. Finally click Finish.

Step 4: Design layout in activity_main.xml.

Step 5: Get contacts details and Display details give in MainActivity file.

Step 6: Launch an emulator and run the application.

## PROGRAM:

```
/*
Program to print the text create your own content providers to get contacts details.
Developed by: J .RITHANIEPRIYANKA
Registeration Number : 212220230039
*/
```
#### Activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

<Button
    android:id="@+id/button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="get_contacts"
    android:onClick="btnGetContactPressed"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    tools:ignore="UsingOnClickInXml" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
#### MainActivity.java
```
package com.example.exp3;

        import androidx.appcompat.app.AppCompatActivity;
        import androidx.core.app.ActivityCompat;
        import androidx.core.content.ContextCompat;

        import android.Manifest;
        import android.annotation.SuppressLint;
        import android.content.ContentResolver;
        import android.content.pm.PackageManager;
        import android.database.Cursor;
        import android.net.Uri;
        import android.os.Bundle;
        import android.provider.ContactsContract;
        import android.util.Log;
        import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    public void btnGetContactPressed(View v){
        getPhoneContacts();
    }
    private void getPhoneContacts(){
        if(ContextCompat.checkSelfPermission(this , Manifest.permission.READ_CONTACTS)
                != PackageManager.PERMISSION_GRANTED)
        {
            ActivityCompat.requestPermissions(this, new String[] {Manifest.permission.READ_CONTACTS}, 0) ;

        }
        ContentResolver contentResolver = getContentResolver();
        Uri uri= ContactsContract.CommonDataKinds.Phone.CONTENT_URI;
        @SuppressLint("Recycle") Cursor cursor = contentResolver.query(uri, null , null,null,null);
        Log.i("CONTACT_PROVIDER_DEMO","TOTAL # of Contacts ::: "+ cursor.getCount());
        if (cursor.getCount() > 0) {
            while(cursor.moveToNext()){
                @SuppressLint("Range") String contactName = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));
                @SuppressLint("Range") String contactNumber = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));

                Log.i("CONTACT_PROVIDER_DEMO","Contact Name :::  "+ contactName+"   PH #   :::"+ contactNumber);
            }
        }
    }

}

```
#### AndroidManifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.example.exp3">

<uses-permission android:name="android.permission.READ_CONTACTS"></uses-permission>
<uses-permission android:name="android.permission.WRITE_CONTACTS"></uses-permission>

<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/Theme.EXP3">
    <activity
        android:name=".MainActivity"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
```

## OUTPUT:
![JAVA EXP3-A](https://user-images.githubusercontent.com/75235132/169340840-df1906e4-4f23-4cb7-b6fe-f403eb1b06eb.jpg)
![JAVA-EXP3-B](https://user-images.githubusercontent.com/75235132/169340960-608c6d85-55ca-4034-b128-48146c36d631.jpg)
![JAVA-EXP3-C](https://user-images.githubusercontent.com/75235132/169341015-3e0e2ad1-e928-4e60-8c87-83dbcb8936bb.jpg)
![JAVA-EXP3-D](https://user-images.githubusercontent.com/75235132/169341103-9185b3ea-78a2-4936-bc1c-d2d2e9075957.jpg)

## RESULT:

Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
