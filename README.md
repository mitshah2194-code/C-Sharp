# C Sharp
# **Complete C#.NET Tutorial - Theory, Practical Examples & Latest Features**

## **Table of Contents**

1. [Introduction to C# & .NET](#introduction)
2. [C# Fundamentals](#fundamentals)
3. [Object-Oriented Programming (OOP)](#oop)
4. [Advanced C# Features](#advanced)
5. [.NET Framework & .NET Core](#dotnet-framework)
6. [LINQ & Collections](#linq)
7. [Async & Parallel Programming](#async)
8. [Entity Framework Core](#ef-core)
9. [Modern C# Features (C# 11, 12)](#modern-features)
10. [Best Practices & Patterns](#best-practices)

---

## **1. Introduction to C# & .NET** {#introduction}

### **1.1 What is C#?**

**C#** (pronounced "C-sharp") is:
- A modern, statically-typed, object-oriented programming language
- Developed by Microsoft in 2000
- Runs on the .NET platform
- Part of the ECMA and ISO standards
- Influences: C++, Java, and VB.NET

### **1.2 What is .NET?**

**.NET** is a free, open-source, cross-platform framework for building applications:

| Version | Release Date | Status | Target |
|---------|--------------|--------|--------|
| **.NET Framework** | 2002 | Legacy (Windows only) | Windows applications |
| **.NET Core 1.0** | June 2016 | Legacy | Cross-platform apps |
| **.NET Core 3.1** | December 2019 | LTS (End: Dec 2022) | Cross-platform |
| **.NET 5** | November 2020 | Out of Support | Unified platform |
| **.NET 6** | November 2021 | LTS (Nov 2024) | Production apps |
| **.NET 7** | November 2022 | Out of Support | Testing/Learning |
| **.NET 8** | November 2023 | **LTS (Nov 2026)** | **Current Standard** |
| **.NET 9** | November 2024 | **Current Release** | **Latest Features** |

### **1.3 .NET Architecture**

```
┌─────────────────────────────────────────────────┐
│          Applications (ASP.NET, WPF, WinForms)  │
├─────────────────────────────────────────────────┤
│          Base Class Library (FCL)                │
│  (Collections, Threading, File I/O, etc.)       │
├─────────────────────────────────────────────────┤
│  Common Language Runtime (CLR)                  │
│  (JIT Compilation, Garbage Collection, etc.)    │
├─────────────────────────────────────────────────┤
│          Operating System                       │
│     (Windows, Linux, macOS)                    │
└─────────────────────────────────────────────────┘
```

### **1.4 Installing .NET**

```bash
# Download from https://dotnet.microsoft.com/download

# Verify installation
dotnet --version     # Check version
dotnet --info        # Detailed info

# Create new project
dotnet new console -n MyApp
cd MyApp
dotnet run
```

---

## **2. C# Fundamentals** {#fundamentals}

### **2.1 Variables & Data Types**

```csharp
// Basic Data Types
byte age = 25;                  // 8-bit unsigned (0-255)
short temperature = -10;        // 16-bit signed
int quantity = 1000;            // 32-bit signed
long population = 8000000000;   // 64-bit signed
float price = 19.99f;           // 32-bit floating point
double pi = 3.14159;            // 64-bit floating point
decimal salary = 50000.50m;     // 128-bit for financial
bool isActive = true;           // Boolean
char grade = 'A';               // Single character
string name = "John Doe";       // String

// Type Inference
var message = "Hello";          // Compiler infers string
var count = 42;                 // Compiler infers int

// Nullable Types (C# 8.0+)
int? nullableInt = null;        // Can hold null
string? nullableString = null;  // Nullable reference type

// var vs dynamic
var x = 10;         // Compile-time: int
dynamic y = 10;     // Runtime: dynamic
// x.NonExistent();  // Compile error
y.NonExistent();    // Runtime error
```

### **2.2 Operators**

```csharp
// Arithmetic Operators
int a = 10, b = 3;
int sum = a + b;         // 13
int difference = a - b;  // 7
int product = a * b;     // 30
int quotient = a / b;    // 3
int remainder = a % b;   // 1
int power = (int)Math.Pow(a, b); // 1000

// Comparison Operators
bool equal = a == b;     // false
bool notEqual = a != b;  // true
bool greater = a > b;    // true
bool less = a < b;       // false
bool greaterOrEqual = a >= b; // true
bool lessOrEqual = a <= b;    // false

// Logical Operators
bool p = true, q = false;
bool and = p && q;       // false
bool or = p || q;        // true
bool not = !p;           // false

// Bitwise Operators
int x = 5;      // 0101
int y = 3;      // 0011
int bitwiseAnd = x & y;  // 0001 = 1
int bitwiseOr = x | y;   // 0111 = 7
int bitwiseXor = x ^ y;  // 0110 = 6
int complement = ~x;     // 1010 (in 2's complement)

// Assignment Operators
int value = 10;
value += 5;  // value = 15
value -= 3;  // value = 12
value *= 2;  // value = 24
value /= 4;  // value = 6
value %= 5;  // value = 1

// Ternary Operator
int age = 20;
string status = age >= 18 ? "Adult" : "Minor";

// Null-Coalescing Operator (C# 8.0+)
string? name = null;
string displayName = name ?? "Anonymous";  // "Anonymous"

// Null-Coalescing Assignment Operator (C# 8.0+)
string? value = null;
value ??= "Default";  // value = "Default"

// Null-Conditional Operator (C# 6.0+)
string? text = null;
int? length = text?.Length;  // null (doesn't throw error)
```

### **2.3 Control Flow**

```csharp
// If-Else
int score = 85;
if (score >= 90)
    Console.WriteLine("A");
else if (score >= 80)
    Console.WriteLine("B");
else if (score >= 70)
    Console.WriteLine("C");
else
    Console.WriteLine("F");

// Switch Statement
string day = "Monday";
switch (day)
{
    case "Monday":
    case "Tuesday":
    case "Wednesday":
        Console.WriteLine("Weekday");
        break;
    case "Saturday":
    case "Sunday":
        Console.WriteLine("Weekend");
        break;
    default:
        Console.WriteLine("Invalid day");
        break;
}

// Switch Expression (C# 8.0+)
string dayType = day switch
{
    "Monday" or "Tuesday" or "Wednesday" or "Thursday" or "Friday" => "Weekday",
    "Saturday" or "Sunday" => "Weekend",
    _ => "Invalid"
};

// Pattern Matching (C# 7.0+)
object obj = 42;
if (obj is int number && number > 0)
    Console.WriteLine($"Positive integer: {number}");

// Loops
// While
int i = 0;
while (i < 5)
{
    Console.WriteLine(i);
    i++;
}

// Do-While
int j = 0;
do
{
    Console.WriteLine(j);
    j++;
} while (j < 5);

// For
for (int k = 0; k < 5; k++)
    Console.WriteLine(k);

// Foreach
string[] colors = { "Red", "Green", "Blue" };
foreach (string color in colors)
    Console.WriteLine(color);

// Range (C# 8.0+)
for (int m = 0..5)  // 0 to 4
    Console.WriteLine(m);
```

### **2.4 Methods**

```csharp
// Basic Method
public int Add(int a, int b)
{
    return a + b;
}

// Method with Optional Parameters
public void Greet(string name, string greeting = "Hello")
{
    Console.WriteLine($"{greeting}, {name}!");
}
Greet("Alice");              // Hello, Alice!
Greet("Bob", "Hi");          // Hi, Bob!

// Named Parameters
Greet(greeting: "Hey", name: "Charlie");

// Method with Parameters Modifier
public void ModifyValue(ref int value)  // ref: pass by reference
{
    value *= 2;
}
int x = 5;
ModifyValue(ref x);
// x is now 10

// out Parameter
public bool TryParse(string input, out int result)
{
    return int.TryParse(input, out result);
}
if (TryParse("42", out int number))
    Console.WriteLine(number);

// params Keyword (variable arguments)
public int Sum(params int[] numbers)
{
    int total = 0;
    foreach (int num in numbers)
        total += num;
    return total;
}
Sum(1, 2, 3);        // 6
Sum(1, 2, 3, 4, 5);  // 15

// Local Functions (C# 7.0+)
public int Multiply(int a, int b)
{
    int LocalAdd(int x, int y) => x + y;
    return LocalAdd(a, b) * 2;
}

// Expression-Bodied Methods (C# 6.0+)
public int Subtract(int a, int b) => a - b;

// Tuple Return (C# 7.0+)
public (int sum, int product) Calculate(int a, int b)
{
    return (a + b, a * b);
}
var (sum, product) = Calculate(5, 3);  // sum=8, product=15

// Method Overloading
public void Print(int value) => Console.WriteLine($"Int: {value}");
public void Print(string value) => Console.WriteLine($"String: {value}");
public void Print(double value) => Console.WriteLine($"Double: {value}");

Print(42);           // Calls Print(int)
Print("Hello");      // Calls Print(string)
Print(3.14);         // Calls Print(double)
```

### **2.5 String Operations**

```csharp
string text = "  Hello, World!  ";

// String Properties
int length = text.Length;              // 17 (includes spaces)
char firstChar = text[0];              // ' '

// String Methods
string trimmed = text.Trim();          // "Hello, World!"
string lower = text.ToLower();
string upper = text.ToUpper();
bool contains = text.Contains("World");         // true
bool startsWith = text.StartsWith("  Hello");   // true
bool endsWith = text.EndsWith("!");             // true

int indexOf = text.IndexOf("World");    // 9
string substring = text.Substring(10, 5);  // "World"
string replaced = text.Replace("World", "C#");
string[] parts = text.Split(',');

// String Concatenation
string firstName = "John";
string lastName = "Doe";
string fullName = firstName + " " + lastName;

// String Interpolation (C# 6.0+)
string age = "30";
string message = $"{firstName} {lastName} is {age} years old";

// Verbatim String
string path = @"C:\Users\John\Documents";
string multiLine = @"Line 1
Line 2
Line 3";

// Raw String Literals (C# 11+)
string json = """
{
    "name": "John",
    "age": 30
}
""";

// String Builder (for performance with many concatenations)
var sb = new StringBuilder();
for (int i = 0; i < 1000; i++)
    sb.Append($"Item {i}, ");
string result = sb.ToString();
```

### **2.6 Arrays & Collections**

```csharp
// Single-Dimensional Array
int[] numbers = new int[5];           // Array of size 5
int[] initialized = { 1, 2, 3, 4, 5 };
int[] shorthand = new[] { 1, 2, 3 };

numbers[0] = 10;
Console.WriteLine(numbers[0]);  // 10

// Multi-Dimensional Array
int[,] matrix = new int[3, 3];
matrix[0, 0] = 1;

int[,] matrixInit = 
{
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};

// Jagged Array
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[3];
jagged[2] = new int[1];

// List (Dynamic Array)
List<int> list = new();
list.Add(1);
list.Add(2);
list.Add(3);

for (int i = 0; i < list.Count; i++)
    Console.WriteLine(list[i]);

list.RemoveAt(0);
list.Insert(0, 10);
bool contains = list.Contains(2);

// Dictionary (Key-Value Pairs)
Dictionary<string, int> ages = new()
{
    { "Alice", 30 },
    { "Bob", 25 },
    { "Charlie", 35 }
};

ages["Alice"] = 31;  // Update
int age = ages["Alice"];

if (ages.TryGetValue("Alice", out int aliceAge))
    Console.WriteLine(aliceAge);  // 31

// HashSet (Unique Values)
HashSet<int> unique = new() { 1, 2, 3, 2, 1 };
// Contains: 1, 2, 3 (duplicates removed)

// Queue (FIFO)
Queue<string> queue = new();
queue.Enqueue("First");
queue.Enqueue("Second");
string first = queue.Dequeue();  // "First"

// Stack (LIFO)
Stack<string> stack = new();
stack.Push("First");
stack.Push("Second");
string top = stack.Pop();  // "Second"

// Tuple
(string, int) person = ("John", 30);
Console.WriteLine($"{person.Item1} is {person.Item2}");

// Named Tuple
(string name, int age) namedPerson = ("Jane", 28);
Console.WriteLine($"{namedPerson.name} is {namedPerson.age}");
```

---

## **3. Object-Oriented Programming (OOP)** {#oop}

### **3.1 Classes & Objects**

```csharp
// Basic Class
public class Person
{
    // Properties
    public string Name { get; set; }
    public int Age { get; set; }
    
    // Auto-Implemented Properties
    public string Email { get; set; }
    
    // Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
    
    // Constructor Chaining
    public Person(string name) : this(name, 0) { }
    
    // Method
    public void DisplayInfo()
    {
        Console.WriteLine($"{Name} is {Age} years old");
    }
}

// Creating Objects
Person person1 = new Person("John", 30);
Person person2 = new("Jane", 28);  // C# 9.0+ target-typed new
person1.DisplayInfo();  // John is 30 years old

// Properties with Backing Fields
public class Student
{
    private int age;
    
    public int Age
    {
        get => age;
        set => age = value > 0 ? value : 0;
    }
}

// Init-Only Properties (C# 9.0+)
public class Employee
{
    public string Name { get; init; }
    public int EmployeeId { get; init; }
    
    // Can be set during initialization, but not later
}
var emp = new Employee { Name = "Alice", EmployeeId = 001 };
// emp.Name = "Bob";  // Error: init-only property

// Primary Constructor (C# 12+)
public class Product(string name, decimal price)
{
    public string Name => name;
    public decimal Price => price;
}

// Usage
var product = new Product("Laptop", 999.99m);
```

### **3.2 Inheritance**

```csharp
// Base Class
public class Animal
{
    public string Name { get; set; }
    
    public virtual void MakeSound()
    {
        Console.WriteLine("Some sound");
    }
}

// Derived Class
public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}

// Usage
Animal dog = new Dog { Name = "Buddy" };
dog.MakeSound();  // Woof!

Animal cat = new Cat { Name = "Whiskers" };
cat.MakeSound();  // Meow!

// Sealed Classes (Cannot be inherited)
public sealed class FinalClass
{
    // Cannot create a derived class
}
```

### **3.3 Encapsulation**

```csharp
public class BankAccount
{
    private decimal balance;  // Private field
    
    public decimal Balance    // Public property
    {
        get => balance;
        private set => balance = value;  // Only accessible within class
    }
    
    public void Deposit(decimal amount)
    {
        if (amount > 0)
            Balance += amount;
    }
    
    public bool Withdraw(decimal amount)
    {
        if (amount > 0 && amount <= Balance)
        {
            Balance -= amount;
            return true;
        }
        return false;
    }
}

// Usage
var account = new BankAccount();
account.Deposit(1000);
Console.WriteLine(account.Balance);  // 1000
account.Withdraw(300);
Console.WriteLine(account.Balance);  // 700
// account.balance = 5000;  // Error: balance is private
```

### **3.4 Polymorphism**

```csharp
// Interface (Contract)
public interface IShape
{
    double GetArea();
    double GetPerimeter();
}

// Implementing Interface
public class Circle : IShape
{
    private readonly double radius;
    
    public Circle(double radius)
    {
        this.radius = radius;
    }
    
    public double GetArea()
    {
        return Math.PI * radius * radius;
    }
    
    public double GetPerimeter()
    {
        return 2 * Math.PI * radius;
    }
}

public class Rectangle : IShape
{
    private readonly double width, height;
    
    public Rectangle(double width, double height)
    {
        this.width = width;
        this.height = height;
    }
    
    public double GetArea()
    {
        return width * height;
    }
    
    public double GetPerimeter()
    {
        return 2 * (width + height);
    }
}

// Usage
IShape circle = new Circle(5);
IShape rectangle = new Rectangle(4, 6);

Console.WriteLine(circle.GetArea());      // 78.5398...
Console.WriteLine(rectangle.GetArea());   // 24

// Abstract Class
public abstract class Vehicle
{
    public abstract void Start();
    public abstract void Stop();
    
    public void Honk()
    {
        Console.WriteLine("Beep beep!");
    }
}

public class Car : Vehicle
{
    public override void Start()
    {
        Console.WriteLine("Car engine starting...");
    }
    
    public override void Stop()
    {
        Console.WriteLine("Car stopped.");
    }
}

// Usage
Vehicle car = new Car();
car.Start();   // Car engine starting...
car.Honk();    // Beep beep!
car.Stop();    // Car stopped.
```

### **3.5 Static Members**

```csharp
public class MathHelper
{
    // Static Field
    public static int CalculationCount = 0;
    
    // Static Property
    public static int Version { get; } = 1;
    
    // Static Method
    public static int Add(int a, int b)
    {
        CalculationCount++;
        return a + b;
    }
    
    // Static Constructor (runs once before first use)
    static MathHelper()
    {
        Console.WriteLine("MathHelper initialized");
    }
}

// Usage
int result = MathHelper.Add(5, 3);  // MathHelper initialized
Console.WriteLine(MathHelper.CalculationCount);  // 1
Console.WriteLine(MathHelper.Version);  // 1

// Static Class (Cannot be instantiated)
public static class StringExtensions
{
    public static int CountWords(this string text)
    {
        return text.Split(new[] { ' ' }, StringSplitOptions.RemoveEmptyEntries).Length;
    }
}

string sentence = "Hello World from C#";
Console.WriteLine(sentence.CountWords());  // 4
```

### **3.6 Composition & Aggregation**

```csharp
// Composition (Strong "has-a" relationship)
public class Engine
{
    public string Type { get; set; }
    public int Horsepower { get; set; }
}

public class Car
{
    private Engine engine;  // Car "has" an Engine
    
    public Car()
    {
        engine = new Engine();  // Engine created with Car
    }
    
    public void Start()
    {
        Console.WriteLine($"Car with {engine.Type} engine starting...");
    }
}

// Aggregation (Weak "has-a" relationship)
public class Department
{
    public string Name { get; set; }
    public List<Employee> Employees { get; set; }
    
    public Department()
    {
        Employees = new List<Employee>();
    }
}

public class Employee
{
    public string Name { get; set; }
    public Department Department { get; set; }  // Employee "knows" Department
}

// Usage
var employees = new List<Employee>
{
    new() { Name = "Alice" },
    new() { Name = "Bob" }
};

var dept = new Department { Name = "IT", Employees = employees };
```

---

## **4. Advanced C# Features** {#advanced}

### **4.1 Generics**

```csharp
// Generic Class
public class Stack<T>
{
    private List<T> items = new();
    
    public void Push(T item)
    {
        items.Add(item);
    }
    
    public T Pop()
    {
        if (items.Count == 0)
            throw new InvalidOperationException("Stack is empty");
        
        int index = items.Count - 1;
        T item = items[index];
        items.RemoveAt(index);
        return item;
    }
    
    public int Count => items.Count;
}

// Usage
Stack<int> intStack = new();
intStack.Push(1);
intStack.Push(2);
int value = intStack.Pop();  // 2

Stack<string> stringStack = new();
stringStack.Push("Hello");
stringStack.Push("World");

// Generic Method
public T GetFirst<T>(List<T> items)
{
    return items.Count > 0 ? items[0] : throw new InvalidOperationException();
}

var numbers = new List<int> { 1, 2, 3 };
int first = GetFirst(numbers);  // 1

// Generic Constraints
public class Repository<T> where T : class, new()
{
    public T Create()
    {
        return new T();  // T must be a class and have parameterless constructor
    }
}

// Multiple Constraints
public class Processor<T> where T : IComparable<T>, new()
{
    public void Process(List<T> items)
    {
        // items.Sort();  // Can use IComparable methods
    }
}

// Base Class Constraint
public interface IEntity
{
    int Id { get; set; }
}

public class DataAccess<T> where T : IEntity
{
    public void Save(T entity)
    {
        Console.WriteLine($"Saving entity with ID: {entity.Id}");
    }
}
```

### **4.2 Delegates & Events**

```csharp
// Delegate Declaration
public delegate void NotifyDelegate(string message);
public delegate int MathDelegate(int a, int b);

// Using Delegate
NotifyDelegate notify = Console.WriteLine;
notify("Hello from delegate");  // Hello from delegate

// Multicast Delegate
notify = null;
notify += Console.WriteLine;
notify += (msg) => Console.WriteLine($"[LOG] {msg}");
notify("System started");

// Event
public class Button
{
    // Event Declaration
    public event EventHandler OnClick;
    
    public void Click()
    {
        OnClick?.Invoke(this, EventArgs.Empty);
    }
}

// Event Handler
Button button = new();
button.OnClick += (sender, e) => Console.WriteLine("Button clicked!");
button.OnClick += (sender, e) => Console.WriteLine("Another handler");
button.Click();

// Custom Event Args
public class ButtonClickedEventArgs : EventArgs
{
    public DateTime ClickTime { get; set; }
}

public class AdvancedButton
{
    public event EventHandler<ButtonClickedEventArgs> OnClick;
    
    public void Click()
    {
        OnClick?.Invoke(this, new ButtonClickedEventArgs { ClickTime = DateTime.Now });
    }
}

// Using Custom Event
var advButton = new AdvancedButton();
advButton.OnClick += (sender, e) => 
    Console.WriteLine($"Clicked at {e.ClickTime}");
advButton.Click();

// Func and Action Delegates
Func<int, int, int> add = (a, b) => a + b;
int result = add(5, 3);  // 8

Action<string> print = (msg) => Console.WriteLine(msg);
print("Hello");

Action<int> printNumber = n => Console.WriteLine($"Number: {n}");
printNumber(42);
```

### **4.3 Lambda Expressions**

```csharp
// Simple Lambda
Func<int, int> square = x => x * x;
Console.WriteLine(square(5));  // 25

// Lambda with Multiple Parameters
Func<int, int, int> multiply = (a, b) => a * b;
Console.WriteLine(multiply(4, 5));  // 20

// Lambda with Block Body
Func<int, int, bool> isGreater = (a, b) =>
{
    bool result = a > b;
    return result;
};

// Lambda with LINQ
List<int> numbers = new() { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();  // [2, 4]
var squared = numbers.Select(n => n * n).ToList();           // [1, 4, 9, 16, 25]

// Discard (C# 7.0+)
Func<int, int, int> getFirst = (a, _) => a;  // Ignore second parameter
int first = getFirst(10, 20);  // 10
```

### **4.4 Anonymous Methods & Local Functions**

```csharp
// Anonymous Method (C# 2.0+)
Func<int, int> square1 = delegate(int x)
{
    return x * x;
};

// Local Function (C# 7.0+)
int Calculate()
{
    int AddNumbers(int a, int b) => a + b;
    int MultiplyNumbers(int a, int b) => a * b;
    
    return AddNumbers(5, 3) + MultiplyNumbers(2, 3);
}

// Usage
Console.WriteLine(Calculate());  // 19

// Local Function with Closure
int multiplier = 5;
int Multiply(int x)
{
    return x * multiplier;
}

Console.WriteLine(Multiply(10));  // 50
```

### **4.5 Attributes**

```csharp
// Built-in Attributes
[Obsolete("Use NewMethod instead")]
public void OldMethod()
{
    Console.WriteLine("Old method");
}

public void NewMethod()
{
    Console.WriteLine("New method");
}

// Custom Attribute
[AttributeUsage(AttributeTargets.Method)]
public class LogMethodAttribute : Attribute
{
    public string Name { get; set; }
    
    public LogMethodAttribute(string name)
    {
        Name = name;
    }
}

// Using Custom Attribute
[LogMethod("GetUser")]
public User GetUser(int id)
{
    return new User { Id = id, Name = "John" };
}

// Reflection to Read Attributes
var method = typeof(Program).GetMethod("GetUser");
var attr = method.GetCustomAttribute<LogMethodAttribute>();
if (attr != null)
    Console.WriteLine($"Method: {attr.Name}");

// Conditional Compilation
#if DEBUG
    Console.WriteLine("Debug mode");
#else
    Console.WriteLine("Release mode");
#endif
```

### **4.6 Reflection**

```csharp
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
    
    public void Greet()
    {
        Console.WriteLine($"Hello, I'm {Name}");
    }
}

// Get Type Information
Type personType = typeof(Person);

// Get Properties
PropertyInfo[] properties = personType.GetProperties();
foreach (PropertyInfo prop in properties)
{
    Console.WriteLine($"Property: {prop.Name}, Type: {prop.PropertyType}");
}

// Get Methods
MethodInfo[] methods = personType.GetMethods();
foreach (MethodInfo method in methods)
{
    Console.WriteLine($"Method: {method.Name}");
}

// Create Instance Dynamically
object person = Activator.CreateInstance(personType);

// Set Property Value
PropertyInfo nameProp = personType.GetProperty("Name");
nameProp?.SetValue(person, "Alice");

// Get Property Value
object nameValue = nameProp?.GetValue(person);
Console.WriteLine(nameValue);  // Alice

// Invoke Method
MethodInfo greetMethod = personType.GetMethod("Greet");
greetMethod?.Invoke(person, null);  // Hello, I'm Alice
```

### **4.7 Exception Handling**

```csharp
// Try-Catch-Finally
try
{
    int result = int.Parse("not a number");
}
catch (FormatException ex)
{
    Console.WriteLine($"Format error: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"General error: {ex.Message}");
}
finally
{
    Console.WriteLine("Cleanup code here");
}

// Exception Filter (C# 6.0+)
try
{
    int[] numbers = { 1, 2, 3 };
    int value = numbers[10];
}
catch (IndexOutOfRangeException ex) when (ex.Message.Contains("range"))
{
    Console.WriteLine("Index out of range");
}

// Custom Exception
public class InvalidAgeException : Exception
{
    public InvalidAgeException(string message) : base(message) { }
}

public void SetAge(int age)
{
    if (age < 0 || age > 150)
        throw new InvalidAgeException("Age must be between 0 and 150");
}

// Throw Expression (C# 7.0+)
public int GetAge(int? age) => age ?? throw new ArgumentNullException(nameof(age));
```

---

## **5. .NET Framework & .NET Core** {#dotnet-framework}

### **5.1 .NET Overview**

```
┌─────────────────────────────────────┐
│         .NET 9 (Current)            │
│  - Unified platform                 │
│  - Cross-platform                   │
│  - High performance                 │
│  - Cloud-native support             │
└─────────────────────────────────────┘
         ↓
┌────────────────────────────────��────┐
│    .NET 8 (LTS - Recommended)       │
│  - Support until Nov 2026           │
│  - Production-ready                 │
│  - Performance optimizations        │
│  - LINQ improvements                │
└─────────────────────────────────────┘
         ↓
┌─────────────────────────────────────┐
│      .NET Framework (Legacy)        │
│  - Windows only                     │
│  - Not recommended for new projects │
│  - Maintenance mode                 │
└─────────────────────────────────────┘
```

### **5.2 Project Types in .NET**

```bash
# Create Different Project Types

# Console Application
dotnet new console -n MyConsoleApp

# Class Library
dotnet new classlib -n MyLibrary

# ASP.NET Core Web API
dotnet new webapi -n MyApi

# ASP.NET Core MVC
dotnet new mvc -n MyMvcApp

# Windows Forms (Windows only)
dotnet new winforms -n MyWinFormsApp

# WPF (Windows only)
dotnet new wpf -n MyWpfApp

# Blazor WebAssembly
dotnet new blazorwasm -n MyBlazorApp

# Blazor Server
dotnet new blazorserver -n MyBlazorServerApp
```

### **5.3 Project File (.csproj)**

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net9.0</TargetFramework>
    <LangVersion>latest</LangVersion>
    <Nullable>enable</Nullable>
  </PropertyGroup>

  <ItemGroup>
    <!-- NuGet Package References -->
    <PackageReference Include="Newtonsoft.Json" Version="13.0.3" />
  </ItemGroup>

</Project>
```

### **5.4 NuGet Package Management**

```bash
# Search and install packages
dotnet add package Serilog
dotnet add package EntityFrameworkCore
dotnet add package Newtonsoft.Json

# List installed packages
dotnet list package

# Update package
dotnet add package Serilog --version 4.0.0

# Remove package
dotnet remove package Newtonsoft.Json

# Local package cache
dotnet nuget add source C:\packages --name local
```

---

## **6. LINQ & Collections** {#linq}

### **6.1 LINQ Basics**

```csharp
List<int> numbers = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Query Syntax
var evenQuery = from n in numbers
                where n % 2 == 0
                select n;

// Method Syntax
var evenMethod = numbers.Where(n => n % 2 == 0);

// Both produce: [2, 4, 6, 8, 10]

// Multiple Conditions
var filtered = numbers
    .Where(n => n > 3)
    .Where(n => n < 9);
// Result: [4, 5, 6, 7, 8]

// Select (Transform)
var doubled = numbers.Select(n => n * 2);
// Result: [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

// SelectMany (Flatten)
List<List<int>> lists = new()
{
    new() { 1, 2 },
    new() { 3, 4 },
    new() { 5, 6 }
};
var flattened = lists.SelectMany(l => l);
// Result: [1, 2, 3, 4, 5, 6]

// Skip & Take
var page = numbers.Skip(5).Take(3);
// Result: [6, 7, 8]

// FirstOrDefault & LastOrDefault
int first = numbers.First();          // 1
int firstEven = numbers.First(n => n % 2 == 0);  // 2
int firstOrDefault = numbers.FirstOrDefault(n => n > 100);  // 0 (default for int)

int last = numbers.Last();            // 10
int lastOrDefault = numbers.LastOrDefault(n => n > 100, -1);

// Single & SingleOrDefault
int single = numbers.Single(n => n == 5);  // 5
// Throws if not exactly one match

// Distinct
var duplicates = new[] { 1, 1, 2, 2, 3, 3 };
var unique = duplicates.Distinct();
// Result: [1, 2, 3]

// Count & Sum
int count = numbers.Count();
int countEven = numbers.Count(n => n % 2 == 0);  // 5
int sum = numbers.Sum();                         // 55
int sumEven = numbers.Where(n => n % 2 == 0).Sum();  // 30

// Average, Min, Max
double average = numbers.Average();
int min = numbers.Min();
int max = numbers.Max();

// Any & All
bool hasEven = numbers.Any(n => n % 2 == 0);  // true
bool allPositive = numbers.All(n => n > 0);   // true
```

### **6.2 LINQ Joins**

```csharp
class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
}

class Order
{
    public int Id { get; set; }
    public int CustomerId { get; set; }
    public decimal Amount { get; set; }
}

var customers = new List<Customer>
{
    new() { Id = 1, Name = "Alice" },
    new() { Id = 2, Name = "Bob" }
};

var orders = new List<Order>
{
    new() { Id = 1, CustomerId = 1, Amount = 100 },
    new() { Id = 2, CustomerId = 1, Amount = 200 },
    new() { Id = 3, CustomerId = 2, Amount = 150 }
};

// Inner Join
var innerJoin = from c in customers
                join o in orders on c.Id equals o.CustomerId
                select new
                {
                    CustomerName = c.Name,
                    OrderAmount = o.Amount
                };

// Left Join (with DefaultIfEmpty)
var leftJoin = from c in customers
               join o in orders on c.Id equals o.CustomerId
                   into orderGroup
               from order in orderGroup.DefaultIfEmpty()
               select new
               {
                   CustomerName = c.Name,
                   OrderAmount = order?.Amount ?? 0
               };

// Group Join
var grouped = from c in customers
              join o in orders on c.Id equals o.CustomerId
                  into customerOrders
              select new
              {
                  Customer = c.Name,
                  Orders = customerOrders.ToList()
              };
```

### **6.3 Grouping**

```csharp
List<int> numbers = new() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Group by Condition
var grouped = from n in numbers
              group n by n % 2 == 0 ? "Even" : "Odd";

foreach (var group in grouped)
{
    Console.WriteLine($"{group.Key}: {string.Join(", ", group)}");
}
// Output:
// Odd: 1, 3, 5, 7, 9
// Even: 2, 4, 6, 8, 10

// Group by Property
class Product
{
    public string Name { get; set; }
    public string Category { get; set; }
    public decimal Price { get; set; }
}

var products = new List<Product>
{
    new() { Name = "Laptop", Category = "Electronics", Price = 999 },
    new() { Name = "Mouse", Category = "Electronics", Price = 29 },
    new() { Name = "Book", Category = "Books", Price = 15 }
};

var byCategory = from p in products
                 group p by p.Category
                 into categoryGroup
                 select new
                 {
                     Category = categoryGroup.Key,
                     Products = categoryGroup.ToList(),
                     TotalPrice = categoryGroup.Sum(p => p.Price)
                 };
```

### **6.4 Ordering**

```csharp
List<string> names = new() { "Charlie", "Alice", "Bob", "David" };

// Ascending
var ascending = names.OrderBy(n => n);
// [Alice, Bob, Charlie, David]

// Descending
var descending = names.OrderByDescending(n => n);
// [David, Charlie, Bob, Alice]

// Multiple Levels
var people = new List<(string Name, int Age)>
{
    ("Alice", 30),
    ("Bob", 25),
    ("Alice", 25)
};

var sorted = people
    .OrderBy(p => p.Name)
    .ThenBy(p => p.Age);
// [Alice 25, Alice 30, Bob 25]

// Reverse
var reversed = names.Reverse();
// [David, Bob, Charlie, Alice]
```

### **6.5 Set Operations**

```csharp
List<int> set1 = new() { 1, 2, 3, 4, 5 };
List<int> set2 = new() { 4, 5, 6, 7, 8 };

// Union (Combines without duplicates)
var union = set1.Union(set2);
// [1, 2, 3, 4, 5, 6, 7, 8]

// Intersect (Common elements)
var intersect = set1.Intersect(set2);
// [4, 5]

// Except (In first but not second)
var except = set1.Except(set2);
// [1, 2, 3]

// Concat (All elements from both)
var concat = set1.Concat(set2);
// [1, 2, 3, 4, 5, 4, 5, 6, 7, 8]
```

### **6.6 Aggregation**

```csharp
List<int> numbers = new() { 1, 2, 3, 4, 5 };

// Aggregate
int sum = numbers.Aggregate((acc, n) => acc + n);  // 15

// Aggregate with Seed
int product = numbers.Aggregate(1, (acc, n) => acc * n);  // 120

// Example: String Concatenation
var words = new[] { "Hello", "World", "from", "C#" };
string sentence = words.Aggregate((acc, word) => acc + " " + word);
// "Hello World from C#"

// Fold (Left to Right)
int fold = numbers.Aggregate(0, (acc, n) => acc + n * 2);  // 30
```

---

## **7. Async & Parallel Programming** {#async}

### **7.1 Async/Await**

```csharp
// Async Method (Returns Task or Task<T>)
public async Task<string> FetchDataAsync()
{
    // Simulate async operation
    await Task.Delay(2000);  // Wait 2 seconds
    return "Data fetched";
}

// Calling Async Method
async Task Main()
{
    string result = await FetchDataAsync();
    Console.WriteLine(result);  // Data fetched
}

// Multiple Async Calls (Sequential)
async Task Sequential()
{
    var result1 = await FetchDataAsync();  // 2 seconds
    var result2 = await FetchDataAsync();  // 2 seconds (total: 4)
    Console.WriteLine($"{result1}, {result2}");
}

// Parallel Async Calls
async Task Parallel()
{
    var task1 = FetchDataAsync();
    var task2 = FetchDataAsync();
    
    var results = await Task.WhenAll(task1, task2);  // ~2 seconds (not 4)
    Console.WriteLine("Both completed");
}

// Async Method with Return Value
public async Task<int> GetCountAsync()
{
    await Task.Delay(1000);
    return 42;
}

// Fire and Forget (Not recommended)
async void FireAndForget()
{
    await SomeAsyncMethod();  // Use Task, not void (except for event handlers)
}

// Try-Catch with Async
async Task HandleErrors()
{
    try
    {
        await Task.Delay(1000);
        throw new InvalidOperationException("Something went wrong");
    }
    catch (InvalidOperationException ex)
    {
        Console.WriteLine($"Error: {ex.Message}");
    }
}

// ConfigureAwait (for library code)
public async Task<string> LibraryMethodAsync()
{
    var result = await FetchDataAsync().ConfigureAwait(false);
    return result;
}
```

### **7.2 Task Parallel Library (TPL)**

```csharp
// Parallel.For
Parallel.For(0, 10, i =>
{
    Console.WriteLine($"Task {i} on thread {Thread.CurrentThread.ManagedThreadId}");
});

// Parallel.ForEach
var numbers = new[] { 1, 2, 3, 4, 5 };
Parallel.ForEach(numbers, number =>
{
    Console.WriteLine($"Processing {number}");
});

// Parallel.Invoke (Run multiple actions in parallel)
Parallel.Invoke(
    () => Console.WriteLine("Action 1"),
    () => Console.WriteLine("Action 2"),
    () => Console.WriteLine("Action 3")
);

// Task Parallel
Task task1 = Task.Run(() =>
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine("Task 1");
        Thread.Sleep(100);
    }
});

Task task2 = Task.Run(() =>
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine("Task 2");
        Thread.Sleep(100);
    }
});

Task.WaitAll(task1, task2);
Console.WriteLine("All tasks completed");

// Task Result (Blocking - use with caution)
Task<int> getNumber = Task.Run(() =>
{
    Thread.Sleep(1000);
    return 42;
});

int result = getNumber.Result;  // Blocks until complete
```

### **7.3 Cancellation Tokens**

```csharp
// CancellationToken
async Task DownloadWithCancellationAsync(CancellationToken token)
{
    for (int i = 0; i < 100; i++)
    {
        token.ThrowIfCancellationRequested();  // Check for cancellation
        
        await Task.Delay(100);
        Console.WriteLine($"Progress: {i}%");
    }
}

// Usage
var cts = new CancellationTokenSource();
cts.CancelAfter(TimeSpan.FromSeconds(2));  // Cancel after 2 seconds

try
{
    await DownloadWithCancellationAsync(cts.Token);
}
catch (OperationCanceledException)
{
    Console.WriteLine("Operation cancelled");
}
```

### **7.4 Thread & ThreadPool**

```csharp
// Thread
Thread thread = new Thread(() =>
{
    for (int i = 0; i < 5; i++)
    {
        Console.WriteLine($"Thread: {i}");
        Thread.Sleep(100);
    }
});

thread.Start();
thread.Join();  // Wait for thread to complete

// ThreadPool
ThreadPool.QueueUserWorkItem(state =>
{
    Console.WriteLine("ThreadPool work item");
    Thread.Sleep(1000);
});

Thread.Sleep(1500);  // Wait for work item

// Current Thread Info
Console.WriteLine($"Thread ID: {Thread.CurrentThread.ManagedThreadId}");
Console.WriteLine($"IsBackground: {Thread.CurrentThread.IsBackground}");
```

### **7.5 Async Patterns**

```csharp
// IAsyncEnumerable (C# 8.0+)
async IAsyncEnumerable<int> GenerateNumbersAsync()
{
    for (int i = 0; i < 5; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}

// Using IAsyncEnumerable
await foreach (var number in GenerateNumbersAsync())
{
    Console.WriteLine(number);
}

// Async LINQ (C# 8.0+)
var even = await GenerateNumbersAsync()
    .Where(n => n % 2 == 0)
    .ToListAsync();

// Custom Awaitable (C# 11+)
class CustomAwaitable
{
    public CustomAwaiter GetAwaiter() => new();
}

class CustomAwaiter : INotifyCompletion
{
    public bool IsCompleted => true;
    
    public void OnCompleted(Action continuation)
    {
        continuation?.Invoke();
    }
    
    public void GetResult() { }
}
```

---

## **8. Entity Framework Core** {#ef-core}

### **8.1 DbContext & Models**

```csharp
using Microsoft.EntityFrameworkCore;

// Define Models
public class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
    public DateTime CreatedAt { get; set; }
    
    // Navigation Property
    public virtual List<Post> Posts { get; set; }
}

public class Post
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public int UserId { get; set; }
    
    // Navigation Property
    public virtual User User { get; set; }
}

// DbContext
public class AppDbContext : DbContext
{
    public DbSet<User> Users { get; set; }
    public DbSet<Post> Posts { get; set; }
    
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        // Connection string can be hardcoded or from configuration
        optionsBuilder.UseSqlServer("Server=.;Database=MyApp;Trusted_Connection=true;Encrypt=false;");
    }
    
    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        base.OnModelCreating(modelBuilder);
        
        // Configure User
        modelBuilder.Entity<User>(entity =>
        {
            entity.HasKey(e => e.Id);
            entity.Property(e => e.Name).IsRequired().HasMaxLength(200);
            entity.Property(e => e.Email).IsRequired().HasMaxLength(100);
            
            // One-to-Many Relationship
            entity.HasMany(e => e.Posts)
                .WithOne(p => p.User)
                .HasForeignKey(p => p.UserId)
                .OnDelete(DeleteBehavior.Cascade);
        });
        
        // Configure Post
        modelBuilder.Entity<Post>(entity =>
        {
            entity.HasKey(e => e.Id);
            entity.Property(e => e.Title).IsRequired().HasMaxLength(500);
            entity.Property(e => e.Content).IsRequired();
        });
    }
}
```

### **8.2 CRUD Operations**

```csharp
using (var context = new AppDbContext())
{
    // CREATE
    var user = new User
    {
        Name = "John Doe",
        Email = "john@example.com",
        CreatedAt = DateTime.Now
    };
    context.Users.Add(user);
    await context.SaveChangesAsync();
    Console.WriteLine($"User created with ID: {user.Id}");
    
    // READ
    var existingUser = await context.Users.FirstOrDefaultAsync(u => u.Email == "john@example.com");
    Console.WriteLine($"Found: {existingUser?.Name}");
    
    // UPDATE
    if (existingUser != null)
    {
        existingUser.Name = "Jane Doe";
        await context.SaveChangesAsync();
    }
    
    // DELETE
    context.Users.Remove(existingUser);
    await context.SaveChangesAsync();
}
```

### **8.3 Relationships**

```csharp
// One-to-Many
public class Category
{
    public int Id { get; set; }
    public string Name { get; set; }
    public virtual List<Product> Products { get; set; }
}

public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int CategoryId { get; set; }
    public virtual Category Category { get; set; }
}

// Many-to-Many
public class Author
{
    public int Id { get; set; }
    public string Name { get; set; }
    public virtual List<Book> Books { get; set; }
}

public class Book
{
    public int Id { get; set; }
    public string Title { get; set; }
    public virtual List<Author> Authors { get; set; }
}

// Junction Table (automatic in EF Core 5.0+)
modelBuilder.Entity<Author>()
    .HasMany(a => a.Books)
    .WithMany(b => b.Authors)
    .UsingEntity(j => j.ToTable("BookAuthors"));

// One-to-One
public class User
{
    public int Id { get; set; }
    public virtual Profile Profile { get; set; }
}

public class Profile
{
    public int Id { get; set; }
    public int UserId { get; set; }
    public virtual User User { get; set; }
}

modelBuilder.Entity<User>()
    .HasOne(u => u.Profile)
    .WithOne(p => p.User)
    .HasForeignKey<Profile>(p => p.UserId);
```

### **8.4 Querying**

```csharp
using (var context = new AppDbContext())
{
    // Basic Query
    var users = await context.Users.ToListAsync();
    
    // Where
    var activeUsers = await context.Users
        .Where(u => u.CreatedAt > DateTime.Now.AddMonths(-1))
        .ToListAsync();
    
    // Select (Projection)
    var userNames = await context.Users
        .Select(u => new { u.Id, u.Name })
        .ToListAsync();
    
    // Include (Load Related Data)
    var usersWithPosts = await context.Users
        .Include(u => u.Posts)
        .ToListAsync();
    
    // Multiple Levels
    var usersWithPostsAndComments = await context.Users
        .Include(u => u.Posts)
            .ThenInclude(p => p.Comments)
        .ToListAsync();
    
    // OrderBy
    var sortedUsers = await context.Users
        .OrderBy(u => u.Name)
        .ThenByDescending(u => u.CreatedAt)
        .ToListAsync();
    
    // Pagination
    var pageSize = 10;
    var page = 1;
    var pagedUsers = await context.Users
        .Skip((page - 1) * pageSize)
        .Take(pageSize)
        .ToListAsync();
    
    // Grouping
    var groupedByMonth = await context.Users
        .GroupBy(u => u.CreatedAt.Month)
        .Select(g => new { Month = g.Key, Count = g.Count() })
        .ToListAsync();
    
    // Joins
    var userPostCount = await context.Users
        .Join(context.Posts,
            u => u.Id,
            p => p.UserId,
            (u, p) => new { u.Name, p.Title })
        .ToListAsync();
    
    // Count
    int totalUsers = await context.Users.CountAsync();
    int activeCount = await context.Users
        .Where(u => u.CreatedAt > DateTime.Now.AddMonths(-1))
        .CountAsync();
    
    // Any
    bool hasUsers = await context.Users.AnyAsync();
    bool hasNewUsers = await context.Users
        .AnyAsync(u => u.CreatedAt > DateTime.Now.AddDays(-1));
    
    // First / FirstOrDefault
    var firstUser = await context.Users.FirstOrDefaultAsync();
    var specificUser = await context.Users
        .FirstOrDefaultAsync(u => u.Email == "john@example.com");
}
```

### **8.5 Migrations**

```bash
# Create initial migration
dotnet ef migrations add InitialCreate

# Update database
dotnet ef database update

# List migrations
dotnet ef migrations list

# Revert to previous migration
dotnet ef database update PreviousMigrationName

# Remove last migration
dotnet ef migrations remove

# Create migration with custom code
dotnet ef migrations add AddUserTable
# Then edit the migration file with raw SQL if needed
```

### **8.6 Advanced Features**

```csharp
// Shadow Properties (Properties not in the model)
modelBuilder.Entity<User>()
    .Property<DateTime>("LastModified");

// Global Query Filters
modelBuilder.Entity<User>()
    .HasQueryFilter(u => !u.IsDeleted);

// Owned Types
public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}

