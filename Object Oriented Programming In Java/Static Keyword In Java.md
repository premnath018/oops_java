8##### Previous [[New, Wrapper Class and Garbage Collection]]
### Understanding Static:

In object-oriented programming, the keyword `static` is used to declare members (variables or methods) that belong to the class itself, rather than to any specific instance of the class. Here are some key points to understand about static members:

1. Access without object creation: Static members can be accessed before any objects of their class are created, and without reference to any object. This is useful for defining common properties or behaviors that are independent of individual instances.

2. Static methods and variables: Both methods and variables can be declared as static. The most common example of a static member is the `main()` method, which is the entry point of a Java program. It is declared as static because it needs to be called before any objects exist.

3. Scope and access: A static method can only access other static data (variables or methods). It cannot directly access non-static data (instance variables). To access non-static members in a static context, you need to explicitly specify the object reference.

Example:

```java
public class Human {
    String message = "Hello World"; // non-static instance variable

    public static void display(Human human) {
		System.out.println(human.message); // accessing non-static member using an object reference
    }

    public static void main(String[] args) {
        Human kunal = new Human();
        kunal.message = "Kunal's message"; // modifying the instance variable
        Human.display(kunal); // calling static method with an object reference
    }
}
```

4. Limitations of static methods: A static method can only call other static methods and cannot directly call a non-static method. It is because static methods belong to the class itself and do not have access to instance-specific data or behavior.

5. Direct access and "this" or "super": In a static method, you cannot refer to the keywords `this` or `super`. These keywords are used to refer to the current instance or the superclass instance, respectively. Since static methods are not tied to any specific instance, they cannot use these keywords.

6. Static initialization block: If you need to perform computations to initialize static variables, you can use a static initialization block. It is executed exactly once when the class is first loaded.

Example:

```java
class UseStatic {
    static int a = 3;
    static int b;

    static {
        System.out.println("Static block initialized.");
        b = a * 4;
    }

    static void meth(int x) {
        System.out.println("x = " + x);
        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }

    public static void main(String args[]) {
        meth(42);
    }
}
```

Output:
```
Static block initialized.
x = 42
a = 3
b = 12
```

Note: The `main` method is static because it needs to be accessible for the application to run before any object instantiation takes place.

Additional Points:

- Only nested classes can be declared as static.
- Static inner classes can have static variables.
- In Java, you cannot override static methods inherited from a superclass because method overriding is resolved at runtime based on the object's type. Static methods, being class-level methods, are resolved during compile-time.
- Static interface methods are not inherited by implementing classes or sub-interfaces.

Example of a static nested class:

```java
public class Static {
    static class Test {
        String name;

        public Test(String name) {
            this.name = name;
        }
    }

    public static void main(String[] args) {
        Test a = new Test("Kunal");
        Test b = new Test("Rahul");

        System.out.println(a.name); // Kunal
        System.out.println(b.name); // Rahul
    }
}
```

Note: The static keyword in this example modifies the declaration of the nested class `Test` to indicate that it is not an inner class and does not have a current instance of the outer class `Static`. However, instances of `Test` can still be created in the `main` method and accessed by each other.

By understanding the concept of static members and their usage, you can effectively utilize them to define class-level behavior and data in your programs.

##### Next [[More About Static, Inner Classes and Singleton Class]]