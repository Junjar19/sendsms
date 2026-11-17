
# Ex.No:3 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
Program to create and design an android application Send SMS using Intent.
Developed by: Junjar U
Registration Number : 212224230110
```

### MainActivity.java
```java
package com.example.exp3;


import android.Manifest;
import android.content.pm.PackageManager;
import android.telephony.SmsManager;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private static final int SMS_PERMISSION_CODE = 101;
    EditText etPhoneNumber, etMessage;
    Button btnSendSms;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etPhoneNumber = findViewById(R.id.etPhoneNumber);
        etMessage = findViewById(R.id.etMessage);
        btnSendSms = findViewById(R.id.btnSendSms);

        btnSendSms.setOnClickListener(v -> sendSms());
    }

    private void sendSms() {

        String phoneNumber =
                etPhoneNumber.getText().toString().trim();

        String message =
                etMessage.getText().toString().trim();

        if (phoneNumber.isEmpty()) {
            Toast.makeText(this,
                    "Enter phone number",
                    Toast.LENGTH_SHORT).show();
            return;
        }

        Intent intent = new Intent(Intent.ACTION_SENDTO);

        intent.setData(Uri.parse("smsto:" + Uri.encode(phoneNumber)));

        intent.putExtra("sms_body", message);

        try {
            startActivity(intent);
        } catch (android.content.ActivityNotFoundException e) {
            Toast.makeText(this,
                    "No SMS application found",
                    Toast.LENGTH_SHORT).show();
        }
    }
}

```

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="24dp"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        android:textSize="28sp"
        android:textStyle="bold"
        android:textColor="#000000"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="60dp"/>

    <EditText
        android:id="@+id/etPhoneNumber"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone"
        app:layout_constraintTop_toBottomOf="@id/tvTitle"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="40dp"/>

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="0dp"
        android:layout_height="120dp"
        android:hint="Enter Your Message"
        android:gravity="top"
        android:inputType="textMultiLine"
        app:layout_constraintTop_toBottomOf="@id/etPhoneNumber"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="20dp"/>

    <Button
        android:id="@+id/btnSendSms"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        app:layout_constraintTop_toBottomOf="@id/etMessage"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="25dp"/>

</androidx.constraintlayout.widget.ConstraintLayout>

```

## OUTPUT

<img width="1912" height="985" alt="image" src="https://github.com/user-attachments/assets/ba216f71-e1aa-43e3-b72f-e673c64dd1d3" />


<img width="1877" height="987" alt="image" src="https://github.com/user-attachments/assets/9df652b9-7b11-4375-a0c7-e0a7d3fac9e2" />



## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
