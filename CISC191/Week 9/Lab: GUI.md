# GUI

## Objective

Write a code that takes user input and performs calculations

## Task
Assignment Code:
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class GUILab extends JFrame implements ActionListener {
    private JTextField wageField, hoursField;
    private JButton calculateButton;
    private JLabel resultLabel;

    public GUILab() {
        setTitle("Yearly Salary Calculator");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(350, 200);
        setLayout(new GridLayout(4, 2, 5, 5));

        add(new JLabel("Hourly Wage ($):"));
        wageField = new JTextField();
        add(wageField);

        add(new JLabel("Hours per Week:"));
        hoursField = new JTextField();
        add(hoursField);

        calculateButton = new JButton("Calculate Yearly Salary");
        calculateButton.addActionListener(this);
        add(calculateButton);

        resultLabel = new JLabel("Yearly Salary: ");
        add(resultLabel);

        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double wage = Double.parseDouble(wageField.getText());
            double hours = Double.parseDouble(hoursField.getText());
            double yearlySalary = wage * hours * 52;
            resultLabel.setText(String.format("Yearly Salary: $%.2f", yearlySalary));
        } catch (NumberFormatException ex) {
            resultLabel.setText("Please enter valid numbers.");
        }
    }

    public static void main(String[] args) {
        new GUILab();
    }
}
```

## This is my flowchart:
<img width="161" height="761" alt="GUILab drawio" src="https://github.com/user-attachments/assets/9c723c19-c53e-4207-bb51-48b06b4c2c96" />

## Challenges encountered while performing the lab:
Slight slip up in my opinion but I forgot to call setVisible(true) so the window didn’t show up, and I accidentally used *12 instead of *52 when calculating the yearly salary.
