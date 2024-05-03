##### Previous [[Principles of OOPs - Inheritance]]
## Introduction:

Polymorphism is a fundamental concept in object-oriented programming that allows objects of different classes to be treated as objects of a common superclass. In Java, method overloading is one aspect of polymorphism. It enables the definition of multiple methods with the same name but different parameter declarations within the same class.

## Two Types of Polymorphism 

 **Compile-time Polymorphism:** Compile-time polymorphism, also known as static polymorphism, is achieved through method overloading. It allows multiple methods with the same name but different parameters to be defined in a class. The appropriate method is determined based on the arguments used in the method call during compile-time.

**Runtime Polymorphism:** Runtime polymorphism, also known as dynamic polymorphism, is achieved through method overriding. It allows a subclass to provide a different implementation of a method defined in its superclass. The appropriate method is determined based on the actual object type at runtime.

## Method Overloading ( Compile-time Polymorphism ) :

Method overloading is a feature in Java that allows multiple methods within the same class to share the same name but have different parameter declarations. The parameter declarations must differ in terms of the number of parameters, their types, or both. The return type alone is insufficient to distinguish between different method versions.

When a method is called, Java determines which version of the method to execute based on the arguments used in the method call. It matches the arguments to the most appropriate method by considering the parameter types. If an exact match is found, that method is called. If an exact match is not found, Java applies automatic type conversions if possible. If no suitable method is found, a compilation error occurs.

Method overloading provides flexibility and convenience, allowing methods with different parameter types to share the same name. It improves code readability and reduces the need for multiple method names. It is important to carefully design overloaded methods to ensure their parameter declarations differ enough to avoid ambiguity.

Here's an example illustrating method overloading:

```java
class OverloadDemo {
    void test(double a) {
        System.out.println("Inside test(double) a: " + a);
    }
    void test(int a) {
        System.out.println("Inside test(int) a: " + a);
    }
}

class Overload {
    public static void main(String args[]) {
        OverloadDemo ob = new OverloadDemo();
        int i = 88;
        double d = 123.2;
        ob.test(i);        // Invokes test(int)
        ob.test(d);        // Invokes test(double)
    }
}
```

In this example, the `OverloadDemo` class defines two overloaded `test` methods, one that takes a `double` parameter and another that takes an `int` parameter. When the `test` method is called with an `int` argument, the version of the method with the `int` parameter is invoked. Similarly, when the `test` method is called with a `double` argument, the version of the method with the `double` parameter is invoked.

Returning Objects:

In Java, methods can also return objects. When a method returns an object, a new object is created within the method, and a reference to it is returned to the calling routine. The object continues to exist as long as there is a reference to it somewhere in the program. When there are no references to it, the object will be reclaimed during garbage collection.

Here's an example that demonstrates returning objects:

```java
class Test {
    int a;
    Test(int i) {
        a = i;
    }
    Test incrByTen() {
        Test temp = new Test(a + 10);
        return temp;
    }
}

class RetOb {
    public static void main(String args[]) {
        Test ob1 = new Test(2);
        Test ob2;
        ob2 = ob1.incrByTen();
        System.out.println("ob1.a: " + ob1.a);
        System.out.println("ob2.a: " + ob2.a);
    }
}
```

Output:
```
ob1.a: 2
ob2.a: 12
```

In this example, the `Test` class has a method called `incrByTen` which creates a new object with the current value of `a` incremented by ten. The method then returns a reference to this new object. In the `RetOb` class, an instance of `Test` is created, and the `incrByTen` method is called on it. The returned object is assigned to `ob2`, and its value is printed along with the original object `ob1`. As you can see, each time `incrByTen` is invoked, a new object is created and returned, allowing for the chaining of operations.

These examples demonstrate the concept of method overloading and returning objects in Java, showcasing the flexibility and power they provide in designing and implementing object-oriented programs.

## Method Overriding

In a class hierarchy, when a method in a subclass has the same name and type signature as a method in its superclass, the method in the subclass is said to override the method in the superclass. This allows the subclass to provide a different implementation of the method. When an overridden method is called from within its subclass, it will always refer to the version of that method defined by the subclass, and the version defined by the superclass will be hidden.

Method overriding occurs when the names and type signatures of the two methods are identical. If they are not, then the two methods are simply overloaded, and the subclass method does not override the superclass method.

Example 1:
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes a sound.");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks.");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        animal.makeSound(); // Output: "Animal makes a sound."

        Dog dog = new Dog();
        dog.makeSound(); // Output: "Dog barks."

        Animal animal2 = new Dog();
        animal2.makeSound(); // Output: "Dog barks."
    }
}
```

In this example, we have a superclass `Animal` with a method `makeSound()`. The subclass `Dog` overrides the `makeSound()` method and provides its own implementation. When we create an instance of `Animal` and call `makeSound()`, it executes the method defined in the `Animal` class. However, when we create an instance of `Dog` and call `makeSound()`, it executes the overridden method in the `Dog` class. Additionally, when we have a superclass reference (`Animal`) pointing to a subclass object (`Dog`), calling `makeSound()` still executes the overridden method in the subclass.

Dynamic Method Dispatch:

Dynamic method dispatch is the mechanism by which a call to an overridden method is resolved at runtime, rather than compile time. It is an essential feature for implementing runtime polymorphism in Java. When an overridden method is called through a superclass reference, Java determines which version of the method to execute based on the type of the object being referred to at the time of the call. This determination is made dynamically at runtime.

Example 2:
```java
class Shape {
    void draw() {
        System.out.println("Drawing a shape.");
    }
}

class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a circle.");
    }
}

class Square extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing a square.");
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape1 = new Circle();
        shape1.draw(); // Output: "Drawing a circle."

        Shape shape2 = new Square();
        shape2.draw(); // Output: "Drawing a square."
    }
}
```

In this example, we have a superclass `Shape` with a method `draw()`. The subclasses `Circle` and `Square` override the `draw()` method with their respective implementations. When we create an instance of `Circle` and assign it to a `Shape` reference, calling `draw()` on that reference will execute the overridden method in the `Circle` class, resulting in the output "Drawing a circle." Similarly, when we create an instance of `Square` and assign it to a `Shape` reference, calling `draw()` will execute the overridden method in the `Square` class, resulting in the output "Drawing a square."

Dynamic method dispatch allows for flexibility in selecting the appropriate overridden method based on the actual object type, enabling polymorphic behavior in Java programs.

##### Next [[Principles of OOPs - Abstraction and Encapsulation]]
