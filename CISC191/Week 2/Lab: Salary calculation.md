# Lab: Calculate salary using classes

## Objectives:
Understand how to apply classes and constructors 

## Task A (using classes)
1. Assignment Code:
```Java
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
      double result = 0.0;
      boolean keepLooking = true;
      int i = 0;

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

