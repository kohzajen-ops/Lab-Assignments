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
