# Java 8, the map and flatMap operations are commonly used in the context of streams.
![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/fc436641-8ad3-4f42-a0c9-b510811e4b3a)

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/7bec34cc-8026-4fd6-90d2-b2198c9ce251)


## 1. map Operation:
The map operation is used to transform each element of a stream using a provided function. It applies the function to each element and produces a new stream of the transformed values.

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/cd66ce1c-a514-469c-9bb3-7b00bc9a7d24)


Example:
Suppose you have a list of integers, and you want to create a new stream where each integer is squared.


      import java.util.Arrays;
      import java.util.List;
      import java.util.stream.Collectors;
      
      public class MapExample {
          public static void main(String[] args) {
              List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
      
              // Using map to square each element
              List<Integer> squaredNumbers = numbers.stream()
                      .map(x -> x * x)
                      .collect(Collectors.toList());
      
              System.out.println("Original Numbers: " + numbers);
              System.out.println("Squared Numbers: " + squaredNumbers);
          }
      }
In this example, the map operation applies the lambda function (x -> x * x) to each element of the stream, squaring each number.

## 2. flatMap Operation:
The flatMap operation is used when each element of the stream is mapped to multiple values, and you want to flatten these multiple values into a single stream.

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/a488423a-2664-4a6b-b76c-927cb4802c0b)


Example:
Suppose you have a list of words, and you want to create a stream of all distinct letters present in these words.

      import java.util.Arrays;
      import java.util.List;
      import java.util.stream.Collectors;
      
      public class FlatMapExample {
          public static void main(String[] args) {
              List<String> words = Arrays.asList("hello", "world");
      
              // Using flatMap to get distinct letters from words
              List<String> distinctLetters = words.stream()
                      .flatMap(word -> Arrays.stream(word.split("")))
                      .distinct()
                      .collect(Collectors.toList());
      
              System.out.println("Original Words: " + words);
              System.out.println("Distinct Letters: " + distinctLetters);
          }
      }
In this example, the flatMap operation splits each word into an array of letters, and then flatMap is used to flatten these arrays into a single stream. The distinct operation ensures that only unique letters are included in the final result.
