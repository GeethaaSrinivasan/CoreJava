# Core-Java-100.md
# Part 2 (Q26–Q50)
# Advanced Core Java + Collections Framework

---

# Q26. What is an Immutable Class?

## Detailed Answer
An immutable class is a class whose state cannot be changed after object creation. To make a class immutable, declare it as final, make fields private and final, initialize fields through constructors, and avoid setter methods. Immutable objects are inherently thread-safe.

## Real-world Use Case
String, LocalDate, and BigDecimal are immutable classes extensively used in enterprise applications.

## Code Example

```java
final class Employee {
    private final String name;

    public Employee(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

---

# Q27. What are Wrapper Classes?

## Detailed Answer
Wrapper classes convert primitive types into objects. Java provides Integer, Double, Boolean, Character, etc. They are required when working with Collections because collections store objects, not primitives.

## Real-world Use Case
Storing employee IDs inside an ArrayList<Integer>.

## Code Example

```java
Integer empId = Integer.valueOf(101);
Double salary = Double.valueOf(50000.50);
```

---

# Q28. What is Autoboxing and Unboxing?

## Detailed Answer
Autoboxing automatically converts primitives into wrapper objects, while unboxing converts wrapper objects back into primitives. Java introduced this feature to simplify coding.

## Real-world Use Case
Frequently used while storing numeric values in collections.

## Code Example

```java
Integer number = 100; // Autoboxing
int value = number;   // Unboxing
```

---

# Q29. What is Object Class?

## Detailed Answer
Object is the root class of all Java classes. Every class implicitly extends Object and inherits methods such as equals(), hashCode(), toString(), clone(), and getClass().

## Real-world Use Case
Frameworks rely heavily on Object methods for logging and comparison.

## Code Example

```java
Object obj = new String("Java");

System.out.println(obj.getClass());
```

---

# Q30. Why should hashCode() and equals() be overridden together?

## Detailed Answer
If two objects are equal according to equals(), they must return the same hashCode(). Collections such as HashMap and HashSet depend on both methods for proper storage and retrieval.

## Real-world Use Case
Employee objects used as HashMap keys.

## Code Example

```java
@Override
public boolean equals(Object o) {
    return this.id == ((Employee)o).id;
}

@Override
public int hashCode() {
    return id;
}
```

---

# Q31. What is a Collection Framework?

## Detailed Answer
Java Collection Framework provides classes and interfaces for storing and manipulating groups of objects. It includes List, Set, Queue, Map, and utility classes for sorting and searching.

## Real-world Use Case
Managing customer records, orders, products, and user sessions.

## Code Example

```java
List<String> names = new ArrayList<>();
names.add("John");
```

---

# Q32. Difference between Collection and Collections?

## Detailed Answer
Collection is an interface representing a group of objects. Collections is a utility class containing static methods for sorting, searching, synchronization, and other operations.

## Real-world Use Case
Using Collections.sort() to sort employee lists.

## Code Example

```java
Collections.sort(names);
```

---

# Q33. Difference between List and Set?

## Detailed Answer
List allows duplicate elements and preserves insertion order. Set does not allow duplicates and may or may not preserve order depending on implementation.

## Real-world Use Case
Customer orders use List; unique email addresses use Set.

## Code Example

```java
List<String> list = new ArrayList<>();
Set<String> set = new HashSet<>();
```

---

# Q34. Difference between Array and ArrayList?

## Detailed Answer
Arrays have fixed sizes, whereas ArrayLists are dynamic and can grow automatically. Arrays can store primitives, while ArrayList stores only objects.

## Real-world Use Case
ArrayList is preferred when record counts are unknown.

## Code Example

```java
ArrayList<String> cities = new ArrayList<>();
cities.add("Chennai");
```

---

# Q35. What is ArrayList?

## Detailed Answer
ArrayList is a dynamic array implementation of List. It provides fast random access, maintains insertion order, and allows duplicates.

## Real-world Use Case
Displaying products on an e-commerce page.

## Code Example

```java
ArrayList<String> products = new ArrayList<>();

products.add("Laptop");
products.add("Mobile");
```

---

# Q36. Difference between ArrayList and LinkedList?

## Detailed Answer
ArrayList provides better random access because it uses arrays internally. LinkedList uses doubly linked nodes and performs better for insertions and deletions.

## Real-world Use Case
ArrayList for reporting systems, LinkedList for queue-like processing.

## Code Example

```java
List<Integer> arrayList = new ArrayList<>();
List<Integer> linkedList = new LinkedList<>();
```

---

# Q37. What is Vector?

## Detailed Answer
Vector is a legacy collection class similar to ArrayList but thread-safe because its methods are synchronized.

## Real-world Use Case
Used in older enterprise applications developed before Java Collections Framework matured.

## Code Example

```java
Vector<String> vector = new Vector<>();
vector.add("Java");
```

---

# Q38. Difference between ArrayList and Vector?

## Detailed Answer
ArrayList is not synchronized and performs better. Vector is synchronized and therefore slower. ArrayList is preferred in modern applications.

## Real-world Use Case
Web applications typically use ArrayList due to better performance.

## Code Example

```java
ArrayList<Integer> list = new ArrayList<>();
Vector<Integer> vector = new Vector<>();
```

---

# Q39. What is Stack Collection?

## Detailed Answer
Stack follows Last In First Out (LIFO) order. The most recently added element is removed first.

## Real-world Use Case
Undo operations in editors.

## Code Example

```java
Stack<Integer> stack = new Stack<>();