public class Company
{
    public int Id { get; set; }
    public string Name { get; set; }
    public Address Address { get; set; }
}

modelBuilder.Entity<Company>()
    .OwnsOne(c => c.Address);

// Raw SQL
var users = await context.Users
    .FromSqlInterpolated($"SELECT * FROM Users WHERE Email = {email}")
    .ToListAsync();

// Transactions
using (var transaction = await context.Database.BeginTransactionAsync())
{
    try
    {
        context.Users.Add(newUser);
        await context.SaveChangesAsync();
        
        context.Posts.Add(newPost);
        await context.SaveChangesAsync();
        
        await transaction.CommitAsync();
    }
    catch (Exception)
    {
        await transaction.RollbackAsync();
        throw;
    }
}

// Change Tracking
var user = await context.Users.FindAsync(1);
user.Name = "New Name";

var entry = context.Entry(user);
Console.WriteLine(entry.State);  // EntityState.Modified

// Bulk Operations
context.Users.AddRange(usersList);
await context.SaveChangesAsync();

context.Users.RemoveRange(usersToDelete);
await context.SaveChangesAsync();
```

---

## **9. Modern C# Features (C# 11, 12)** {#modern-features}

### **9.1 C# 11 Features**

```csharp
// Required Properties (C# 11)
public class Person
{
    public required string Name { get; set; }
    public string? Phone { get; set; }
    
