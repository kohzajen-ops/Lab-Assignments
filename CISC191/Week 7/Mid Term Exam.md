## Version 1

InventoryControlSystem:
```java
package MidTermExamVer1;

import java.util.Scanner;

public class InventoryControlSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Painkillers pk = new Painkillers();
        Bandages bd = new Bandages();
        Equipment eq = new Equipment();

        pk.updateItem("Tylenol", "Johnson & Johnson", 1.2);
        bd.updateItem("Elastic Bandage", "3M", 0.5);
        eq.updateItem("Thermometer", "Omron", 0.8);

        pk.displayItem();
        System.out.println();
        bd.displayItem();
        System.out.println();
        eq.displayItem();
    }
}
```

InventoryItem.java:
```java
package MidTermExamVer1;

class InventoryItem {
    protected String name;
    protected String company;
    protected double weight;

    public void updateItem(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void updateItem(String name) {
        this.name = name;
    }

    public void displayItem() {
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight: " + weight + " lbs");
    }
}

class Painkillers extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Painkiller Section");
        super.displayItem();
    }
}

class Bandages extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Bandage Section");
        super.displayItem();
    }
}

class Equipment extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Equipment Section");
        super.displayItem();
    }
}
```

## Version 2

InventoryControlSystem:
```java
package MidTermExamVer2;

import java.util.Scanner;

public class InventoryControlSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Painkillers pk = new Painkillers();

        try {
            System.out.print("Enter item name: ");
            String name = sc.nextLine();
            if (name.isEmpty()) throw new IllegalArgumentException("Name cannot be empty.");

            System.out.print("Enter company name: ");
            String company = sc.nextLine();

            System.out.print("Enter item weight (lbs): ");
            double weight = Double.parseDouble(sc.nextLine());

            pk.updateItem(name, company, weight);
            pk.displayItem();

        } catch (NumberFormatException e) {
            System.out.println("Error: Weight must be a number!");
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

InventoryItem.java:
```java
package MidTermExamVer2;

class InventoryItem {
    protected String name;
    protected String company;
    protected double weight;

    public void updateItem(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void updateItem(String name) {
        this.name = name;
    }

    public void displayItem() {
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight: " + weight + " lbs");
    }
}

class Painkillers extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Painkiller Section");
        super.displayItem();
    }
}

class Bandages extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Bandage Section");
        super.displayItem();
    }
}

class Equipment extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Equipment Section");
        super.displayItem();
    }
}
```

## Version 3
InventoryControlSystem:
```java
package MidTermExamVer3;

import java.util.Scanner;

public class InventoryControlSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Painkillers pk = new Painkillers();

        try {
            System.out.print("Enter item name: ");
            String name = sc.nextLine();

            System.out.print("Enter company name: ");
            String company = sc.nextLine();

            System.out.print("Enter weight (lbs): ");
            double weight = Double.parseDouble(sc.nextLine());

            System.out.print("Enter expiry date (YYYY-MM-DD): ");
            String expiry = sc.nextLine();

            System.out.print("Enter age group (Adult/Child/All): ");
            String age = sc.nextLine();

            pk.updateItem(name, company, weight, expiry, age);
            pk.displayItem();

        } catch (InvalidAgeGroupException e) {
            System.out.println("Custom Error: " + e.getMessage());
        } catch (NumberFormatException e) {
            System.out.println("Error: Weight must be a number!");
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

InventoryItem.java:
```java
package MidTermExamVer3;

class InventoryItem {
    protected String name;
    protected String company;
    protected double weight;

    public void updateItem(String name, String company, double weight) {
        this.name = name;
        this.company = company;
        this.weight = weight;
    }

    public void updateItem(String name) {
        this.name = name;
    }

    public void displayItem() {
        System.out.println("Name: " + name);
        System.out.println("Company: " + company);
        System.out.println("Weight: " + weight + " lbs");
    }
}

class InvalidAgeGroupException extends Exception {
    public InvalidAgeGroupException(String message) {
        super(message);
    }
}

class Painkillers extends InventoryItem {
    private String expiryDate;
    private String ageGroup;

    public void updateItem(String name, String company, double weight, String expiryDate, String ageGroup)
            throws InvalidAgeGroupException {
        if (!ageGroup.matches("(?i)(adult|child|all)")) {
            throw new InvalidAgeGroupException("Invalid age group. Use Adult, Child, or All.");
        }
        super.updateItem(name, company, weight);
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
    }

    @Override
    public void displayItem() {
        System.out.println("Painkiller Section");
        super.displayItem();
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
    }
}

class Bandages extends InventoryItem {
    private String expiryDate;
    private String ageGroup;
    private String waterproof;

    public void updateItem(String name, String company, double weight, String expiryDate, String ageGroup, String waterproof)
            throws InvalidAgeGroupException {
        if (!ageGroup.matches("(?i)(adult|child|all)")) {
            throw new InvalidAgeGroupException("Invalid age group. Use Adult, Child, or All.");
        }
        super.updateItem(name, company, weight);
        this.expiryDate = expiryDate;
        this.ageGroup = ageGroup;
        this.waterproof = waterproof;
    }

    @Override
    public void displayItem() {
        System.out.println("Bandage Section");
        super.displayItem();
        System.out.println("Expiry Date: " + expiryDate);
        System.out.println("Age Group: " + ageGroup);
        System.out.println("Waterproof: " + waterproof);
    }
}

class Equipment extends InventoryItem {
    @Override
    public void displayItem() {
        System.out.println("Equipment Section");
        super.displayItem();
    }
}
```
