# Java 8 Stream API Functions

## 1. `filter`
   - **Description:** Filters elements based on a given condition.
   - **Example:**
     ```java
     List<String> fruits = Arrays.asList("apple", "banana", "orange", "grape");
     List<String> filteredFruits = fruits.stream()
                                         .filter(fruit -> fruit.startsWith("a"))
                                         .collect(Collectors.toList());
     ```

## 2. `map`
   - **Description:** Transforms each element using the provided function.
   - **Example:**
     ```java
     List<String> words = Arrays.asList("hello", "world");
     List<String> upperCaseWords = words.stream()
                                       .map(String::toUpperCase)
                                       .collect(Collectors.toList());
     ```

## 3. `flatMap`
   - **Description:** Flattens nested collections or arrays into a single stream.
   - **Example:**
     ```java
     List<List<String>> listOfLists = Arrays.asList(Arrays.asList("a", "b"), Arrays.asList("c", "d"));
     List<String> flatList = listOfLists.stream()
                                       .flatMap(Collection::stream)
                                       .collect(Collectors.toList());
     ```

## 4. `forEach`
   - **Description:** Performs an action for each element in the stream.
   - **Example:**
     ```java
     List<String> colors = Arrays.asList("red", "green", "blue");
     colors.stream().forEach(System.out::println);
     ```

## 5. `collect`
   - **Description:** Transforms the elements into a different form, e.g., a List or Map.
   - **Example:**
     ```java
     List<String> animals = Arrays.asList("lion", "tiger", "cheetah");
     Set<String> animalSet = animals.stream().collect(Collectors.toSet());
     ```

## 6. `reduce`
   - **Description:** Performs a reduction on the elements using an associative accumulation function.
   - **Example:**
     ```java
     List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
     Optional<Integer> sum = numbers.stream().reduce((a, b) -> a + b);
     ```

## 7. `distinct`
   - **Description:** Removes duplicate elements from the stream.
   - **Example:**
     ```java
     List<String> colors = Arrays.asList("red", "green", "blue", "red");
     List<String> uniqueColors = colors.stream().distinct().collect(Collectors.toList());
     ```

## 8. `sorted`
   - **Description:** Sorts the elements of the stream.
   - **Example:**
     ```java
     List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
     List<Integer> sortedNumbers = numbers.stream().sorted().collect(Collectors.toList());
     ```

## 9. `peek`
   - **Description:** Performs an action on each element without affecting the stream.
   - **Example:**
     ```java
     List<String> fruits = Arrays.asList("apple", "banana", "orange");
     List<String> upperCaseFruits = fruits.stream()
                                         .map(String::toUpperCase)
                                         .peek(System.out::println)
                                         .collect(Collectors.toList());
     ```

## 10. `limit` and `skip`
    - **Description:** Limits or skips a specified number of elements.
    - **Example:**
      ```java
      List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
      List<Integer> limitedNumbers = numbers.stream().limit(3).collect(Collectors.toList());
      List<Integer> skippedNumbers = numbers.stream().skip(2).collect(Collectors.toList());
      ```

## 11. `anyMatch`, `allMatch`, and `noneMatch`
    - **Description:** Checks if any, all, or no elements match a given condition.
    - **Example:**
      ```java
      List<String> fruits = Arrays.asList("apple", "banana", "orange");
      boolean anyStartsWithA = fruits.stream().anyMatch(fruit -> fruit.startsWith("a"));
      boolean allStartWithA = fruits.stream().allMatch(fruit -> fruit.startsWith("a"));
      boolean noneStartWithZ = fruits.stream().noneMatch(fruit -> fruit.startsWith("z"));
      ```

## 12. `findAny` and `findFirst`
    - **Description:** Returns any or the first element of the stream.
    - **Example:**
      ```java
      List<String> colors = Arrays.asList("red", "green", "blue");
      Optional<String> anyColor = colors.stream().findAny();
      Optional<String> firstColor = colors.stream().findFirst();
      ```

## 13. `min` and `max`
    - **Description:** Finds the minimum or maximum element based on a comparator.
    - **Example:**
      ```java
      List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
      Optional<Integer> minNumber = numbers.stream().min(Comparator.naturalOrder());
      Optional<Integer> maxNumber = numbers.stream().max(Comparator.naturalOrder());
      ```

## 14. `count`
    - **Description:** Counts the number of elements in the stream.
    - **Example:**
      ```java
      List<String> fruits = Arrays.asList("apple", "banana", "orange");
      long count = fruits.stream().count();
      ```

## 15. `toArray`
    - **Description:** Converts the stream into an array.
    - **Example:**
      ```java
      List<String> fruits = Arrays.asList("apple", "banana", "orange");
      String[] fruitArray = fruits.stream().toArray(String[]::new);
      ```

