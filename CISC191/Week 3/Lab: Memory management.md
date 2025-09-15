# Memory management

## Objectives:
Understand how memory management works in Java 

## Task A (using classes)
1. Assignment Code:
```Java
public class Car {
    private String model;
    private int year;
    private double speed;

    public Car(String model, int year, double speed) {
        this.model = model;
        this.year = year;
        this.speed = speed;
    }

    public void accelerate() {
        speed += 10;
        System.out.println("The car is now going at " + speed + " km/h.");
    }

    public void displayDetails() {
        System.out.println("Model: " + model + ", Year: " + year + ", Speed: " + speed + " km/h.");
    }

    public static void main(String[] args) {
        Car myCar = new Car("Toyota Corolla", 2020, 60);
        myCar.displayDetails();
        myCar.accelerate();
        myCar.displayDetails();
    }
}
```

## Expected output
1. Memory Mapping: Stack and Heap

  Stack: Local variables and method calls are stored here. In this case, the main() method is called and resides on the stack. The myCar reference is a local variable in the main() method and will be stored in the stack. Method call information such as displayDetails() and accelerate() is also stored on the stack when they are executed.

  Heap: Objects are stored in the heap. When the line Car myCar = new Car("Toyota Corolla", 2020, 60); is executed: A new Car object is created on the heap with the model, year, and speed values and the myCar reference on the stack points to this object on the heap.

2. Garbage Collection

  If the reference variable myCar were to go out of scope (e.g., if the main() method finishes execution), then the object that myCar pointed to could be collected by the garbage collector. Since we are not explicitly nullifying myCar, the memory will be eligible for garbage collection after main() finishes running.

## This is my flowchart:
<img width="121" height="461" alt="Lab_ Memory management drawio" src="https://github.com/user-attachments/assets/e999dde6-30af-4f81-bf1d-9926de1e5b5a" />


## Challenges encountered while performing the lab:
At first, I struggled a bit with how to properly write a constructor to initialize the model, year, and speed attributes when creating an object. After that, I needed to clearly distinguish between instance variables and local variables in main(). Mapping how the object is stored in the heap and how the reference variable is stored in the stack was also really tricky for me.
