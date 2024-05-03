##### Previous [[Classes & Object]]

Let us see some important keywords and methods of class ```
1.this 2.final 3.finalize() 4.constructors ```

### The `this` Keyword:
The `this` keyword in Java refers to the current instance of the class. It can be used inside a method or a constructor of a class to refer to the current object. This is particularly useful when you want to differentiate between instance variables and parameters with the same name.

```java
class Person {
    private String name;

    public Person(String name) {
        this.name = name; // 'this' refers to the current object's instance variable
    }

    public void displayName() {
        System.out.println("Name: " + this.name);
    }

	public static void main(String args[]){
		Person hari = new Person("Hari");
		hari.displayName();
	}
}
```

In the above example, `this.name` refers to the `name` instance variable of the `Person` class.

### The `final` Keyword:
The `final` keyword in Java is used to declare constants, prevent method overriding, and ensure immutability of variables. When applied to a variable, it means the variable can only be assigned once.

```java
class Constants {
    public static final int MAX_COUNT = 100;
    public final String name;

    public Constants(String name) {
        this.name = name; // 'final' instance variable must be initialized in the constructor
    }
}
```

Here, `MAX_COUNT` is a constant and `name` is a final instance variable that must be initialized in the constructor.

### The `finalize()` Method:
The `finalize()` method is called by the garbage collector on an object before it is reclaimed. It can be overridden to perform cleanup tasks or release resources associated with the object.

```java
class Resource {
    private String name;

    public Resource(String name) {
        this.name = name;
    }

    protected void finalize() {
        System.out.println("Cleaning up resource: " + this.name);
        // Cleanup code here
    }
}
```

### Constructors and Inheritance:
In Java, constructors are special methods used to initialize objects. When a subclass is created, the constructor of the superclass is automatically called before the constructor of the subclass executes.

```java
class Animal {
    public Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal {
    public Dog() {
        System.out.println("Dog constructor called");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
    }
}
```

In this example, creating a `Dog` instance (`new Dog()`) will invoke the constructor of `Animal` first (`Animal()`), followed by the constructor of `Dog` (`Dog()`). This is due to inheritance, where the superclass constructor is always called implicitly or explicitly by the subclass constructor.

### Explicitly Calling Superclass Constructors:
If the superclass has parameterized constructors, and there is no default (no-argument) constructor provided explicitly, the subclass constructor must explicitly call one of the superclass constructors using `super()`.

```java
class Vehicle {
    private String color;

    public Vehicle(String color) {
        this.color = color;
    }
}

class Car extends Vehicle {
    private String model;

    public Car(String color, String model) {
        super(color); // Call to superclass constructor
        this.model = model;
    }
}
```

In this example, the `Car` constructor explicitly calls `super(color)` to initialize the `color` attribute inherited from `Vehicle`.

These examples should help clarify and expand upon the topics of constructors, inheritance, `this` keyword, `final` keyword, and finalization methods in Java. Each of these concepts plays a crucial role in object-oriented programming in Java.

##### Next [[New, Wrapper Class and Garbage Collection]]