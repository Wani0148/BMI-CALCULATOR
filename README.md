# BMI TRACKER NURUL SYAZWANI BINTI MUHD ISMAIDI 2020482832


MainActivity
package com.example.myapplication;

import android.os.Bundle;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import android.view.View;

public class MainActivity extends AppCompatActivity {
    private EditText height;
    private EditText weight;
    private TextView result;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        height = (EditText) findViewById(R.id.height);
        weight = (EditText) findViewById(R.id.weight);
        result = (TextView) findViewById(R.id.result);
    }

    public void calculateBMI(View v){
        String heightStr = height.getText().toString();
        String weightStr = weight.getText().toString();


        float heightValue = Float.parseFloat(heightStr)/100;
        float weightValue = Float.parseFloat(weightStr);

        float bmi = weightValue/(heightValue*heightValue);
        displayBMI(bmi);

    }
    private void displayBMI(float bmi){
        String bmiCategory;
        String healthRisk;
        String bmiResult;
        if (Float.compare(bmi,18.4f)<=0){
            bmiCategory = getString(R.string.underweight);
            healthRisk = getString(R.string.malnutritionRisk);
        }else if (Float.compare(bmi,18.5f)>=0 && Float.compare(bmi,24.9f)<=0){
            bmiCategory = getString(R.string.normalWeight);
            healthRisk = getString(R.string.lowRisk);
        }else if (Float.compare(bmi,25f)>=0 && Float.compare(bmi,29.9f)<=0){
            bmiCategory = getString(R.string.overweight);
            healthRisk = getString(R.string.enhancedRisk);
        }else if (Float.compare(bmi,30f)>=0 && Float.compare(bmi,34.9f)<=0){
            bmiCategory = getString(R.string.moderatelyObese);
            healthRisk = getString(R.string.mediumRisk);
        }else if (Float.compare(bmi,35f)>=0 && Float.compare(bmi,39.9f)<=0){
            bmiCategory = getString(R.string.severelyObese);
            healthRisk = getString(R.string.highRisk);
        }else{
            bmiCategory = getString(R.string.very_severelyObese);
            healthRisk = getString(R.string.very_severelyRisk);
        }
        bmiResult = bmi + "\n\n" + bmiCategory + "\n" + healthRisk;
        result.setText(bmiResult);
    }
}

activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    android:paddingLeft="16dp"
    android:paddingTop="16dp"
    android:paddingRight="16dp"
    android:paddingBottom="16dp"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="48dp"
        android:layout_marginBottom="1dp"
        android:text="@string/height"
        android:textSize="20dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/height"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/height"
        android:layout_width="0dp"
        android:layout_height="wrap_content"

        android:layout_marginBottom="16dp"
        android:inputType="number||numberDecimal"
        android:textColor="#AF155D"
        android:textSize="25dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/textView2"
        app:layout_constraintEnd_toEndOf="@+id/weight"
        app:layout_constraintStart_toStartOf="@+id/textView" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="48dp"
        android:layout_marginEnd="50dp"
        android:layout_marginBottom="2dp"
        android:text="@string/weight"
        android:textSize="20dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/weight"
        app:layout_constraintEnd_toStartOf="@+id/button"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/weight"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="175dp"
        android:layout_marginEnd="16dp"
        android:inputType="number||numberDecimal"
        android:textColor="#AF155D"
        android:textSize="25dp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="@+id/textView2"
        app:layout_constraintTop_toTopOf="parent" />

    <Button

        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="128dp"
        android:textSize="15dp"
        android:onClick="calculateBMI"
        android:text="CALCULATE"

        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/weight" />

    <TextView
        android:id="@+id/result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="30dp"
        android:layout_marginTop="13dp"
        android:text="@string/result"
        android:textSize="20dp"
        android:textStyle="bold"
        android:gravity="center"
        app:layout_constraintStart_toStartOf="@+id/button"
        app:layout_constraintTop_toBottomOf="@+id/button" />


</androidx.constraintlayout.widget.ConstraintLayout>

themes.xml

<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="Theme.BMICalculator" parent="Theme.MaterialComponents.DayNight.DarkActionBar">
        <!-- Primary brand color. -->
        <item name="colorPrimary">@color/purple_200</item>
        <item name="colorPrimaryVariant">@color/purple_500</item>
        <item name="colorOnPrimary">@color/white</item>
        <!-- Secondary brand color. -->
        <item name="colorSecondary">@color/teal_200</item>
        <item name="colorSecondaryVariant">@color/teal_700</item>
        <item name="colorOnSecondary">@color/black</item>
        <!-- Status bar color. -->
        <item name="android:statusBarColor" tools:targetApi="l">?attr/colorPrimaryVariant</item>
        <!-- Customize your theme here. -->
    </style>
</resources>

string.xml

<resources>
<string name="app_name">BMI TRACKER</string>
<string name="calc">BMI CALCULATOR</string>
<string name="record">BMI RECORD</string>
<string name="height">Height</string>
<string name="weight">Weight</string>
<string name="result">Result</string>
<string name="underweight">Underweight</string>
<string name="malnutritionRisk">Malnutrition Risk</string>
<string name="normalWeight">Normal Weight</string>
<string name="lowRisk">Low Risk</string>
<string name="overweight">Overweight</string>
<string name="enhancedRisk">Enhanced Risk</string>
<string name="moderatelyObese">Moderately Obese</string>
<string name="mediumRisk">Medium Risk</string>
<string name="severelyObese">Severely Obese</string>
<string name="highRisk">High Risk</string>
<string name="very_severelyObese">Very Severely Obese</string>
<string name="very_severelyRisk">Very Severely Risk</string>

</resources>

colors.xml

<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="purple_200">#F30473</color>
    <color name="purple_500">#AF155D</color>
    <color name="purple_700">#FF3700B3</color>
    <color name="teal_200">#FF03DAC5</color>
    <color name="teal_700">#FF018786</color>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
</resources>
