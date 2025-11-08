# GUI2

## Objective

Write a code that takes user input and performs calculations

## Task
Assignment Code:
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.text.NumberFormat;

public class GUILab2 extends JFrame implements ActionListener {
    private JFormattedTextField milesField;
    private JButton convertButton;
    private JLabel kmLabel, mLabel, feetLabel;

    public GUILab2() {
        setTitle("Distance Converter");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(400, 200);
        setLayout(new GridLayout(5, 2, 5, 5));

        add(new JLabel("Distance (miles):"));
        NumberFormat numberFormat = NumberFormat.getNumberInstance();
        milesField = new JFormattedTextField(numberFormat);
        milesField.setColumns(10);
        add(milesField);

        convertButton = new JButton("Convert");
        convertButton.addActionListener(this);
        add(convertButton);

        kmLabel = new JLabel("Kilometers: ");
        add(kmLabel);
        mLabel = new JLabel("Meters: ");
        add(mLabel);
        feetLabel = new JLabel("Feet: ");
        add(feetLabel);

        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double miles = ((Number)milesField.getValue()).doubleValue();

            double km = miles * 1.60934;
            double meters = km * 1000;
            double feet = miles * 5280;

            kmLabel.setText(String.format("Kilometers: %.2f km", km));
            mLabel.setText(String.format("Meters: %.2f m", meters));
            feetLabel.setText(String.format("Feet: %.2f ft", feet));
        } catch (Exception ex) {
            kmLabel.setText("Please enter a valid number.");
            mLabel.setText("");
            feetLabel.setText("");
        }
    }

    public static void main(String[] args) {
        new GUILab2();
    }
}
```

## This is my flowchart:
<img width="201" height="761" alt="GUILab2 drawio" src="https://github.com/user-attachments/assets/a9066bbf-e339-453e-91f1-30c44babfea7" />

## Challenges encountered while performing the lab:
Learning from my mistakes from the first lab, I didn't forget setVisible(true). However, deciding between "kilometres” and “kilometers" got me thinking a bit.
