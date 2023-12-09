# map and reduce 
https://www.youtube.com/watch?v=w-iwyp_A7e8

![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/98d025a7-dd94-4610-a068-22da02fedc28)

## Map
map() Function:
The map() function in the Stream API is an intermediate operation that transforms each element of a stream using a given function. It creates a new stream consisting of the results of applying the provided function to each element of the original stream.

Example:
Suppose you have a list of numbers and you want to square each number using map():

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


## Reduce 
![image](https://github.com/himanshumalvi/himanshumalvi/assets/45842963/c274407e-3f0b-40fb-b4b2-715d9a54b0da)

    List<Integer> numbers = Arrays.asList(3, 7, 8, 1, 5, 9);

    List<String> words = Arrays.asList("corejava", "spring", "hibernate");
--- 
    int sum1 = numbers.stream().mapToInt(i -> i).sum();
    
    System.out.println(sum1);
--- 
    Integer reduceSum = numbers.stream().reduce(0, (a, b) -> a + b);
    
    System.out.println(reduceSum);
--- 
    Optional<Integer> reduceSumWithMethodReference = numbers.stream().reduce(Integer::sum);
    
    System.out.println(reduceSumWithMethodReference.get());
--- 
    Integer mulResult = numbers.stream().reduce(1, (a, b) -> a * b);
    
    System.out.println(mulResult);
--- 
    Integer maxvalue = numbers.stream().reduce(0, (a, b) -> a > b ? a : b);
    
    System.out.println(maxvalue);
--- 
    Integer maxvalueWithMethodReference = numbers.stream().reduce(Integer::max).get();
    System.out.println(maxvalueWithMethodReference);
--- 
    String longestString = words.stream()
      .reduce((word1, word2) -> word1.length() > word2.length() ? word1 : word2)
      .get();
      
    System.out.println(longestString);
--- 
//get employee whose grade A
//get salary

      double avgSalary = EmployeeDatabase.getEmployees().stream()
        .filter(employee -> employee.getGrade().equalsIgnoreCase("A"))
        .map(employee -> employee.getSalary())
        .mapToDouble(i -> i)
        .average().getAsDouble();
        
        System.out.println(avgSalary);

--- 


    double sumSalary = EmployeeDatabase.getEmployees().stream()
      .filter(employee -> employee.getGrade().equalsIgnoreCase("A"))
      .map(employee -> employee.getSalary())
      .mapToDouble(i -> i)
      .sum();
      
    System.out.println(sumSalary);
