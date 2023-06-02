# alertdialog
xml file-
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/txtAlert"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="200dp"
        android:textSize="25sp"
        android:text="Alert Dialog Box"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btnAlert"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="22dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp"
        android:text="Show Alert Dialog"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/txtAlert" />




</androidx.constraintlayout.widget.ConstraintLayout>


java file-
package com.example.alertdialog;

import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.content.DialogInterface;
import android.os.Bundle;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        @SuppressLint({"MissingInflatedId", "LocalSuppress"})
        Button show = findViewById(R.id.btnAlert);

        show.setOnClickListener(view -> {
            showAlertDialog();
        });

    }

    private void showAlertDialog() {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Alert Dialog");
        builder.setMessage("This is an alert dialog.");

        builder.setPositiveButton("OK", (dialogInterface, i) ->
                Toast.makeText(MainActivity.this,"OK Button Clicked!!",Toast.LENGTH_SHORT).show());

        builder.setNegativeButton("CANCEL", (dialogInterface, i) ->
                Toast.makeText(MainActivity.this, "CANCEL Button Clicked!!", Toast.LENGTH_SHORT).show());

        AlertDialog dialog = builder.create();
        dialog.show();

    }
}
