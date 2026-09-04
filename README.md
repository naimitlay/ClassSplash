Splash Iskan
====================

Creat new Class
=================

activity_main.xml
========================


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Page 1"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:textSize="40sp"
        android:textStyle="bold"
        android:textColor="#00796B"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />




</androidx.constraintlayout.widget.ConstraintLayout>

/////////////////////////////////////////////////////////////////////////////

activity_splash.xml
---------------------

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tvPageTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome to Class Splash Iskan!"
        android:textColor="#00796B"
        android:textSize="40sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/imgLauncher"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_chainStyle="packed" />

    <ImageView
        android:id="@+id/imgLauncher"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:layout_marginTop="24dp"
        android:contentDescription="Launcher Icon"
        android:src="@mipmap/ic_launcher"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/tvPageTitle" />

</androidx.constraintlayout.widget.ConstraintLayout>

=====================================================================
Splash.Java
-------------

package com.naim.classsplash;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class Splash extends AppCompatActivity {

    Handler handler = new Handler();


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_splash);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });


// প্রোগ্রাম এখানে শুরু

        handler.postDelayed(() -> {
            Intent intent = new Intent(Splash.this, MainActivity.class);
            startActivity(intent);
            finish(); // স্প্ল্যাশ স্ক্রিনটি বন্ধ করে দেবে
        }, 3000);  // ৩ সেকেন্ড সময়
       
    }//onCreate end
    
    // অতিরিক্ত সতর্কতা: স্ক্রিন বন্ধ হয়ে গেলে যেন ব্যাকগ্রাউন্ডে কোড না চলে
    protected void onDestroy() {
        super.onDestroy();
        handler.removeCallbacksAndMessages(null); // মেমোরি লিক আটকাবে
    }

    
}//end

========================================================================================================================

AndroidManifest
==================


<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.ClassSplash">
        <activity
            android:name=".MainActivity"
            android:exported="false" />
        <activity
            android:name=".Splash"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>


    </application>

</manifest>

=======================================================================================











