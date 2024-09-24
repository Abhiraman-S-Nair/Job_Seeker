# **Object-Oriented Programming (OOP) Concepts**

**Object-Oriented Programming (OOP)** is a programming paradigm based on the concept of objects, which can contain data and code: data in the form of fields (attributes or properties), and code in the form of procedures (methods). OOP principles help in structuring software by modeling real-world entities into objects.

---

## 1. Encapsulation

**Encapsulation** is the process of bundling the data (attributes) and methods (functions) that operate on the data into a single unit or class. It also involves restricting direct access to some of an object's components, which is known as data hiding.

### Example in Python:
```python
class Employee:
    def __init__(self, name, salary):
        self.name = name       # Public attribute
        self.__salary = salary  # Private attribute using name mangling

    def get_salary(self):
        return self.__salary  # Accessing private attribute via method

emp = Employee("John", 5000)
print(emp.name)        # Output: John
print(emp.get_salary())  # Output: 5000
```

### Example in C++:
```cpp
class Employee {
private:
    int salary;

public:
    std::string name;
    
    Employee(std::string emp_name, int emp_salary) {
        name = emp_name;
        salary = emp_salary;
    }

    int getSalary() {
        return salary;
    }
};

int main() {
    Employee emp("John", 5000);
    std::cout << emp.name << std::endl;        // Output: John
    std::cout << emp.getSalary() << std::endl; // Output: 5000
}
```

**Key Points:**
- Encapsulation hides the internal state and allows controlled access via methods.
- Use of access modifiers (private, public, protected) in C++.

---

## 2. Inheritance

**Inheritance** is the mechanism by which one class can inherit properties and behaviors (methods) from another class. The new class (derived class) can also have its own additional properties or methods.

### Example in Python:
```python
class Animal:
    def sound(self):
        return "Some sound"

class Dog(Animal):
    def sound(self):
        return "Bark"

dog = Dog()
print(dog.sound())  # Output: Bark
```

### Example in C++:
```cpp
class Animal {
public:
    virtual void sound() {
        std::cout << "Some sound" << std::endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        std::cout << "Bark" << std::endl;
    }
};

int main() {
    Dog dog;
    dog.sound();  // Output: Bark
}
```

**Key Points:**
- Inheritance allows code reuse by creating a hierarchy of classes.
- In C++, `override` keyword is used to explicitly state that a method is overriding a base class method.

---

## 3. Polymorphism

**Polymorphism** allows objects of different types to be treated as objects of a common superclass. It is often used to implement method overriding and method overloading.

### Example (Method Overriding) in Python:
```python
class Animal:
    def speak(self):
        return "Animal speaks"

class Cat(Animal):
    def speak(self):
        return "Meow"

def animal_speak(animal):
    print(animal.speak())

animal_speak(Animal())  # Output: Animal speaks
animal_speak(Cat())     # Output: Meow
```

### Example in C++:
```cpp
class Animal {
public:
    virtual void speak() {
        std::cout << "Animal speaks" << std::endl;
    }
};

class Cat : public Animal {
public:
    void speak() override {
        std::cout << "Meow" << std::endl;
    }
};

void animal_speak(Animal* animal) {
    animal->speak();
}

int main() {
    Animal a;
    Cat c;
    animal_speak(&a);  // Output: Animal speaks
    animal_speak(&c);  // Output: Meow
}
```

**Key Points:**
- **Method Overriding**: A subclass can provide a specific implementation for a method that is already defined in its superclass.
- **Compile-time vs Run-time Polymorphism**: Method overloading is an example of compile-time polymorphism, whereas overriding is an example of run-time polymorphism.

---

## 4. Abstraction

**Abstraction** is the concept of hiding the complex implementation details and showing only the necessary features of an object. It can be implemented using abstract classes or interfaces.

### Example in Python:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14 * self.radius * self.radius

circle = Circle(5)
print(circle.area())  # Output: 78.5
```

### Example in C++:
```cpp
class Shape {
public:
    virtual double area() = 0;  // Pure virtual function
};

class Circle : public Shape {
private:
    double radius;
    
public:
    Circle(double r) : radius(r) {}
    double area() override {
        return 3.14 * radius * radius;
    }
};

int main() {
    Circle c(5);
    std::cout << c.area() << std::endl;  // Output: 78.5
}
```

**Key Points:**
- Abstract classes cannot be instantiated.
- They provide a blueprint for derived classes to implement specific methods.

---

## 5. Classes and Objects

**Classes** are blueprints for creating objects (instances), and **objects** are instances of classes.

### Example in Python:
```python
class Car:
    def __init__(self, model, year):
        self.model = model
        self.year = year

    def display_info(self):
        return f"Model: {self.model}, Year: {self.year}"

car = Car("Tesla", 2022)
print(car.display_info())  # Output: Model: Tesla, Year: 2022
```

### Example in C++:
```cpp
class Car {
public:
    std::string model;
    int year;

    Car(std::string m, int y) : model(m), year(y) {}
    
    void display_info() {
        std::cout << "Model: " << model << ", Year: " << year << std::endl;
    }
};

int main() {
    Car car("Tesla", 2022);
    car.display_info();  // Output: Model: Tesla, Year: 2022
}
```

**Key Points:**
- A **class** is a user-defined data type that has attributes and methods.
- An **object** is an instance of a class and has access to its methods and attributes.

---

## 6. SOLID Principles

**SOLID** is an acronym for five design principles that make software designs more understandable, flexible, and maintainable.

- **S**: Single Responsibility Principle (SRP)
- **O**: Open/Closed Principle (OCP)
- **L**: Liskov Substitution Principle (LSP)
- **I**: Interface Segregation Principle (ISP)
- **D**: Dependency Inversion Principle (DIP)

### Example (SRP in Python):
```python
class Report:
    def __init__(self, data):
        self.data = data
    
    def generate_report(self):
        return f"Report data: {self.data}"

class ReportPrinter:
    def print_report(self, report):
        print(report.generate_report())

report = Report("Data")
printer = ReportPrinter()
printer.print_report(report)
```

---

## 7. Virtual Functions and Overriding in C++

**Virtual functions** in C++ allow derived classes to override methods in the base class. This enables **run-time polymorphism**.

### Example:
```cpp
class Base {
public:
    virtual void show() {
        std::cout << "Base class" << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        std::cout << "Derived class" << std::endl;
    }
};

int main() {
    Base* base_ptr;
    Derived d;
    base_ptr = &d;
    
    base_ptr->show();  // Output: Derived class
}
```

**Key Points:**
- **Virtual functions** enable polymorphism, allowing derived classes to override base class methods.
- The `virtual` keyword is used in the base class, and `override` is used in the derived class to indicate the method is being overridden.

---

## Conclusion

Object-Oriented Programming (OOP) principles, such as **Encapsulation**, **Inheritance**, **Polymorphism**, and **Abstraction**, form the foundation of modern programming languages. Mastering these concepts will help you build scalable, maintainable, and robust software systems.