    public Person(string name)
    {
        Name = name;
    }
}

var person = new Person("John") { Phone = "123-456-7890" };
// new Person("John");  // Error: Name is required

// Raw String Literals (C# 11)
string json = """
{
    "name": "John",
    "age": 30
}
""";

string path = """
C:\Users\John\Documents
""";

// Generic Math (C# 11)
public static class MathHelper
{
    public static T Add<T>(T a, T b) where T : System.Numerics.IAdditionOperators<T, T, T>
    {
        return a + b;
    }
}

int result = MathHelper.Add(5, 3);           // 8
double resultD = MathHelper.Add(5.5, 3.2);  // 8.7

// File-Scoped Types (C# 11)
file class InternalHelper
{
    // Only visible within this file
}

// List Patterns (C# 11)
int[] numbers = { 1, 2, 3, 4, 5 };

if (numbers is [1, 2, ..])
    Console.WriteLine("Starts with 1, 2");

if (numbers is [.., 4, 5])
    Console.WriteLine("Ends with 4, 5");

if (numbers is [var first, .., var last])
    Console.WriteLine($"First: {first}, Last: {last}");

// Numeric IntPtr (C# 11)
nuint size = nuint.Max;
nint offset = nint.Min;

// Cached Anonymous Function (C# 11)
Func<int, int> square = x => x * x;  // Compiled once, reused
```

### **9.2 C# 12 Features**

```csharp
// Primary Constructors (C# 12)
public class User(string name, int age)
{
    public string Name => name;
    public int Age => age;
    
