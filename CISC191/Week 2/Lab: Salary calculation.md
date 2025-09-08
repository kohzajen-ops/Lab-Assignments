# Lab: Calculate salary using classes

## Objectives:
Understand how to apply classes and constructors 

## Task A (using classes)
1. Assignment Code:
```Java
package SalaryCalc;

public class TaxTableTools {

    private int [] search =   {   0,  20000, 50000, 100000, Integer.MAX_VALUE };
    private double [] value = { 0.0,   0.10,  0.20,   0.30,              0.40 };
    private int nEntries;

    public TaxTableTools () {
        nEntries  = search.length;
    }

    public void setTables(int[] newSearch, double[] newValue) {
        if (newSearch.length != newValue.length) {
            throw new IllegalArgumentException("Search and value tables must have same length.");
        }
        search = newSearch;
        value = newValue;
        nEntries = search.length;
    }

    public double getValue(int searchArgument) {
        double result;
        boolean keepLooking;
        int i;

        result = 0.0;
        keepLooking = true;
        i = 0;

        while ((i < nEntries) && keepLooking) {
            if (searchArgument <= search[i]) {
                result = value[i];
                keepLooking = false;
            }
            else {
                ++i;
            }
        }

        return result;
    }
}
````

2. Assignment Code:
```Java
package SalaryCalc;

import java.util.Scanner;

public class IncomeTaxMain {

    public static int getInteger(Scanner input, String prompt) {
        int inputValue;

        System.out.println(prompt + ": ");
        inputValue = input.nextInt();

        return inputValue;
    }

    public static void main(String [] args) {
        final String PROMPT_SALARY = "\nEnter annual salary (-1 to exit)";
        Scanner scnr = new Scanner(System.in);
        int annualSalary;
        double taxRate;
        int taxToPay;

        int []    salary   = {   0,  20000, 50000, 100000, Integer.MAX_VALUE };
        double [] taxTable = { 0.0,   0.10,  0.20,   0.30,              0.40 };

        TaxTableTools table = new TaxTableTools();

        table.setTables(salary, taxTable);

        annualSalary = getInteger(scnr, PROMPT_SALARY);

        while (annualSalary >= 0) {
            taxRate = table.getValue(annualSalary);
            taxToPay= (int)(annualSalary * taxRate);
            System.out.println("Annual Salary: " + annualSalary +
                    "\tTax rate: " + taxRate +
                    "\tTax to pay: " + taxToPay);

            annualSalary = getInteger(scnr, PROMPT_SALARY);
        }
    }
}
````

## Notes on output:

Enter annual salary (-1 to exit): 
10000
Annual Salary: 10000	Tax rate: 0.1	Tax to pay: 1000

Enter annual salary (-1 to exit): 
50000
Annual Salary: 50000	Tax rate: 0.2	Tax to pay: 10000

Enter annual salary (-1 to exit): 
50001
Annual Salary: 50001	Tax rate: 0.3	Tax to pay: 15000

Enter annual salary (-1 to exit): 
100001
Annual Salary: 100001	Tax rate: 0.4	Tax to pay: 40000

Enter annual salary (-1 to exit): 
-1

Process finished with exit code 0

## Task B (using constructor overload)
1. Assignment Code:
```Java
package SalaryCalcu;

import java.util.Scanner;

public class TaxTableTools {

    private int [] search =   {   0, 20000, 50000, 100000,  Integer.MAX_VALUE };
    private double [] value = { 0.0,  0.10,  0.20,   0.30, 0.40 };
    private int nEntries;

    public TaxTableTools() {
        nEntries = search.length;
    }

    public TaxTableTools(int[] newSearch, double[] newValue) {
        if (newSearch.length != newValue.length) {
            throw new IllegalArgumentException("Search and value tables must have same length.");
        }
        search = newSearch;
        value  = newValue;
        nEntries = search.length;
    }

    public int getInteger(Scanner input, String prompt) {
        int inputValue = 0;

        System.out.println(prompt + ": ");
        inputValue = input.nextInt();

        return inputValue;
    }

    public double getValue(int searchArgument) {
        double result;
        boolean keepLooking;
        int i;

        result = 0.0;
        keepLooking = true;
        i = 0;

        while ((i < nEntries) && keepLooking) {
            if (searchArgument <= search[i]) {
                result = value[i];
                keepLooking = false;
            } else {
                ++i;
            }
        }
        return result;
    }
}
````

2. Assignment Code:
```Java
package SalaryCalcu;

import java.util.Scanner;

public class IncomeTaxMain {

    public static void main(String[] args) {
        final String PROMPT_SALARY = "\nEnter annual salary (-1 to exit)";
        Scanner scnr = new Scanner(System.in);
        int annualSalary;
        double taxRate;
        int taxToPay;
        int i; 

        int [] salaryRange = { 0, 30000, 60000, 80000, Integer.MAX_VALUE };
        double [] taxRates = { 0.0, 0.25, 0.35, 0.40, 0.45 };

        TaxTableTools table = new TaxTableTools(salaryRange, taxRates);


        annualSalary = table.getInteger(scnr, PROMPT_SALARY);

        while (annualSalary >= 0) {
            taxRate = table.getValue(annualSalary);
            taxToPay = (int)(annualSalary * taxRate);

            System.out.println("Annual Salary: " + annualSalary +
                    "\tTax rate: " + taxRate +
                    "\tTax to pay: " + taxToPay);

            annualSalary = table.getInteger(scnr, PROMPT_SALARY);
        }
    }
}
````

## Notes on output:
Enter annual salary (-1 to exit): 
10000
Annual Salary: 10000	Tax rate: 0.25	Tax to pay: 2500

Enter annual salary (-1 to exit): 
50000
Annual Salary: 50000	Tax rate: 0.35	Tax to pay: 17500

Enter annual salary (-1 to exit): 
70000
Annual Salary: 70000	Tax rate: 0.4	Tax to pay: 28000

Enter annual salary (-1 to exit): 
120000
Annual Salary: 120000	Tax rate: 0.45	Tax to pay: 54000

Enter annual salary (-1 to exit): 
-1

Process finished with exit code 0
