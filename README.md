# -<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/generateButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="50dp"
        android:text="Generate Password" />

    <TextView
        android:id="@+id/passwordTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20sp"
        android:layout_centerHorizontal="true"
        android:layout_below="@id/generateButton"
        android:layout_marginTop="20dp"/>

</RelativeLayout>



package com.example.myapplicationgenerator

import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val generateButton = findViewById<Button>(R.id.generateButton)
        val passwordTextView = findViewById<TextView>(R.id.passwordTextView)

        generateButton.setOnClickListener {
            val password = generatePassword()
            passwordTextView.text = password
        }
    }

    private fun generatePassword(): String {
        val letters = "abcdefghijklmnopqrstuvwxyz"
        val numbers = "0123456789"
        val password = StringBuilder()

        for (i in 0 until 10) {
            if (i % 2 == 0) {
                password.append(letters.random())
            } else {
                password.append(numbers.random())
            }
        }

        return password.toString()
    }
}