    public void Display()
    {
        Console.WriteLine($"{name} is {age}");
    }
}

var user = new User("John", 30);

// Collection Expressions (C# 12)
int[] array = [1, 2, 3];
List<int> list = [1, 2, 3];
HashSet<int> set = [1, 2, 3];

// Spread Operator in Collections (C# 12)
int[] array1 = [1, 2, 3];
int[] array2 = [4, 5, 6];
int[] combined = [..array1, ..array2];  // [1, 2, 3, 4, 5, 6]

// Default Lambda Parameters (C# 12)
var greet = (string name = "Guest") => $"Hello, {name}!";
Console.WriteLine(greet());       // Hello, Guest!
Console.WriteLine(greet("John")); // Hello, John!

// Alias Any Type (C# 12)
using StringDictionary = System.Collections.Generic.Dictionary<string, string>;

StringDictionary dict = new() { { "key", "value" } };

// Inline Arrays (C# 12)
[System.Runtime.CompilerServices.InlineArray(3)]
struct CharBuffer
{
    private char element0;
}

CharBuffer buffer = default;
buffer[0] = 'a';
buffer[1] = 'b';
buffer[2] = 'c';

// Optional Parameters in Lambda (C# 12)
Func<int, int, int> add = (a, b = 5) => a + b;
Console.WriteLine(add(10));    // 15
Console.WriteLine(add(10, 3)); // 13

