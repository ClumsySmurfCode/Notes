## Reference :
https://www.youtube.com/watch?v=K1iu1kXkVoA


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
