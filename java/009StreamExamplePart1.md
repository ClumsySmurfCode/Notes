# Stream API 

Below are some examples demonstrating the use of Java 8 Stream API functions.

# DATA Set 

         static List<Student> list = Arrays.asList(
                    new Student(1, "Aditya", "Mall", 30, "Male", "Mechanical Engineering", 2014, "Mumbai", 122),
                    new Student(2, "Pulkith", "Singh", 26, "Male", "Computer Engineering", 2018, "Delhi", 67),
                    new Student(3, "Ankita", "Patil", 25, "Female", "Computer Engineering", 2019, "Kerala", 164),
                    new Student(4, "Satish", "Malaghan", 30, "Male", "Mechanical Engineering", 2014, "Kerala", 26),
                    new Student(5, "Darshan", "Mukd", 23, "Male", "Instrumentation Engineering", 2022, "Mumbai", 12),
                    new Student(6, "Chetan", "Star", 24, "Male", "Mechanical Engineering", 2023, "Karnataka", 90),
                    new Student(7, "Appu", "Raj", 31, "Male", "Electronics Engineering", 2014, "Karnataka", 324),
                    new Student(8, "Nam", "Dev", 31, "Male", "Computer Engineering", 2014, "Karnataka", 433),
                    new Student(9, "Sonu", "Shankar", 27, "Female", "Computer Engineering", 2018, "Karnataka", 7),
                    new Student(10, "Satyam", "Pandey", 26, "Male", "Biotech Engineering", 2017, "Mumbai", 98));

            
## 1. Find the Count of Students in Each Department

      public static void findTheCountOfStudentsInEachDepartment() {
          Map<String, Long> collect = list.stream()
                  .collect(Collectors.groupingBy(Student::getDepartmantName, Collectors.counting()));
          System.out.println("Count of Students in each Department" + collect);
      }

## 2. Find All Department Names

      public static void findAllDepartmentNames() {
          List<String> deptName = list.stream().map(Student::getDepartmantName).distinct().collect(Collectors.toList());
          System.out.println("Department Names " + deptName);
      }
## 3. Find Students Below the Age of 25

      public static void findAgeLessThan25() {
          List<Student> collect = list.stream().filter(student -> student.getAge() < 25).collect(Collectors.toList());
          System.out.println("List of Students whose Age is less than 25 " + collect);
      }
## 4. Find the Maximum Age

      public static void findMaxAge() {
          OptionalInt max = list.stream().mapToInt(Student::getAge).max();
          System.out.println("Max age of students " + max.getAsInt());
      }
      
## 5. Find the Average Age of Male and Female Students

      public static void findAvgAgeOfMaleAndFemale() {
          Map<String, Double> collect = list.stream()
                  .collect(Collectors.groupingBy(Student::getGender, Collectors.averagingInt(Student::getAge)));
          System.out.println("Average age of Male and Female students " + collect);
      }

## 6. Find the Count of Students in Each Department (Duplicate Method)

      public static void findcountOfStudentInEachDepartment() {
          Map<String, Long> collect = list.stream()
                  .collect(Collectors.groupingBy(Student::getDepartmantName, Collectors.counting()));
          System.out.println(collect);
      }
      
## 7. The findYougestStudent method is designed to find the youngest student in the given list of Student objects. Let's break down the method:
       public static void findYougestStudent() {
        int min = list.stream().mapToInt(Student::getAge).min().getAsInt();
        System.out.println("Minimum age of student is " + min);
    
        // or
    
        Student student = list.stream().min(Comparator.comparing(Student::getAge)).get();
        System.out.println("Young student is " + student);
    }

## 8. getSeniorStudent
    public static void getSeniorStudent() {

        int seniorStudent = list.stream().filter(t -> t.getGender().equals("Female")).mapToInt(Student::getAge).max()
                .getAsInt();

        System.out.println("Senior Female student is " + seniorStudent);

        Student student = list.stream().filter(t -> t.getGender().equals("Female"))
                .max(Comparator.comparing(Student::getAge)).get();

        System.out.println("Senior Female student is " + student);

    }
    
## 9. findRankBetween50to100
    public static void findRankBetween50to100() {

        List<Student> collect = list.stream().filter(t -> t.getRank() > 50 && t.getRank() < 100)
                .collect(Collectors.toList());
        System.out.println(collect);

    }
    
## 10. findTheMaxcountStudentsIndepartment
    public static void findTheMaxcountStudentsIndepartment() {

        Entry<String, Long> entry = list.stream()
                .collect(Collectors.groupingBy(Student::getDepartmantName, Collectors.counting())).entrySet().stream()
                .max(Map.Entry.comparingByValue()).get();

        System.out.println(entry);

    }
    
## 11. findTheEmployeeWhoLeavesInMumbaiAndSortBytheriNames
    public static void findTheEmployeeWhoLeavesInMumbaiAndSortBytheriNames() {

        List<Student> collect = list.stream().filter(t -> t.getCity().equals("Mumbai"))
                .sorted(Comparator.comparing(Student::getFirstName)).collect(Collectors.toList());
        System.out.println(collect);

    }
    
## 12. find noOfStudentPresentInCollege
    public static void noOfStudentPresentInCollege() {

        long count = list.stream().count();

        System.out.println(count);

    }
    
## 13. find findTheDepartmentHavingMaxStudent
    public static void findTheDepartmentHavingMaxStudent() {

        Entry<String, Long> entry = list.stream()
                .collect(Collectors.groupingBy(Student::getDepartmantName, Collectors.counting())).entrySet().stream()
                .max(Map.Entry.comparingByValue()).get();

        System.out.println(entry.getKey() + " " + entry.getValue());

    }
    
## 14. find findTheAverageRankInAllDepartments
    public static void findTheAverageRankInAllDepartments() {

        Map<String, Double> collect = list.stream()
                .collect(Collectors.groupingBy(Student::getDepartmantName, Collectors.averagingInt(Student::getRank)));

        System.out.println(collect);

    }

## 15. find findHighRankInEachDepartment
    public static void findHighRankInEachDepartment() {

        Map<String, Optional<Student>> collect = list.stream().collect(Collectors.groupingBy(Student::getDepartmantName,
                Collectors.minBy(Comparator.comparing(Student::getRank))));

        System.out.println(collect);

    }
    
## 16. find sortTheStudentsBasedonRank
    public static void sortTheStudentsBasedonRank() {

        List<Student> collect = list.stream().sorted(Comparator.comparing(Student::getRank))

                .collect(Collectors.toList());

        System.out.println(collect);
    }

## 17. find findTheSecondHighestRank
    public static void findTheSecondHighestRank() {

        Student student = list.stream().sorted(Comparator.comparing(Student::getRank)).skip(1).findFirst().get();

        System.out.println(student);

    }
    
## 18. find displayRanksInEachDepartmentInDecendingOrder
    public static void displayRanksInEachDepartmentInDecendingOrder() {

        Map<String, List<Student>> collect = list.stream()
                .collect(Collectors.groupingBy(Student::getDepartmantName,
                        Collectors.collectingAndThen(Collectors.toList(), list -> list.stream()
                                .sorted(Comparator.comparing(Student::getRank)).collect(Collectors.toList()))));
        System.out.println(collect);
    }


