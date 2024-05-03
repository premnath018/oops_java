##### Previous [[This, Final, Finalize Method and Constructors]]
## New , Wrapper Class and Garbage Collection 

 Let's delve into the concepts of `new` keyword, wrapper classes, and garbage collection in Java with a more detailed explanation.

### The `new` Keyword:

The `new` keyword in Java is used to instantiate objects of a class. When `new` is used to create an object, memory is allocated on the heap, and the constructor of the class is invoked to initialize the newly created object.

#### Memory Allocation and Object Creation:

When you use `new` to create an object, the following steps occur:
- Memory allocation: Memory is allocated on the heap to store the object's instance variables.
- Constructor invocation: The constructor of the class is called to initialize the newly created object.

Example:
```java
// Creating an instance of the Person class using 'new'
Person person = new Person("John");
```

In the above example, `new Person("John")` creates a new `Person` object and initializes it with the name `"John"`.

### Wrapper Classes:

Wrapper classes in Java are used to represent primitive data types as objects. Each primitive data type (`int`, `char`, `boolean`, etc.) has a corresponding wrapper class (`Integer`, `Character`, `Boolean`, etc.) that provides useful methods and functionalities.

#### Purpose of Wrapper Classes:

- **Conversion**: Wrapper classes facilitate conversion between primitive data types and objects.
- **Utilization of Collections**: Many Java collections (like `ArrayList` or `HashMap`) can only store objects, not primitives. Wrapper classes allow primitives to be used within these collections.
- **Nullability**: Wrapper classes can hold `null` values, which primitives cannot.

Example:
```java
// Using Integer wrapper class to store an integer value
Integer num = new Integer(10);

// Converting int to Integer using autoboxing
int value = 5;
Integer intValue = value; // Autoboxing
```

In the above example, `Integer` is a wrapper class for the primitive `int`, allowing `int` to be used as an object.

### Garbage Collection:

Garbage collection in Java is an automatic process where the JVM (Java Virtual Machine) reclaims memory occupied by objects that are no longer referenced or reachable by the application.

#### How Garbage Collection Works:

- **Identifying Unreachable Objects**: The JVM's garbage collector identifies objects that are no longer reachable by tracing references from the root objects (like `main()` method).
- **Reclaiming Memory**: Once an object is identified as unreachable, the memory occupied by that object is reclaimed, and its resources are freed up for reuse.

#### Benefits of Garbage Collection:

- **Automatic Memory Management**: Developers don't need to manually deallocate memory, reducing the risk of memory leaks.
- **Enhanced Developer Productivity**: Focus can be on application logic rather than memory management.

 Let's incorporate an example of garbage collection in Java to demonstrate how it works.

### Garbage Collection Example:

Garbage collection in Java automatically reclaims memory occupied by objects that are no longer reachable by the application. Let's consider a scenario where objects become eligible for garbage collection.

```java
class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public void finalize() {
        System.out.println("Cleaning up person: " + name);
    }
}

public class GarbageCollectionExample {
    public static void main(String[] args) {
        Person person1 = new Person("Alice");
        Person person2 = new Person("Bob");

        // Making person1 eligible for garbage collection
        person1 = null;

        // At this point, person1 is no longer referenced
        // Triggering garbage collection explicitly (for demonstration purposes)
        System.gc();

        // Creating more objects
        Person person3 = new Person("Charlie");
        Person person4 = new Person("David");

        // Making person3 and person4 eligible for garbage collection
        person3 = null;
        person4 = null;

        // Triggering garbage collection again (for demonstration purposes)
        System.gc();
    }
}

Output :
Cleaning up person: Alice
Cleaning up person: David
Cleaning up person: Charlie

```

In the above example:
- We define a `Person` class with a constructor that initializes the `name` instance variable.
- The `finalize()` method is overridden in `Person` class to print a message when the object is being garbage collected.
- In the `main()` method:
  - We create `Person` objects (`person1`, `person2`, `person3`, `person4`).
  - We set `person1` to `null`, making it eligible for garbage collection.
  - We explicitly call `System.gc()` to suggest garbage collection to the JVM (Note: It's a hint, and the JVM may choose to ignore it).
  - Later, `person3` and `person4` are also set to `null` to make them eligible for garbage collection.
  - We again call `System.gc()` to suggest garbage collection.

When garbage collection is triggered (either explicitly or automatically by the JVM), objects that are no longer referenced (`person1`, `person3`, `person4`) are finalized (if necessary) and reclaimed, freeing up memory resources.

The output of this program may vary depending on JVM implementation and when garbage collection actually occurs. However, the `finalize()` method in the `Person` class will be called when the respective objects are garbage collected, demonstrating the cleanup process. Note that relying on `finalize()` for critical cleanup is discouraged; this example is for illustrative purposes only.

##### Next [[Static Keyword In Java]]