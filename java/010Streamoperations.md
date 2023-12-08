In Java 8, streams operations are broadly categorized into three types: stream creation and source, intermediate operations, and terminal operations.

1. Stream Creation and Source:
Stream Creation: Streams can be created from various sources such as collections, arrays, I/O channels, and generator functions.

java
Copy code
List<String> list = Arrays.asList("apple", "banana", "orange");
Stream<String> streamFromList = list.stream();
Stream Generation: Streams can be generated using static methods in the Stream interface.

java
Copy code
Stream<String> generatedStream = Stream.generate(() -> "element").limit(5);
Other Sources: Streams can also be created from I/O operations, arrays, and other sources.

2. Intermediate Operations:
Filtering: These operations filter elements based on a certain condition.

java
Copy code
stream.filter(element -> element.startsWith("a"))
Mapping: Transform elements from one form to another.

java
Copy code
stream.map(String::toUpperCase)
FlatMap: Flatten nested structures (e.g., lists within lists).

java
Copy code
stream.flatMap(line -> Arrays.stream(line.split("\\s+")))
Sorting: Arrange elements based on a comparator.

java
Copy code
stream.sorted()
Peeking: Perform an action on each element without affecting the stream.

java
Copy code
stream.peek(System.out::println)
Limit and Skip: Limit the number of elements or skip a certain number of elements.

java
Copy code
stream.limit(5)
Distinct: Remove duplicate elements.

java
Copy code
stream.distinct()
3. Terminal Operations:
forEach: Perform an action on each element of the stream.

java
Copy code
stream.forEach(System.out::println)
collect: Convert elements of the stream into a different form, such as a List or Map.

java
Copy code
List<String> list = stream.collect(Collectors.toList())
reduce: Perform a reduction on the elements.

java
Copy code
Optional<String> concatenated = stream.reduce((s1, s2) -> s1 + s2);
count: Count the number of elements in the stream.

java
Copy code
long count = stream.count()
anyMatch, allMatch, noneMatch: Check if any, all, or no elements match a given condition.

java
Copy code
boolean anyStartsWithA = stream.anyMatch(s -> s.startsWith("A"));
findAny and findFirst: Return any or the first element of the stream.

java
Copy code
Optional<String> anyElement = stream.findAny();
Optional<String> firstElement = stream.findFirst();
min and max: Find the minimum or maximum element based on a comparator.

java
Copy code
Optional<String> minElement = stream.min(Comparator.naturalOrder());
Optional<String> maxElement = stream.max(Comparator.naturalOrder());
toArray: Convert the stream into an array.

java
Copy code
String[] array = stream.toArray(String[]::new);
