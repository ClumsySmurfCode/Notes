## JAVA 8 
Java 8 introduced several significant features, especially in terms of functional programming. Here's an overview of some key features that are important for interview preparation:

#### JAVA Versions
![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/b5503af8-6ca7-442d-ab84-26efc660402d)

### Lambda Expressions:
Lambda expressions provide a concise way to express instances of single-method interfaces (functional interfaces). They introduce functional programming constructs to Java.

      Example: (a, b) -> a + b

### Functional Interfaces:
An interface with a single abstract method is called a functional interface. The @FunctionalInterface annotation can be used to ensure that the interface has only one abstract method.

        Example:
        @FunctionalInterface
        public interface MyFunctionalInterface {
            int doSomething(int a, int b);
        }
### Streams:
The Stream API allows you to process collections of data in a functional style. It includes methods like filter, map, reduce, and more.

        Example:
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        int sum = numbers.stream()
                        .filter(n -> n % 2 == 0)
                        .mapToInt(Integer::intValue)
                        .sum();

### Default Methods:
Default methods allow you to add new methods to interfaces without breaking existing implementations. Classes can now inherit methods from interfaces.

        Example:
        interface MyInterface {
            default void myDefaultMethod() {
                System.out.println("Default method");
            }
        }

### Method References:
Method references provide a shorthand notation for lambda expressions when calling a method.
        
        Example:
        // Using lambda expression
        list.forEach(item -> System.out.println(item));
        
        // Using method reference
        list.forEach(System.out::println);

### Optional:
Optional is a container object which may or may not contain a non-null value. It helps to avoid NullPointerException.

        Example:
        Optional<String> name = Optional.ofNullable(getName());

### New Date and Time API:
The java.time package provides a comprehensive set of classes for handling date and time.

        Example:
        LocalDate today = LocalDate.now();
        
### Nashorn JavaScript Engine:
Java 8 includes a new JavaScript engine called Nashorn, which provides 2 to 10 times better performance, as well as a more powerful API.

### Parallel Streams:
The Stream API also provides parallel processing of collections, making it easier to take advantage of multi-core processors.

### Collectors:
The Collectors class provides several utility methods for working with streams, especially useful for converting a stream into a collection or a single value.


### Generic Methods in Java 
Generic methods in Java allow you to write a method that can work with any type of data. By using generics, you can create methods and classes that are type-safe and can work with different data types without sacrificing type information at compile time. Here's how you can define and use generic methods in Java:

Syntax for Generic Methods:
      
            public class MyClass {
                // Generic method
                public <T> void myGenericMethod(T value) {
                    // Method implementation
                    System.out.println("Received value: " + value);
                }
            }

##### Explanation:
<T> declares a type parameter, which can be any non-primitive data type or a class.
T is a placeholder for the actual type that will be provided when the method is called.
Example Usage:

            public class Main {
                public static void main(String[] args) {
                    MyClass myClass = new MyClass();
            
                    // Calling generic method with Integer
                    myClass.myGenericMethod(10);
            
                    // Calling generic method with String
                    myClass.myGenericMethod("Hello, Generics!");
                }
            }
            
In the example above, the myGenericMethod can accept arguments of any type. When calling the method, the type parameter T is inferred based on the type of the argument provided.

##### Generic Methods with Bounds:
You can also use bounds to restrict the types that can be used with a generic method. For example:

            public class MyClass {
                // Generic method with bounds
                public <T extends Number> void processNumber(T number) {
                    // Method implementation
                    System.out.println("Received number: " + number);
                }
            }
            
In this case, the generic method processNumber can only accept types that extend the Number class.

##### Wildcard in Generic Methods:
You can use wildcard (?) as a type argument in a generic method to represent an unknown type. For example:

            public class MyClass {
                // Generic method with wildcard
                public void printList(List<?> list) {
                    for (Object item : list) {
                        System.out.println(item);
                    }
                }
            }

In this example, printList can accept a list of any type.