stack.push(10);
stack.push(20);

System.out.println(stack.pop());
```

---

# Q40. What is Queue?

## Detailed Answer
Queue follows First In First Out (FIFO) order. Elements are processed in the same order they are inserted.

## Real-world Use Case
Order processing systems and task scheduling.

## Code Example

```java
Queue<String> queue = new LinkedList<>();

queue.add("Order1");
queue.add("Order2");
```

---

# Q41. Difference between HashSet and TreeSet?

## Detailed Answer
HashSet stores unique elements without maintaining order. TreeSet stores elements in sorted order using natural sorting or comparators.

## Real-world Use Case
HashSet for unique IDs, TreeSet for sorted rankings.

## Code Example

```java
Set<Integer> hs = new HashSet<>();
Set<Integer> ts = new TreeSet<>();
```

---

# Q42. What is LinkedHashSet?

## Detailed Answer
LinkedHashSet maintains insertion order while preventing duplicates. Internally it combines HashSet and LinkedList features.

## Real-world Use Case
Displaying recently visited pages in original sequence.

## Code Example

```java
LinkedHashSet<String> set =
        new LinkedHashSet<>();
```

---

# Q43. What is HashMap?

## Detailed Answer
HashMap stores data as key-value pairs. It allows one null key and multiple null values and provides average O(1) lookup performance.

## Real-world Use Case
Customer ID mapped to Customer object.

## Code Example

```java
Map<Integer,String> employees =
        new HashMap<>();

employees.put(1, "John");
```

---

# Q44. How does HashMap work internally?

## Detailed Answer
HashMap uses hashCode() to determine bucket location. equals() is used when collisions occur. Java 8 converts large linked lists into balanced trees to improve performance.

## Real-world Use Case
Caching applications and product lookup systems.

## Code Example

```java
map.put(101, "Java");
map.get(101);
```

---

# Q45. What is Hash Collision?

## Detailed Answer
Hash collision occurs when different keys produce the same hash value. HashMap handles collisions using linked lists and balanced trees.

## Real-world Use Case
Millions of customer records stored in HashMaps.

## Code Example

```java
hashCode("ABC") == hashCode("XYZ");
```

---

# Q46. Difference between HashMap and Hashtable?

## Detailed Answer
HashMap is not synchronized and allows null values. Hashtable is synchronized, thread-safe, and does not allow null keys or values.

## Real-world Use Case
HashMap is commonly used in Spring Boot applications.

## Code Example

```java
HashMap<Integer,String> hm =
        new HashMap<>();

Hashtable<Integer,String> ht =
        new Hashtable<>();
```

---

# Q47. Difference between HashMap and ConcurrentHashMap?

## Detailed Answer
ConcurrentHashMap supports concurrent updates without locking the entire map. It achieves better scalability than synchronized HashMap.

## Real-world Use Case
High-traffic microservices storing cached user sessions.

## Code Example

```java
ConcurrentHashMap<Integer,String> map =
        new ConcurrentHashMap<>();
```

---

# Q48. What is Comparable Interface?

## Detailed Answer
Comparable provides natural ordering for objects. The compareTo() method defines sorting logic within the class itself.

## Real-world Use Case
Sorting employees by ID.

## Code Example

```java
class Employee
implements Comparable<Employee>{

    public int compareTo(Employee e){
        return this.id - e.id;
    }
}
```

---

# Q49. What is Comparator Interface?

## Detailed Answer
Comparator provides custom sorting logic outside the class. Multiple sorting criteria can be implemented without modifying the original class.

## Real-world Use Case
Sort employees by name, salary, or experience.

## Code Example

```java
Comparator<Employee> byName =
    (e1,e2) ->
      e1.getName()
      .compareTo(e2.getName());
```

---

# Q50. Difference between Comparable and Comparator?

## Detailed Answer
Comparable supports one natural sorting order and is implemented inside the class. Comparator supports multiple sorting strategies and is implemented externally.

## Real-world Use Case
Employee objects sorted differently for HR, Payroll, and Reporting systems.

## Code Example

```java
Collections.sort(empList);

empList.sort(
  Comparator.comparing(
     Employee::getName
  )
);
```

---

✅ Part 2 Completed (Q26–Q50)

Topics Covered:
- Immutable Classes
- Wrapper Classes
- Autoboxing & Unboxing
- Object Class
- equals() & hashCode()
- Collections Framework
- ArrayList
- LinkedList
- Vector
- Stack
- Queue
- Set Implementations
- HashMap Internals
- ConcurrentHashMap
- Comparable
- Comparator
- Collection Interview Questions