// Interceptors (C# 12 Preview)
// Can intercept method calls and replace them
// (Advanced feature, mainly for tooling)

// Method Groups Improved (C# 12)
string[] words = ["apple", "banana", "cherry"];
var upperWords = words.Select(string.ToUpper);
// Simpler than: words.Select(w => w.ToUpper())
```

### **9.3 Nullable Reference Types**

```csharp
// Enable in .csproj: <Nullable>enable</Nullable>

// Non-nullable by default
string name = "John";      // OK
string? nullableName = null;  // OK with ?

// name = null;  // Error
nullableName = null;      // OK

// Property Nullability
public class Person
{
    public string Name { get; set; }           // Non-nullable (required)
    public string? Email { get; set; }         // Nullable
    public string Phone { get; set; } = "";    // Default value
}

// Null-coalescing assignment
string? value = null;
value ??= "default";  // value = "default"

// Null-conditional member access
Person? person = null;
string? email = person?.Email;  // email = null (no exception)

// Null-forgiving operator (!)
string? text = GetText();
int length = text!.Length;  // Suppresses warning (use carefully!)
```

### **9.4 Record Types**

```csharp
// Record Class (C# 9+)
public record Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

// With Expression (Immutable copies)
var person1 = new Person { Name = "John", Age = 30 };
var person2 = person1 with { Name = "Jane" };  // New instance

