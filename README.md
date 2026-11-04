# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1. Start the application.
2. Create a new Android project in Android Studio.
3. Design the first screen with:
4. One EditText to accept a number.
5. One Button labeled FACTORIAL.
6. Create a second activity to display the result.
7. In MainActivity, read the number entered by the user.
8. Create an Explicit Intent to open SecondActivity.
9. Pass the entered number to SecondActivity using putExtra().
10. In SecondActivity, receive the number using getIntent().getStringExtra().
11. Convert the received value into an integer.
12. Calculate the factorial of the number using a for loop.
13. Display the factorial result in a TextView.
14. Run the application.
15. Verify that the second screen displays the correct factorial.
16. Stop the application.

## PROGRAM:
```
Program to print the text “ExplicitIntent”.
Developed by: KOWSHIK RAM S
Registration Number : 212225230143
```
## activity_main.xml :
```
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
        android:text="@string/enter_a_number"
        android:textSize="20sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.9" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="32dp"
        android:layout_marginEnd="32dp"
        android:layout_marginBottom="32dp"
        android:autofillHints="none"
        android:ems="10"
        android:hint="@string/enter_a_number"
        android:inputType="number"
        android:minHeight="48dp"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.5" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="32dp"
        android:text="@string/factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity.java :
```

package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText editText;
    Button button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText = findViewById(R.id.editTextText);
        button = findViewById(R.id.button);

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                String num = editText.getText().toString().trim();

                if (num.isEmpty()) {
                    editText.setError("Please enter a number");
                    return;
                }

                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                intent.putExtra("number", num);
                startActivity(intent);

            }
        });

    }
}
```
## activity2.xml :
```
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/result_placeholder"
        android:textSize="30sp"
        android:textStyle="bold"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```
## MainActivity2.java :
```

package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    TextView result;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity2);

        result = findViewById(R.id.result);

        String number = getIntent().getStringExtra("number");

        if (number != null && !number.isEmpty()) {
            try {
                int n = Integer.parseInt(number);
                long fact = 1;
                for (int i = 1; i <= n; i++) {
                    fact = fact * i;
                }
                result.setText("Factorial of " + n + " = " + fact);
            } catch (NumberFormatException e) {
                result.setText("Invalid number");
            }
        } else {
            result.setText("No number received");
        }

    }
}
```
## OUTPUT

<img width="1920" height="1080" alt="Screenshot (166)" src="https://github.com/user-attachments/assets/b93da20e-062a-42a9-90bd-fcf65c71e60d" />

<img width="1920" height="1080" alt="Screenshot (167)" src="https://github.com/user-attachments/assets/141c0bfe-9457-4a28-bcfc-f87f21a67519" />

## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