**Note:** This is not an exhaustive list, and there are more functions and variations available in the Java 8 Stream API.


# Java 8 Stream API Functions

## Stream Creation and Source

1. **`stream()`:**
   - **Example:**
     ```java
     List<String> list = Arrays.asList("apple", "banana", "orange");
     Stream<String> stream = list.stream();
     ```
   - **Explanation:** Converts a collection into a stream.

2. **`of()`:**
   - **Example:**
     ```java
     Stream<String> stream = Stream.of("apple", "banana", "orange");
     ```
   - **Explanation:** Creates a stream from individual elements.

3. **`generate()`:**
   - **Example:**
     ```java
     Stream<String> stream = Stream.generate(() -> "element").limit(5);
     ```
   - **Explanation:** Generates an infinite stream based on a supplier.

4. **`iterate()`:**
   - **Example:**
     ```java
     Stream<Integer> stream = Stream.iterate(0, n -> n + 2).limit(5);
     ```
   - **Explanation:** Generates an infinite stream with a seed and a function.

5. **`concat()`:**
   - **Example:**
     ```java
     Stream<String> stream1 = Stream.of("apple", "banana");
     Stream<String> stream2 = Stream.of("orange", "grape");
     Stream<String> concatenated = Stream.concat(stream1, stream2);
     ```
   - **Explanation:** Concatenates two streams.

## Intermediate Operations

6. **`filter()`:**
   - **Example:**
     ```java
     stream.filter(s -> s.length() > 5)
     ```
   - **Explanation:** Filters elements based on a given condition.

7. **`map()`:**
   - **Example:**
     ```java
     stream.map(String::toUpperCase)
     ```
   - **Explanation:** Transforms each element using a function.

8. **`flatMap()`:**
   - **Example:**
     ```java
     stream.flatMap(line -> Arrays.stream(line.split("\\s+")))
     ```
   - **Explanation:** Flattens nested collections.

9. **`distinct()`:**
   - **Example:**
     ```java
     stream.distinct()
     ```
   - **Explanation:** Removes duplicate elements.

10. **`sorted()`:**
    - **Example:**
      ```java
      stream.sorted()
      ```
    - **Explanation:** Sorts the elements.

11. **`peek()`:**
    - **Example:**
      ```java
      stream.peek(System.out::println)
      ```
    - **Explanation:** Performs an action on each element without affecting the stream.

12. **`limit()`:**
    - **Example:**
      ```java
      stream.limit(5)
      ```
    - **Explanation:** Limits the number of elements in the stream.

13. **`skip()`:**
    - **Example:**
      ```java
      stream.skip(2)
      ```
    - **Explanation:** Skips the first N elements of the stream.

## Terminal Operations

14. **`forEach()`:**
    - **Example:**
      ```java
      stream.forEach(System.out::println)
      ```
    - **Explanation:** Performs an action for each element.

15. **`collect()`:**
    - **Example:**
      ```java
      List<String> list = stream.collect(Collectors.toList())
      ```
    - **Explanation:** Transforms elements into a different form (e.g., a collection).

16. **`reduce()`:**
    - **Example:**
      ```java
      Optional<String> concatenated = stream.reduce((s1, s2) -> s1 + s2);
      ```
    - **Explanation:** Performs a reduction on the elements.

17. **`count()`:**
    - **Example:**
      ```java
      long count = stream.count()
      ```
    - **Explanation:** Returns the count of elements.

18. **`anyMatch()`, `allMatch()`, `noneMatch()`:**
    - **Example:**
      ```java
      boolean anyStartsWithA = stream.anyMatch(s -> s.startsWith("A"));
      ```
    - **Explanation:** Checks if any, all, or none of the elements match a condition.

19. **`findFirst()` and `findAny()`:**
    - **Example:**
      ```java
      Optional<String> anyElement = stream.findAny();
      Optional<String> firstElement = stream.findFirst();
      ```
    - **Explanation:** Returns the first or any element.

20. **`min()` and `max()`:**
    - **Example:**
      ```java
      Optional<String> minElement = stream.min(Comparator.naturalOrder());
      Optional<String> maxElement = stream.max(Comparator.naturalOrder());
      ```
    - **Explanation:** Finds the minimum or maximum element.

21. **`toArray()`:**
    - **Example:**
      ```java
      String[] array = stream.toArray(String[]::new);
      ```
    - **Explanation:** Converts the stream into an array.

22. **`forEachOrdered()`:**
    - **Example:**
      ```java
      stream.parallel().forEachOrdered(System.out::println);
      ```
    - **Explanation:** Performs an action for each element, maintaining order in parallel streams.