// Value Equality (compared by value, not reference)
var p1 = new Person { Name = "John", Age = 30 };
var p2 = new Person { Name = "John", Age = 30 };
Console.WriteLine(p1 == p2);  // true (not same reference)

// Positional Records (C# 9+)
public record User(string Name, int Age, string Email);

var user = new User("John", 30, "john@example.com");
var (name, age, email) = user;  // Deconstruction

// Record Struct (C# 10+)
public record struct Point
{
    public int X { get; set; }
    public int Y { get; set; }
}

// Init-Only Properties
public record Company
{
    public required string Name { get; init; }
    public string? Address { get; init; }
}

var company = new Company { Name = "Acme Corp", Address = "123 Main St" };
// company.Name = "New Name";  // Error: init-only
```

### **9.5 Pattern Matching**

```csharp
// Type Pattern
object obj = "Hello";
if (obj is string str)
{
    Console.WriteLine(str.Length);
}

// Property Pattern (C# 8+)
public class Person { public string Name { get; set; } }

if (person is { Name: "John" })
{
    Console.WriteLine("Found John");
}

// List Pattern (C# 11+)
int[] numbers = { 1, 2, 3, 4, 5 };

if (numbers is [1, 2, ..])
    Console.WriteLine("Starts with 1, 2");

if (numbers is [.., 4, 5])
    Console.WriteLine("Ends with 4, 5");

