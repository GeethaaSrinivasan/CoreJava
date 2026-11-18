# Core-Java-100.md
# Part 1 (Q1-Q25)
# Java Full Stack Interview Questions for 3-8 Years Experience

---

# Q1. What is JVM, JRE, and JDK?

## Detailed Answer
JVM (Java Virtual Machine) is responsible for executing Java bytecode and providing platform independence. JRE (Java Runtime Environment) contains JVM and required libraries to run Java applications. JDK (Java Development Kit) includes JRE along with development tools such as javac, javadoc, and debugger required to develop Java applications.

## Real-world Use Case
A developer compiles code using JDK, while clients only need JRE to execute the application.

## Code Example

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello Java");
    }
}
```

---

# Q2. Why is Java platform independent?

## Detailed Answer
Java source code is compiled into bytecode (.class files). This bytecode can run on any system having a compatible JVM. The JVM interprets bytecode into machine-specific instructions, making Java a "Write Once, Run Anywhere" language.

## Real-world Use Case
The same banking application can run on Windows, Linux, and macOS without code changes.

## Code Example

```java
javac Main.java
java Main
```

---

# Q3. Difference between == and equals()?

## Detailed Answer
The == operator compares references or memory addresses of objects. The equals() method compares object content. String and wrapper classes override equals() to compare actual values instead of memory locations.

## Real-world Use Case
Used extensively while comparing usernames, emails, and business identifiers.

## Code Example

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

---

# Q4. Why is String immutable?

## Detailed Answer
String is immutable because its value cannot be modified after creation. This improves security, thread safety, hashcode caching, and String pool optimization. Any modification creates a new object.

## Real-world Use Case
Database URLs and security tokens remain unchanged throughout execution.

## Code Example

```java
String name = "Java";
name.concat("17");

System.out.println(name);
```

---

# Q5. What is String Pool?

## Detailed Answer
String Pool is a special memory area inside heap where string literals are stored. If a String already exists in the pool, JVM reuses it instead of creating a new object, saving memory.

## Real-world Use Case
Frequently used values such as status codes and country codes reuse pooled strings.

## Code Example

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

---

# Q6. Difference between String, StringBuilder, and StringBuffer?

## Detailed Answer
String is immutable. StringBuilder is mutable and not thread-safe, making it faster. StringBuffer is mutable and thread-safe because its methods are synchronized.

## Real-world Use Case
StringBuilder is preferred while generating reports containing thousands of concatenations.

## Code Example

```java
StringBuilder sb = new StringBuilder();
sb.append("Java");
sb.append(" Full Stack");

System.out.println(sb);
```

---

# Q7. What is Constructor?

## Detailed Answer
A constructor is a special method that initializes an object. It has the same name as the class and does not have a return type. Constructors are executed automatically when objects are created.

## Real-world Use Case
Initializing employee information while creating Employee objects.

## Code Example

```java
class Employee {
    Employee() {
        System.out.println("Created");
    }
}
```

---

# Q8. What is Constructor Overloading?

## Detailed Answer
Constructor overloading means defining multiple constructors with different parameter lists. It provides multiple ways to initialize objects.

## Real-world Use Case
Different constructors can initialize employee data with varying details.

## Code Example

```java
class Employee {
    Employee() {}

    Employee(String name) {}

    Employee(String name, int age) {}
}
```

---

# Q9. What is Method Overloading?

## Detailed Answer
Method overloading allows multiple methods with the same name but different parameter lists. It is achieved at compile time.

## Real-world Use Case
A calculator application can have multiple add() methods.

## Code Example

```java
class Calculator {
    int add(int a, int b){
        return a+b;
    }

    double add(double a,double b){
        return a+b;
    }
}
```

---

# Q10. What is Method Overriding?

## Detailed Answer
Method overriding occurs when a subclass provides its own implementation of a parent class method. Runtime polymorphism is achieved through overriding.

## Real-world Use Case
Different payment types implement payment processing differently.

## Code Example

```java
class Animal{
    void sound(){
        System.out.println("Animal");
    }
}

class Dog extends Animal{
    void sound(){
        System.out.println("Bark");
    }
}
```

---

# Q11. What is Encapsulation?

## Detailed Answer
Encapsulation binds data and methods together while restricting direct access using private variables. Access is provided through getters and setters.

## Real-world Use Case
Bank account balances should not be modified directly.

## Code Example

```java
class Account{
    private double balance;

    public double getBalance(){
        return balance;
    }
}
```

---

# Q12. What is Inheritance?

## Detailed Answer
Inheritance allows one class to acquire properties and methods of another class. It promotes code reuse and supports hierarchical relationships.

## Real-world Use Case
Manager inherits common employee attributes.

## Code Example

```java
class Employee {}

