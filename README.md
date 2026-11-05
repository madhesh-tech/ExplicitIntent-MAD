# EXPERIMENT 2B :To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.
## NAME : MADHESH I
## REGISTRATION NUMBER : 212224220055


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Start app → show first screen.

Step 2 : User enters a number in the box.

Step 3 :User presses the Factorial button.

Step 4 :Read the number from the box.

Step 5 :Send this number to the second screen using explicit intent.

Step 6: Open the second screen.

Step 7: Second screen receives the number.

Step 8 :Calculate factorial of the number.

Step 9 :Show the factorial result in a TextView.





## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: MADHESH I
Registeration Number : 212224220055
*/
```
MainActivity.java

```java
package com.example.mulexp2b;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity
{

    EditText numberInput;
    Button factorialBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        numberInput = findViewById(R.id.editTextNumber);
        factorialBtn = findViewById(R.id.buttonFactorial);

        factorialBtn.setOnClickListener(new View.OnClickListener()
        {
            @Override
            public void onClick(View v)
            {
                String numStr = numberInput.getText().toString();
                if (!numStr.isEmpty())
                {
                    int number = Integer.parseInt(numStr);
                    Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                    intent.putExtra("number", number);
                    startActivity(intent);
                }
            }
        });
    }
}

```
activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.486" />

    <Button
        android:id="@+id/buttonFactorial"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber"
        app:layout_constraintVertical_bias="0.468" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="312dp"
        android:layout_height="87dp"
        android:text="Explicit Intent"
        android:textColor="#FF5722"
        android:textSize="48sp"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.494"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.747" />
</androidx.constraintlayout.widget.ConstraintLayout>

```

MainActivity2.java

```java
package com.example.mulexp2b;

import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity
{

    TextView resultView;

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        resultView = findViewById(R.id.textViewResult);
        int number = getIntent().getIntExtra("number", 0);
        long fact = factorial(number);
        resultView.setText("Factorial of " + number + " = " + fact);
    }
    private long factorial(int n)
    {
        long result = 1;
        for (int i = 1; i <= n; i++)
        {
            result *= i;
        }
        return result;
    }
}
```
activity_main2.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="231dp"
        android:layout_height="65dp"
        android:text="Result will appear here"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.588" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="325dp"
        android:layout_height="124dp"
        android:text="Explicit Intent"
        android:textColor="#FF5722"
        android:textSize="48sp"
        app:layout_constraintBottom_toTopOf="@+id/textViewResult"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.667" />
</androidx.constraintlayout.widget.ConstraintLayout>
```




## OUTPUT

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/f0f84110-d69a-46b5-aa38-7499c77bb6a2" />

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/674beed5-a629-4f3a-b45b-4f03cb5aab40" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


