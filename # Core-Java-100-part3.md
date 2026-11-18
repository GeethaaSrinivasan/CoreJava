# Core-Java-100.md
# Part 3 (Q51–Q75)
# Generics + Java 8 Features + Stream API

---

# Q51. What are Generics in Java?

## Detailed Answer
Generics allow classes, interfaces, and methods to operate on different data types while providing compile-time type safety. They eliminate the need for explicit type casting and reduce runtime errors. Generics improve code reusability and readability.

## Real-world Use Case
A common repository class can manage Employee, Product, and Customer entities.

## Code Example

```java
List<String> names = new ArrayList<>();
names.add("Java");

// names.add(100); // Compilation Error
```

---

# Q52. What are the advantages of Generics?

## Detailed Answer
Generics provide type safety, eliminate ClassCastException, improve code readability, and increase code reuse. Errors are detected during compilation rather than at runtime.

## Real-world Use Case
Enterprise applications use generic service and repository layers.

## Code Example

```java
List<Integer> ids = new ArrayList<>();

ids.add(101);

Integer id = ids.get(0);
```

---

# Q53. What is a Generic Class?

## Detailed Answer
A Generic Class allows the data type to be defined at object creation time. The type parameter acts as a placeholder for actual data types.

## Real-world Use Case
Custom container implementations used across projects.

## Code Example

```java
class Box<T> {
    private T value;

    public void set(T value){
        this.value = value;
    }

    public T get(){
        return value;
    }
}
```

---

# Q54. What is a Generic Method?

## Detailed Answer
A Generic Method allows type parameters to be declared at the method level instead of the class level. It can operate on different data types.

## Real-world Use Case
Utility libraries often contain generic helper methods.

## Code Example

```java
public static <T> void print(T value){
    System.out.println(value);
}
```

---

# Q55. What is Type Erasure?

## Detailed Answer
Java implements generics using Type Erasure. During compilation, generic type information is removed and replaced with Object or bounded types. Generics exist only at compile time.

## Real-world Use Case
Explains why runtime cannot identify generic parameter types directly.

## Code Example

```java
List<String> list = new ArrayList<>();
```

Compiled as:

```java
List list = new ArrayList();
```

---

# Q56. What is a Functional Interface?

## Detailed Answer
A Functional Interface contains exactly one abstract method. It can contain default and static methods. Functional interfaces are heavily used in Lambda Expressions.

## Real-world Use Case
Runnable, Comparator, Supplier, and Predicate are functional interfaces.

## Code Example

```java
@FunctionalInterface
interface Calculator{
    int add(int a,int b);
}
```

---

# Q57. What is Lambda Expression?

## Detailed Answer
Lambda Expressions provide a concise way to implement functional interfaces. They reduce boilerplate code by eliminating anonymous class syntax.

## Real-world Use Case
Used extensively in Stream API processing.

## Code Example

```java
Calculator c =
    (a,b) -> a+b;

System.out.println(c.add(10,20));
```

---

# Q58. Difference between Lambda and Anonymous Class?

## Detailed Answer
Lambda expressions are lightweight and concise. Anonymous classes create separate class instances and require more code. Lambdas focus on behavior rather than object creation.

## Real-world Use Case
Event handling and collection processing.

## Code Example

```java
Runnable r =
    () -> System.out.println("Running");
```

---

# Q59. What is Method Reference?

## Detailed Answer
Method references provide a cleaner way to call methods using the :: operator. They improve readability compared to equivalent lambda expressions.

## Real-world Use Case
Frequently used in Stream API pipelines.

## Code Example

```java
List<String> names =
    List.of("Java","Spring");

names.forEach(System.out::println);
```

---

# Q60. What is Optional Class?

## Detailed Answer
Optional is a container object that may or may not contain a value. It helps avoid NullPointerException and encourages safer null handling.

## Real-world Use Case
Returning optional customer details from repositories.

## Code Example

```java
Optional<String> name =
        Optional.of("Java");

System.out.println(name.orElse("Unknown"));
```

---

# Q61. What is Stream API?

## Detailed Answer
Stream API provides a functional programming approach for processing collections. It supports filtering, mapping, sorting, grouping, and aggregation operations.

## Real-world Use Case
Processing large employee datasets efficiently.

## Code Example

```java
List<Integer> numbers =
    List.of(1,2,3,4);

numbers.stream()
       .forEach(System.out::println);
```

---

# Q62. Difference between Collection and Stream?

## Detailed Answer
Collections store data, whereas Streams process data. Streams do not modify original data and support functional-style operations.

## Real-world Use Case
Collection stores all customer records while Streams process them.

## Code Example

```java
employees.stream()
         .filter(e -> e.getSalary() > 50000);
```

---

# Q63. What is filter() in Stream API?

## Detailed Answer
filter() is an intermediate operation used to select elements matching a given condition. It returns a filtered stream.

