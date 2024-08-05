The SOLID principles are a set of five design principles in object-oriented programming that help developers create more maintainable, scalable, and robust software. Here's a brief overview of each principle with example code:

### 1. Single Responsibility Principle (SRP)
A class should have only one reason to change.

**Example:**
```python
class UserAuthenticator:
    def authenticate(self, username, password):
        # Logic for user authentication
        pass

class EmailService:
    def send_welcome_email(self, user_email):
        # Logic for sending a welcome email
        pass
```

### 2. Open/Closed Principle (OCP)
Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

**Example:**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

# Extending without modifying existing code
class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        return 0.5 * self.base * self.height
```

### 3. Liskov Substitution Principle (LSP)
Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

**Example:**
```python
class Bird:
    def fly(self):
        pass

class Sparrow(Bird):
    def fly(self):
        # Sparrow flying logic
        pass

class Ostrich(Bird):
    def fly(self):
        raise Exception("Ostriches can't fly")

# Following LSP
class Ostrich(Bird):
    def walk(self):
        # Ostrich walking logic
        pass
```

### 4. Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use.

**Example:**
```python
from abc import ABC, abstractmethod

class Printer(ABC):
    @abstractmethod
    def print_document(self, document):
        pass

class Scanner(ABC):
    @abstractmethod
    def scan_document(self, document):
        pass

class AllInOnePrinter(Printer, Scanner):
    def print_document(self, document):
        # Print logic
        pass

    def scan_document(self, document):
        # Scan logic
        pass

class SimplePrinter(Printer):
    def print_document(self, document):
        # Print logic
        pass
```

### 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

**Example:**
```python
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def connect(self):
        pass

class MySQLDatabase(Database):
    def connect(self):
        # MySQL connection logic
        pass

class PostgreSQLDatabase(Database):
    def connect(self):
        # PostgreSQL connection logic
        pass

class DataAccess:
    def __init__(self, db: Database):
        self.db = db

    def connect_to_database(self):
        self.db.connect()

# Using Dependency Injection
mysql_db = MySQLDatabase()
data_access = DataAccess(mysql_db)
data_access.connect_to_database()
```

By adhering to these principles, developers can create software that is easier to maintain, extend, and refactor, ultimately leading to more robust and scalable applications.