// Relational Pattern (C# 9+)
int age = 25;
string category = age switch
{
    < 18 => "Minor",
    >= 18 and < 65 => "Adult",
    >= 65 => "Senior"
};

// Logical Pattern (C# 9+)
if (age >= 18 and age < 65)
{
    Console.WriteLine("Working age");
}

// Not Pattern (C# 9+)
if (value is not null)
{
    Console.WriteLine("Value is not null");
}

// Combined Pattern
var result = (age, isMember) switch
{
    (>= 65, true) => "Senior Member",
    (>= 65, false) => "Senior Non-Member",
    (< 18, true) => "Youth Member",
    (< 18, false) => "Youth Non-Member",
    _ => "Regular Member"
};
```

---

## **10. Best Practices & Patterns** {#best-practices}

### **10.1 Naming Conventions**

```csharp
// Classes, Properties, Methods, Events: PascalCase
public class UserAccount { }
public string FirstName { get; set; }
public void ProcessPayment() { }
public event EventHandler DataReceived;

// Local variables, parameters: camelCase
int userId = 123;
void ProcessData(string userName) { }

// Private/Protected fields: _camelCase or camelCase
private string _privateField;
protected List<string> _protectedList;

// Constants: UPPER_CASE or PascalCase
private const int MAX_ATTEMPTS = 3;
private const string ConnectionString = "...";

// Interfaces: IPascalCase
public interface IUserRepository { }
public interface IPaymentProcessor { }

// Abbreviations in names
public class HttpClient { }  // HTTP, not HTTP
public class XmlParser { }   // XML, not XML
```

### **10.2 Code Organization**

```csharp
public class UserService
{
    // 1. Private fields
    private readonly IUserRepository _repository;
    private readonly ILogger<UserService> _logger;
    
    // 2. Public properties
    public bool IsInitialized { get; private set; }
    
    // 3. Constructor
    public UserService(IUserRepository repository, ILogger<UserService> logger)
    {
        _repository = repository;
        _logger = logger;
    }
    
    // 4. Public methods
    public async Task<User> GetUserAsync(int id)
    {
        try
        {
            return await _repository.GetByIdAsync(id);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error getting user");
            throw;
        }
    }
    
    // 5. Private methods
    private void ValidateUser(User user)
    {
        if (user == null)
            throw new ArgumentNullException(nameof(user));
    }
    
    // 6. IDisposable (if needed)
    public void Dispose()
    {
        _repository?.Dispose();
    }
}
```

### **10.3 Error Handling**

```csharp
// Specific Exception Handling
try
{
    var result = int.Parse(userInput);
}
catch (ArgumentException ex)
{
    Console.WriteLine("Argument error: " + ex.Message);
}
catch (FormatException ex)
{
    Console.WriteLine("Format error: " + ex.Message);
}
catch (OverflowException ex)
{
    Console.WriteLine("Overflow error: " + ex.Message);
}
catch (Exception ex)
{
    Console.WriteLine("Unexpected error: " + ex.Message);
}

// Custom Exception
public class InvalidUserException : Exception
{
    public int UserId { get; }
    
    public InvalidUserException(int userId, string message)
        : base(message)
    {
        UserId = userId;
    }
}

// Throwing with Context
try
{
    await _repository.SaveAsync(user);
}
catch (Exception ex)
{
    throw new InvalidUserException(user.Id, "Failed to save user", ex);
}

// Using Pattern (Automatic disposal)
using (var reader = new StreamReader(filePath))
{
    string content = await reader.ReadToEndAsync();
}

// Using Declaration (C# 8+)
using FileStream fs = new(filePath, FileMode.Open);
var content = fs.ReadByte();
```

### **10.4 Performance Tips**

```csharp
// 1. Use StringBuilder for many concatenations
var sb = new StringBuilder();
for (int i = 0; i < 1000; i++)
{
    sb.Append($"Item {i}, ");
}
string result = sb.ToString();

// 2. Use object pooling
ArrayPool<byte> pool = ArrayPool<byte>.Shared;
byte[] buffer = pool.Rent(1024);
try
{
    // Use buffer
}
finally
{
    pool.Return(buffer);
}

// 3. Cache expensive operations
private Dictionary<int, UserData> _cache = new();

public UserData GetUser(int id)
{
    if (_cache.TryGetValue(id, out var user))
        return user;
    
    var userData = FetchFromDatabase(id);
    _cache[id] = userData;
    return userData;
}

// 4. Avoid LINQ for large collections
// Bad
var result = _collection.Where(x => x.IsActive).ToList();

// Better
List<Item> result = new(capacity: _collection.Count);
foreach (var item in _collection)
{
    if (item.IsActive)
        result.Add(item);
}

// 5. Use ValueTask for potentially synchronous operations
public ValueTask<int> GetCountAsync()
{
    if (_cachedCount.HasValue)
        return new ValueTask<int>(_cachedCount.Value);
    
    return new ValueTask<int>(FetchCountAsync());
}

