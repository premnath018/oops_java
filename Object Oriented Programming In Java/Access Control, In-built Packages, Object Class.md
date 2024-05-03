##### Previous [[Principles of OOPs - Abstraction and Encapsulation]]
## Access Control:

Access control in Java determines how members (variables, methods, and nested classes) of a class can be accessed by other classes or code outside the class itself. Java provides four access modifiers to control access levels: public, private, protected, and default (no modifier).

1. **Public:** Public members are accessible from any class or package. They have the widest scope of accessibility.

2. **Private:** Private members are only accessible within the same class. They are not visible to any other class or package.

3. **Protected:** Protected members are accessible within the same class, subclasses (even if they are in different packages), and other classes in the same package.

4. **Default (No modifier):** Members with no explicit access modifier (also known as package-private) are accessible within the same class and other classes in the same package. They are not accessible outside the package.

Access Modifiers Table:

| Access Modifier | Same Class | Same Package | Subclass | Diff Package |
| --------------- | ---------- | ------------ | -------- | ------------ |
| Public          | Yes ✅      | Yes ✅        | Yes ✅    | Yes ✅        |
| Private         | Yes ✅      | No 🚫        | No 🚫    | No 🚫        |
| Protected       | Yes ✅      | Yes ✅        | Yes ✅    | No 🚫        |
| Default         | Yes ✅      | Yes ✅        | No 🚫    | No 🚫        |

Example 2: Student Class

```java
package school;

public class Student {
    private String name;
    protected int age;
    int grade; // default access modifier
    public int id;

    public Student(String name, int age, int grade, int id) {
        this.name = name;
        this.age = age;
        this.grade = grade;
        this.id = id;
    }

    public void displayDetails() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Grade: " + grade);
        System.out.println("ID: " + id);
    }
}

package school;

public class Main {
    public static void main(String[] args) {
        Student student = new Student("John", 15, 10, 12345);
        student.displayDetails();
        System.out.println("Age: " + student.age);
        System.out.println("Grade: " + student.grade);
        System.out.println("ID: " + student.id);
    }
}
```

In this example, the `Student` class has different access modifiers for its members. The `name` field is private,
which means it can only be accessed within the same class. The `age` field is protected, allowing it to be accessed
within the same class, subclasses, and other classes in the same package. The `grade` field has the default access modifier,
so it is accessible within the same package. The `id` field is public, making it accessible from anywhere.

In the `Main` class, we create an instance of the `Student` class and access its members. We can access the `age` field
because it is protected and the `Main` class is in the same package. We can access the `grade` field because it has
the default access modifier and the `Main` class is in the same package. We can access the `id` field because it is public
and accessible from anywhere. However, we cannot access the `name` field because it is private and accessible only within
the `Student` class.

## Packages in Java:

Packages in Java are used to organize classes and interfaces into groups or modules. They provide a way to create a namespace and avoid naming conflicts. Packages also control the visibility and accessibility of classes and interfaces.

**1. Naming and Structure:**
   - Packages are named using a hierarchical naming convention, similar to file system paths. The convention is to use lowercase letters and separate levels with periods (e.g., `com.example.package`).
   - The package declaration is the first line of code in a Java source file and specifies the package to which the file belongs.
   - Packages are stored in the file system as directories. The directory structure reflects the package hierarchy.

**2. Visibility and Access:**
   - By default, classes within a package can access other classes within the same package without explicit import statements.
   - Classes within a package can access public and default (package-private) members of other classes within the same package.
   - To access classes outside the package, import statements are required. Only public classes and interfaces are accessible from other packages.
   - The package-private access level is the default access level if no access modifier is specified. It allows classes within the same package to access the member.

Example:

```java
package com.example.package;

public class MyClass {
    public void publicMethod() {
        System.out.println("This is a public method.");
    }

    void defaultMethod() {
        System.out.println("This is a default method.");
    }

    private void privateMethod() {
        System.out.println("This is a private method.");
    }
}
```

In this example, we have a class named `MyClass` within the package `com.example.package`. The class contains three methods: `publicMethod()`, `defaultMethod()`, and `privateMethod()`.

The `publicMethod()` is accessible from anywhere because it is declared as public. It can be accessed by other classes, regardless of whether they are in the same package or a different package.

The `defaultMethod()` does not have an access modifier specified, making it package-private. It is accessible only within the same package. Other classes outside the package cannot access this method directly.

The `privateMethod()` is declared as private, making it accessible only within the same class. It cannot be accessed by any other class, even if they are in the same package.

To use the `MyClass` from another package, we need to import it:

```java
package com.example.anotherpackage;

import com.example.package.MyClass;

public class AnotherClass {
    public static void main(String[] args) {
        MyClass myObj = new MyClass();
        myObj.publicMethod();   // Accessible
        myObj.defaultMethod();  // Not accessible (different package)
        myObj.privateMethod();  // Not accessible (private)
    }
}
```

In the `AnotherClass` example, we import the `MyClass` from the `com.example.package` package. We can access the `publicMethod()` because it is public and accessible from anywhere. However, we cannot access the `defaultMethod()` because it is package-private (default) and `AnotherClass` is in a different package. Similarly, the `privateMethod()` is not accessible because it is private to the `MyClass` itself.

## Inbuilt Object Methods in Java

Java provides a set of predefined methods that are available to all objects. These methods are inherited from the `java.lang.Object` class, which is the root class for all Java classes. Here are some commonly used inbuilt object methods:

1. `toString()`: Returns a string representation of the object. By default, it returns the class name followed by the object's hash code.

2. `equals(Object obj)`: Compares the current object with the specified object for equality. By default, it compares the object references (memory addresses) and returns `true` if they refer to the same object.

3. `hashCode()`: Returns a hash code value for the object. The default implementation returns the memory address of the object.

4. `getClass()`: Returns the class object associated with the object. It allows you to obtain information about the object's runtime class.

5. `clone()`: Creates and returns a copy of the object. It performs a shallow copy by default, which means that the object's fields are copied, but the references to other objects are still shared.

6. `finalize()`: Called by the garbage collector before reclaiming the object's memory. It allows you to perform any necessary cleanup operations.

Example:

```java
public class MyClass {
    private int value;

    public MyClass(int value) {
        this.value = value;
    }

    @Override
    public String toString() {
        return "MyClass[value=" + value + "]";
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        }
        if (obj == null || getClass() != obj.getClass()) {
            return false;
        }
        MyClass myObj = (MyClass) obj;
        return value == myObj.value;
    }

    @Override
    public int hashCode() {
        return Objects.hash(value);
    }

    public static void main(String[] args) {
        MyClass obj1 = new MyClass(10);
        MyClass obj2 = new MyClass(10);

        System.out.println(obj1.toString());          // Output: MyClass[value=10]
        System.out.println(obj1.equals(obj2));        // Output: false
        System.out.println(obj1.hashCode());          // Output: 123456 (example value)
        System.out.println(obj1.getClass().getName()); // Output: MyClass
    }
}
```

In this example, the `MyClass` defines its own implementation of the `toString()`, `equals()`, `hashCode()`, and `getClass()` methods.

The `toString()` method is overridden to return a custom string representation of the object.

The `equals()` method compares the `value` field of two `MyClass` objects for equality.

The `hashCode()` method calculates the hash code based on the `value` field.

The `getClass().getName()` method retrieves the name of the class.

In the `main()` method, we create two `MyClass` objects and demonstrate the usage of these inbuilt object methods.