## Real-world Use Case
Finding employees whose salaries exceed a threshold.

## Code Example

```java
numbers.stream()
       .filter(n -> n > 5)
       .forEach(System.out::println);
```

---

# Q64. What is map() in Stream API?

## Detailed Answer
map() transforms each element into another form. It is commonly used to convert entities into DTOs or extract specific fields.

## Real-world Use Case
Extracting customer names from customer objects.

## Code Example

```java
employees.stream()
         .map(Employee::getName)
         .forEach(System.out::println);
```

---

# Q65. Difference between map() and flatMap()?

## Detailed Answer
map() creates one output element per input element. flatMap() flattens nested structures into a single stream.

## Real-world Use Case
Processing nested order item collections.

## Code Example

```java
list.stream()
    .flatMap(Collection::stream)
    .forEach(System.out::println);
```

---

# Q66. What is sorted() in Stream API?

## Detailed Answer
sorted() sorts stream elements using natural ordering or custom comparators. It returns a new sorted stream.

## Real-world Use Case
Sorting employees by salary or experience.

## Code Example

```java
numbers.stream()
       .sorted()
       .forEach(System.out::println);
```

---

# Q67. What is distinct() in Stream API?

## Detailed Answer
distinct() removes duplicate elements from a stream. It relies on equals() and hashCode() methods.

## Real-world Use Case
Removing duplicate email addresses.

## Code Example

```java
numbers.stream()
       .distinct()
       .forEach(System.out::println);
```

---

# Q68. What is limit() in Stream API?

## Detailed Answer
limit() restricts the number of elements processed from a stream. It is useful for pagination and top-N operations.

## Real-world Use Case
Showing top 10 customers.

## Code Example

```java
numbers.stream()
       .limit(5)
       .forEach(System.out::println);
```

---

# Q69. What is reduce() in Stream API?

## Detailed Answer
reduce() performs aggregation operations by repeatedly combining stream elements into a single result.

## Real-world Use Case
Calculating total revenue.

## Code Example

```java
int sum =
    numbers.stream()
           .reduce(0,
                   Integer::sum);
```

---

# Q70. What is collect() in Stream API?

## Detailed Answer
collect() gathers stream results into collections, maps, strings, or custom containers. It is a terminal operation.

## Real-world Use Case
Converting filtered employee data into a list.

## Code Example

```java
List<Integer> result =
    numbers.stream()
           .collect(Collectors.toList());
```

---

# Q71. What are Collectors in Java?

## Detailed Answer
Collectors provide utility methods for common reduction operations such as grouping, partitioning, counting, and joining.

## Real-world Use Case
Generating department-wise employee reports.

## Code Example

```java
Collectors.counting();
Collectors.joining(",");
```

---

# Q72. What is groupingBy() Collector?

## Detailed Answer
groupingBy() groups elements based on a classification function and returns a Map containing grouped results.

## Real-world Use Case
Grouping employees by department.

## Code Example

```java
Map<String,List<Employee>> map =
employees.stream()
.collect(Collectors.groupingBy(
         Employee::getDepartment
));
```

---

# Q73. What is partitioningBy() Collector?

## Detailed Answer
partitioningBy() divides stream elements into two groups based on a boolean condition. It always returns a Map<Boolean, List<T>>.

## Real-world Use Case
Separating active and inactive users.

## Code Example

```java
Map<Boolean,List<Employee>> result =
employees.stream()
.collect(Collectors.partitioningBy(
          e -> e.getSalary() > 50000
));
```

---

# Q74. What is Parallel Stream?

## Detailed Answer
Parallel Streams divide tasks among multiple threads, allowing concurrent processing and improved performance for large datasets.

## Real-world Use Case
Bulk processing of millions of transactions.

## Code Example

```java
numbers.parallelStream()
       .forEach(System.out::println);
```

---

# Q75. When should Parallel Streams be avoided?

## Detailed Answer
Parallel Streams should be avoided for small datasets, I/O-intensive tasks, shared mutable state, and applications requiring strict ordering. Improper use can reduce performance.

## Real-world Use Case
Avoid using parallel streams for database calls inside stream pipelines.

## Code Example

```java
employees.parallelStream()
         .forEach(
             e -> updateDatabase(e)
         );
```

---

✅ Part 3 Completed (Q51–Q75)

### Topics Covered
- Generics
- Type Erasure
- Functional Interfaces
- Lambda Expressions
- Method References
- Optional
- Stream API
- Intermediate Operations
- Terminal Operations
- Collectors
- Grouping & Partitioning
- Parallel Streams

### Next Part (Q76–Q100)
Multithreading & Concurrency:
- Thread Lifecycle
- Runnable vs Callable
- Synchronization
- Deadlock
- Volatile
- Executor Framework
- CompletableFuture
- Concurrent Collections
- Lock API
- Producer Consumer
- Fork Join Framework
- Real-time Interview Scenarios