private async Task<int> FetchCountAsync()
{
    return await _repository.CountAsync();
}

// 6. Avoid boxing with generics
// Bad
object value = 42;  // Boxing

// Good
T value = GetGenericValue<int>();
```

### **10.5 Security Best Practices**

```csharp
// 1. Never hardcode sensitive data
// Bad
private const string ApiKey = "sk-1234567890";

// Good
private readonly string _apiKey = _configuration["ApiKeys:Service"];

// 2. Use proper authentication/authorization
[Authorize]
[HttpGet("secure")]
public IActionResult GetSecureData()
{
    return Ok("Secure data");
}

[Authorize(Roles = "Admin")]
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    return NoContent();
}

// 3. Input validation
public void CreateUser(string name, int age)
{
    if (string.IsNullOrWhiteSpace(name))
        throw new ArgumentException("Name cannot be empty");
    
    if (age < 0 || age > 150)
        throw new ArgumentException("Age must be between 0 and 150");
}

// 4. SQL Injection Prevention
// Bad
string query = $"SELECT * FROM Users WHERE Email = '{email}'";

// Good
var user = await context.Users
    .FirstOrDefaultAsync(u => u.Email == email);

// Or with parameters
using (var cmd = new SqlCommand("SELECT * FROM Users WHERE Email = @email", conn))
{
    cmd.Parameters.AddWithValue("@email", email);
}

// 5. Sensitive Data in Logs
private readonly ILogger<UserService> _logger;

public void ProcessUserData(string ssn)
{
    // Bad
    _logger.LogInformation($"Processing SSN: {ssn}");
    
    // Good
    _logger.LogInformation("Processing user data");
}

// 6. Cross-Site Scripting (XSS) Prevention
// In ASP.NET Core, use @Html.Encode() or @Html.Raw() carefully
@Html.Encode(Model.UserInput)  // Safe

// 7. CSRF Protection
// ASP.NET Core MVC includes automatic CSRF protection
```

### **10.6 Testing**

```csharp
// Unit Testing with xUnit
[Fact]
public void Add_WhenCalledWithTwoNumbers_ReturnsSum()
{
    // Arrange
    var calculator = new Calculator();
    
    // Act
    int result = calculator.Add(2, 3);
    
    // Assert
    Assert.Equal(5, result);
}

// Parametrized Test
[Theory]
[InlineData(2, 3, 5)]
[InlineData(-1, 1, 0)]
[InlineData(0, 0, 0)]
public void Add_WithVariousInputs_ReturnsCorrectSum(int a, int b, int expected)
{
    var calculator = new Calculator();
    Assert.Equal(expected, calculator.Add(a, b));
}

// Mocking with Moq
[Fact]
public async Task GetUser_WhenUserExists_ReturnsUser()
{
    // Arrange
    var mockRepository = new Mock<IUserRepository>();
    mockRepository
        .Setup(r => r.GetByIdAsync(1))
        .ReturnsAsync(new User { Id = 1, Name = "John" });
    
    var service = new UserService(mockRepository.Object);
    
    // Act
    var user = await service.GetUserAsync(1);
    
    // Assert
    Assert.NotNull(user);
    Assert.Equal("John", user.Name);
    mockRepository.Verify(r => r.GetByIdAsync(1), Times.Once);
}

// Exception Testing
[Fact]
public void Divide_WhenDivisorIsZero_ThrowsException()
{
    var calculator = new Calculator();
    
    Assert.Throws<DivideByZeroException>(() => calculator.Divide(10, 0));
}

// Async Testing
[Fact]
public async Task FetchData_ReturnsData()
{
    var service = new DataService();
    
    var result = await service.FetchDataAsync();
    
    Assert.NotEmpty(result);
}
```

### **10.7 Documentation**

```csharp
/// <summary>
/// Calculates the sum of two numbers.
/// </summary>
/// <param name="a">The first number</param>
/// <param name="b">The second number</param>
/// <returns>The sum of a and b</returns>
/// <exception cref="ArgumentException">Thrown when result would overflow</exception>
/// <example>
/// <code>
/// int result = Add(5, 3);  // returns 8
/// </code>
/// </example>
public int Add(int a, int b)
{
    return a + b;
}

/// <summary>
/// Gets a user by their ID.
/// </summary>
/// <param name="id">The user ID</param>
/// <returns>The user object if found; otherwise null</returns>
/// <remarks>
/// This method queries the database. For frequently accessed users,
/// consider caching the result.
/// </remarks>
public async Task<User> GetUserAsync(int id)
{
    return await _repository.GetByIdAsync(id);
}

/// <summary>
/// Represents a user in the system.
/// </summary>
/// <remarks>
/// This class is used to store user information. Email should be unique.
/// </remarks>
public class User
{
    /// <summary>Gets or sets the user's unique identifier.</summary>
    public int Id { get; set; }
    
    /// <summary>Gets or sets the user's full name.</summary>
    public string Name { get; set; }
}
```

---

## **Installation & Setup Guide**

### **Install .NET SDK**

```bash
# Download from https://dotnet.microsoft.com/download

# Verify Installation
dotnet --version
dotnet --info

# List installed SDKs
dotnet --list-sdks
dotnet --list-runtimes
```

### **First C# Program**

```bash
# Create new console project
dotnet new console -n MyFirstApp
cd MyFirstApp

# Run
dotnet run

# Build
dotnet build

# Publish
dotnet publish -c Release
```

### **Visual Studio Setup**

1. Download Visual Studio Community (free)
2. Install with C# workload
3. Create new project → Console App
4. Write code and press F5 to run

### **VS Code Setup**

```bash
# Install C# Dev Kit extension
# Install .NET Install Tool extension

# Create project
dotnet new console -n MyApp
cd MyApp
code .

# Debug with launch.json (automatically created)
```

---

## **Common Debugging Tips**

```csharp
// 1. Console Output
Console.WriteLine($"Debug: value = {value}");
Console.WriteLine($"Debug: {nameof(variable)} = {variable}");

// 2. Debug class
System.Diagnostics.Debug.WriteLine("Debug message");
System.Diagnostics.Debug.Assert(value > 0, "Value should be positive");

// 3. Breakpoints
// In IDE: Click left margin or Ctrl+B

// 4. Conditional Breakpoint
// Right-click breakpoint → Filter → Add condition

// 5. Debug Output
if (System.Diagnostics.Debugger.IsAttached)
{
    Console.WriteLine("Debugger attached");
}

// 6. Exception Helpers
try
{
    throw new InvalidOperationException("Something failed");
}
catch (Exception ex)
{
    System.Diagnostics.Debug.WriteLine(ex.ToString());
}
```

---

## **Summary Table**

| Concept | Version | Key Feature |
|---------|---------|-------------|
| **Nullable Reference Types** | C# 8.0 | Type-safe null handling |
| **Records** | C# 9.0 | Value semantics for classes |
| **Primary Constructors** | C# 12 | Simplified constructor syntax |
| **Pattern Matching** | C# 7.0+ | Powerful expression matching |
| **Async/Await** | C# 5.0 | Built-in asynchronous programming |
| **LINQ** | C# 3.0 | Query language for collections |
| **Generics** | C# 2.0 | Type-safe containers |
| **Task Parallel Library** | .NET 4.0 | Parallel computation |
| **Entity Framework Core** | .NET Core | ORM for databases |

---

## **Learning Resources**

- **Microsoft Docs**: https://docs.microsoft.com/en-us/dotnet/csharp/
- **C# Documentation**: https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp
- **.NET Learning**: https://learn.microsoft.com/en-us/training/
- **GitHub Samples**: https://github.com/dotnet/samples
- **Pluralsight**: C# and .NET courses
- **YouTube**: Various C# tutorial channels

---

## **Key Takeaways**

✅ **C#** is a modern, versatile language for building various applications
✅ **.NET 8/9** are the current standard versions with excellent performance
✅ **Async/Await** enables scalable, responsive applications
✅ **LINQ** provides powerful data querying capabilities
✅ **Entity Framework Core** simplifies database operations
✅ **Pattern Matching** makes code more expressive
✅ **Nullable Reference Types** prevent null reference exceptions
✅ **Records** provide value semantics for data classes
✅ **Dependency Injection** is built-in for loose coupling
✅ **Testing** is crucial for maintainable code

This comprehensive guide covers everything from C# fundamentals to advanced enterprise patterns. Practice with real projects to master these concepts! 🚀