class Manager extends Employee {}
```

---

# Q13. What is Polymorphism?

## Detailed Answer
Polymorphism means one interface with multiple implementations. It allows methods to behave differently depending on the object calling them.

## Real-world Use Case
Multiple payment methods implement a single payment interface.

## Code Example

```java
Animal animal = new Dog();
animal.sound();
```

---

# Q14. What is Abstraction?

## Detailed Answer
Abstraction hides implementation details and shows only essential features. It can be achieved using abstract classes and interfaces.

## Real-world Use Case
Users interact with ATM operations without knowing backend processing.

## Code Example

```java
abstract class Vehicle{
    abstract void start();
}
```

---

# Q15. Difference between Abstract Class and Interface?

## Detailed Answer
Abstract classes can have both abstract and concrete methods. Interfaces define contracts and support multiple inheritance. Java 8 introduced default and static methods in interfaces.

## Real-world Use Case
Payment interface implemented by multiple providers.

## Code Example

```java
interface Payment{
    void pay();
}
```

---

# Q16. What is Marker Interface?

## Detailed Answer
A marker interface contains no methods or fields. It provides metadata information to JVM or frameworks.

## Real-world Use Case
Serializable indicates an object can be converted into bytes.

## Code Example

```java
class Employee implements Serializable {
}
```

---

# Q17. What is Serialization?

## Detailed Answer
Serialization converts an object into byte stream form for storage or transmission. Deserialization reconstructs the object back.

## Real-world Use Case
Sending session objects across distributed systems.

## Code Example

```java
class Employee implements Serializable {
    private int id;
}
```

---

# Q18. What is transient keyword?

## Detailed Answer
transient prevents a variable from being serialized. During serialization, JVM ignores transient fields.

## Real-world Use Case
Passwords should not be stored in serialized objects.

## Code Example

```java
class User implements Serializable{
    transient String password;
}
```

---

# Q19. What is final keyword?

## Detailed Answer
The final keyword restricts modification. Final variables cannot be reassigned, final methods cannot be overridden, and final classes cannot be inherited.

## Real-world Use Case
String class is final to maintain immutability.

## Code Example

```java
final class Utility {
}
```

---

# Q20. Difference between Heap and Stack Memory?

## Detailed Answer
Stack memory stores local variables and method calls. Heap memory stores objects and instance variables. Stack memory is faster while heap supports dynamic allocation.

## Real-world Use Case
Employee objects reside in heap, while references exist in stack.

## Code Example

```java
Employee employee = new Employee();
```

---

# Q21. What is Garbage Collection?

## Detailed Answer
Garbage Collection automatically removes unused objects from heap memory. JVM identifies unreachable objects and frees memory.

## Real-world Use Case
Prevents memory leaks in long-running enterprise applications.

## Code Example

```java
Employee emp = new Employee();
emp = null;
```

---

# Q22. What is finalize() method?

## Detailed Answer
finalize() was invoked before garbage collection of an object. It is deprecated because its behavior is unpredictable and impacts performance.

## Real-world Use Case
Modern projects use try-with-resources instead.

## Code Example

```java
@Override
protected void finalize() throws Throwable {
    System.out.println("Cleanup");
}
```

---

# Q23. What is Exception Handling?

## Detailed Answer
Exception handling enables applications to manage runtime errors gracefully. Java provides try, catch, finally, throw, and throws keywords.

## Real-world Use Case
Handling database connection failures without crashing the application.

## Code Example

```java
try{
    int result = 10/0;
}
catch(Exception e){
    System.out.println(e.getMessage());
}
```

---

# Q24. Difference between Checked and Unchecked Exceptions?

## Detailed Answer
Checked exceptions are verified during compilation and must be handled explicitly. Unchecked exceptions occur at runtime and extend RuntimeException.

## Real-world Use Case
IOException is checked, NullPointerException is unchecked.

## Code Example

```java
FileReader file =
    new FileReader("test.txt");
```

---

# Q25. Difference between throw and throws?

## Detailed Answer
throw is used to explicitly throw an exception. throws is used in method signatures to declare possible exceptions that may occur.

## Real-world Use Case
Service methods often declare checked exceptions using throws.

## Code Example

```java
public void validate(int age)
        throws Exception {

    if(age < 18){
        throw new Exception("Invalid age");
    }
}
```

---

✅ Part 1 Completed (Q1-Q25)

Topics Covered:
- JVM/JDK/JRE
- OOPs Concepts
- String Handling
- Constructors
- Inheritance
- Polymorphism
- Abstraction
- Interfaces
- Serialization
- Memory Management
- Garbage Collection
- Exception Handling

Next Part (Q26-Q50):
- Advanced Core Java
- Wrapper Classes
- Immutable Objects
- Comparable vs Comparator
- Generics
- Reflection API
- Java 8 Features
- Collections Framework (beginning)
```**