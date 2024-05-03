##### Previous [[OOPS/Object Oriented Programming System ( OOPS )/Principles of OOPs - Polymorphism|Principles of OOPs - Polymorphism]]

Abstraction and Encapsulation are two important concepts in object-oriented programming, particularly in Java. They help in designing modular and maintainable code by hiding implementation details and providing a clear interface for interacting with objects.

## Abstraction:

Abstraction is the process of representing complex real-world entities as simplified models in software. It focuses on capturing essential characteristics and behavior while hiding unnecessary details. In Java, abstraction is achieved through abstract classes and interfaces.

### Abstraction in Object-Oriented Programming:

In OOP, abstraction is achieved by creating classes that represent abstract concepts or entities. These classes define the common characteristics and behavior of a group of related objects, without specifying the specific details of each object. Abstraction helps in creating a clear separation between the abstract concept and its implementation.

Abstraction is often associated with two main concepts:

1. Abstract Data Types (ADTs):  
    Abstract data types represent a specific concept or data structure and define the operations that can be performed on that data. They provide a high-level view of the data and hide the implementation details.
    
    For example, consider the abstract data type "Stack." It represents a collection of elements with a "last in, first out" (LIFO) behavior. The Stack ADT defines operations like "push" (to add an element), "pop" (to remove the most recently added element), and "isEmpty" (to check if the stack is empty). The implementation details, such as whether an array or linked list is used internally, are hidden from the user of the Stack ADT.
    
2. Interfaces:  
    Interfaces in Java are a way to define a contract that a class must adhere to. They specify a set of methods that a class implementing the interface must provide. Interfaces allow for achieving abstraction by defining a common interface that multiple classes can implement, enabling polymorphism and loose coupling.
    
    For example, the Java Collections framework provides interfaces like List, Set, and Map. These interfaces define common operations that different implementations (e.g., ArrayList, LinkedList, HashSet, TreeMap) must support. By programming to the interface (e.g., List) instead of a specific implementation (e.g., ArrayList), we achieve abstraction, and the specific implementation details are hidden.

Example of Abstraction:

1. Example 1
```java
abstract class Animal {
    abstract void makeSound();
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Dog barks.");
    }
}

class Cat extends Animal {
    void makeSound() {
        System.out.println("Cat meows.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        Animal cat = new Cat();

        dog.makeSound(); // Output: "Dog barks."
        cat.makeSound(); // Output: "Cat meows."
    }
}
```

In this example, the `Animal` class is an abstract class with an abstract method `makeSound()`. The `Dog` and `Cat` classes extend the `Animal` class and provide their own implementation of the `makeSound()` method. By defining `Animal` as an abstract class, we create a level of abstraction and ensure that any concrete subclass of `Animal` must provide an implementation for the `makeSound()` method. The `Main` class demonstrates how we can create instances of the concrete subclasses (`Dog` and `Cat`) and invoke the `makeSound()` method, which results in different outputs based on the specific implementation in each subclass.

2. Example 2
Certainly! Let's consider an example of abstraction using vehicles.

```java
interface Vehicle {
    void start();
    void stop();
}

class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car started.");
    }

    @Override
    public void stop() {
        System.out.println("Car stopped.");
    }
}

class Motorcycle implements Vehicle {
    @Override
    public void start() {
        System.out.println("Motorcycle started.");
    }

    @Override
    public void stop() {
        System.out.println("Motorcycle stopped.");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle car = new Car();
        Vehicle motorcycle = new Motorcycle();

        car.start(); // Output: "Car started."
        car.stop();  // Output: "Car stopped."

        motorcycle.start(); // Output: "Motorcycle started."
        motorcycle.stop();  // Output: "Motorcycle stopped."
    }
}
```

In this example, we have an interface called `Vehicle`, which defines two methods: `start()` and `stop()`. The `Car` and `Motorcycle` classes implement the `Vehicle` interface and provide their own implementations for the `start()` and `stop()` methods.

By using the `Vehicle` interface, we create an abstraction of a general vehicle concept without specifying the internal details of each vehicle type. Both `Car` and `Motorcycle` are considered vehicles and must implement the methods defined in the `Vehicle` interface.

In the `Main` class, we create instances of `Car` and `Motorcycle` using the `Vehicle` interface reference. We can call the `start()` and `stop()` methods on these instances, and the appropriate implementation for each vehicle type is executed.

This example demonstrates abstraction by providing a clear separation between the abstract concept of a vehicle (defined by the `Vehicle` interface) and its specific implementations (`Car` and `Motorcycle`). The user of the `Vehicle` interface does not need to be concerned with the internal details of each vehicle type; they can interact with the objects through the common interface methods. This abstraction allows for code modularity, flexibility, and easier maintenance.

## Encapsulation:

Encapsulation is the practice of bundling data and methods that operate on that data into a single unit, called a class. It helps in achieving data abstraction, data hiding, and data protection. In encapsulation, the internal state of an object is kept private, and external access is controlled through methods.

In Java, encapsulation is typically achieved by declaring class variables as private and providing public getter and setter methods to access and modify the internal state of the object. This way, the implementation details are hidden from the outside world, and access to the object's data is controlled.

Example of Encapsulation:

```java
class Person {
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 0) {
            this.age = age;
        } else {
            System.out.println("Invalid age!");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("John");
        person.setAge(25);

        System.out.println("Name: " + person.getName());
        System.out.println("Age: " + person.getAge());
    }
}
```

In this example, the `Person` class encapsulates the `name` and `age` data fields. These fields are declared as private, preventing direct access from outside the class. The class provides public getter and setter methods (`getName()`, `setName()`, `getAge()`, `setAge()`) to access and modify the data fields. This way, the internal state of the `Person` object is protected, and any changes to the data must go through the defined methods, allowing for validation or additional logic if needed.

The `Main` class demonstrates how we can create an instance of the `Person` class and use the getter and setter methods to interact with the object's data. The encapsulation ensures that the object's state remains controlled and consistent, and any modifications to the data can be performed through the defined methods.

Abstraction and encapsulation are fundamental principles in object-oriented programming that promote code organization, modularity, and maintainability. They help in managing complexity, hiding implementation details, and providing a clear and controlled interface for working with objects.

##### Next [[Access Control, In-built Packages, Object Class]]