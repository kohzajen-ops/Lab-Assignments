# Activity: GUI input and formatted text fields

## Objective

Write a code that takes user input and performs calculations

## Task
Assignment Code:
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class GUILab3 extends JFrame implements ActionListener {
    private JSpinner milesSpinner;
    private JButton convertButton;
    private JLabel kmLabel;

    public GUILab3() {
        setTitle("Miles to Kilometers Converter");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(300, 150);
        setLayout(new GridLayout(3, 2, 5, 5));

        add(new JLabel("Distance (miles):"));
        milesSpinner = new JSpinner(new SpinnerNumberModel(0.0, 0.0, 10000.0, 0.1));
        add(milesSpinner);

        convertButton = new JButton("Convert to km");
        convertButton.addActionListener(this);
        add(convertButton);

        kmLabel = new JLabel("Kilometers: ");
        add(kmLabel);

        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double miles = (double) milesSpinner.getValue();
            double km = miles * 1.60934;
            kmLabel.setText(String.format("Kilometers: %.2f km", km));
        } catch (Exception ex) {
            kmLabel.setText("Error: invalid input");
        }
    }

    public static void main(String[] args) {
        new GUILab3();
    }
}
```

## This is my flowchart:
<img width="161" height="761" alt="GUILab3 drawio" src="https://github.com/user-attachments/assets/f0b2f15d-dddf-4376-9497-c8021352cf0e" />


## Challenges encountered while performing the lab:
Learning from the first and second lab, I think this lab went pretty smooth.
