# Q1. Explain 
1. Object Oriented Programming
2. Why OOPs?
3. Explain basic concept in Oops: classes ,objects, Data abstraction & Encapsulation, Inheritance,Polymorphism, Dynamic binding, Messge passing
4. Why we prefer class insted od structure?
5. Provide a code of nesting of member function 


### 1. Object-Oriented Programming (OOP)
Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects," which are instances of classes. These objects can contain data, in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).
- The moto of cpp is to add OOP in C language

### 2. Why OOP?
OOP offers several advantages:
- **Modularity:** The source code for an object can be written and maintained independently of the source code for other objects.
- **Reusability:** Objects can be reused across programs.
- **Scalability:** Easier to manage and scale complex programs.
- **Maintainability:** Easy to maintain and modify existing code.
- Provide Features such as class , object, private, public etc

### 3. Basic Concepts in OOP

#### Classes and Objects
- **Class:** A blueprint for creating objects. It defines a datatype by bundling data and methods that work on the data into one single unit.
- **Object:** An instance of a class.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    string model;
    int year;

    void display() {
        cout << "Brand: " << brand << "\nModel: " << model << "\nYear: " << year << endl;
    }
};

int main() {
    Car car1;
    car1.brand = "Toyota";
    car1.model = "Corolla";
    car1.year = 2020;

    car1.display();

    return 0;
}
```

**Output:**
```
Brand: Toyota
Model: Corolla
Year: 2020
```

#### Data Abstraction and Encapsulation
- **Data Abstraction:** The process of exposing only the relevant and essential data to the outside world while hiding the background details.
- **Encapsulation:** Wrapping data and the methods that work on data within a single unit, i.e., a class.

**Example:**
```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance;

public:
    void setBalance(double bal) {
        balance = bal;
    }

    double getBalance() {
        return balance;
    }
};

int main() {
    BankAccount account;
    account.setBalance(1000.50);
    cout << "Balance: $" << account.getBalance() << endl;

    return 0;
}
```

**Output:**
```
Balance: $1000.5
```

#### Inheritance
Inheritance allows a class to inherit properties and methods from another class.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Vehicle {
public:
    string brand = "Ford";
    void honk() {
        cout << "Honk! Honk!" << endl;
    }
};

class Car : public Vehicle {
public:
    string model = "Mustang";
};

int main() {
    Car myCar;
    myCar.honk();
    cout << myCar.brand + " " + myCar.model << endl;

    return 0;
}
```

**Output:**
```
Honk! Honk!
Ford Mustang
```

#### Polymorphism
Polymorphism means "many forms." It allows one interface to be used for a general class of actions.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void makeSound() {
        cout << "Animal sound" << endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() override {
        cout << "Bark" << endl;
    }
};

int main() {
    Animal* animal;
    Dog dog;
    animal = &dog;

    animal->makeSound();

    return 0;
}
```

**Output:**
```
Bark
```

#### Dynamic Binding
Dynamic binding (or late binding) occurs when the method to be invoked is determined at runtime.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class" << endl;
    }
};

int main() {
    Base* b;
    Derived d;
    b = &d;

    b->show();

    return 0;
}
```

**Output:**
```
Derived class
```

#### Message Passing
Message passing involves calling methods on objects to communicate and perform actions.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Messenger {
public:
    void sendMessage(string message) {
        cout << "Message: " << message << endl;
    }
};

int main() {
    Messenger msg;
    msg.sendMessage("Hello, World!");

    return 0;
}
```

**Output:**
```
Message: Hello, World!
```

### 4. Why We Prefer Classes Instead of Structures
Classes provide the following benefits over structures:
- **Data Hiding:** Members of a class can be private, protected, or public.
- **Methods:** Classes can contain methods (functions), whereas structures cannot (in C, but they can in C++).
- **Inheritance and Polymorphism:** Classes support inheritance and polymorphism, allowing for more complex data modeling and reuse.

### 5. Nesting of Member Functions
Nesting of member functions means calling one member function from within another member function of the same class.

**Example:**
```cpp
#include <iostream>
#include <string>
using namespace std;

class Binary
{
private:
    string s;
    void chk();

public:
    void read();
    void onescomp();
    void show();
};

int main() //driver program
{
    Binary ok;
    ok.read();
    // ok.chk(); not possible coz it is pvt
    ok.onescomp();
    ok.show();

    return 0;
}
void Binary::read()
{
    cout << "\n Enter  Binary Number:";
    cin >> s;
}
void Binary::chk()
{
    for (int i = 0; i < s.length(); i++)
    {
        if (s.at(i) != '1' && s.at(i) != '0')
        {
            cout << "\n Invalid Binary NO";
            exit(0);
        }
    }
}
void Binary::onescomp()
{
    chk(); // here pvt can access
    for (int i = 0; i < s.length(); i++)
    {
        if (s.at(i) == '0')
        {
            s.at(i) = '1';
        }
        else
        {
            s.at(i) = '0';
        }
    }
}
void Binary::show()
{
    cout << s;
}
```


These explanations and examples should help you understand the fundamental concepts of OOP in C++.

----

# Q2.Explain following in CPP

1. Explain Objects Memory allocation in cpp : concept of memory alloted to variables when object created and function memory shared
2. Explain Arrays in Classes with example
3. Explain Static data members and static methods in CPP
4. Explain Array of object in CPP
5. Explain Passing Object as function argument 



Certainly! Let's delve into each of these topics in C++:

### 1. Objects Memory Allocation in C++

In C++, when you create an object of a class, memory is allocated for the object's member variables. Here's a breakdown of how memory allocation works:

- **Member Variables**: When an object is created, memory is allocated for its member variables. This memory is allocated on the stack if the object is created locally within a function, or on the heap if the object is created using `new`.
- **Member Functions**: Member functions do not consume memory for each object. They are shared among all instances of the class. Only one copy of each member function exists, regardless of the number of objects created.

Example:
```cpp
class MyClass {
public:
    int x;
    float y;

    void display() {
        // This function does not consume additional memory per object
        std::cout << "x: " << x << ", y: " << y << std::endl;
    }
};

int main() {
    MyClass obj1;
    MyClass obj2;

    obj1.x = 10;
    obj1.y = 20.5;

    obj2.x = 30;
    obj2.y = 40.5;

    obj1.display();
    obj2.display();

    return 0;
}
```
In this example, `obj1` and `obj2` each have their own `x` and `y` variables, but they share the same `display` function.

### 2. Arrays in Classes with Example

You can include arrays as member variables in classes. This is useful when your class needs to manage a collection of elements.

Example:
```cpp
class Student {
private:
    std::string name;
    int scores[5]; // Array to store scores in 5 subjects

public:
    void setName(std::string studentName) {
        name = studentName;
    }

    void setScores(int sc[]) {
        for (int i = 0; i < 5; i++) {
            scores[i] = sc[i];
        }
    }

    void display() {
        std::cout << "Name: " << name << std::endl;
        std::cout << "Scores: ";
        for (int i = 0; i < 5; i++) {
            std::cout << scores[i] << " ";
        }
        std::cout << std::endl;
    }
};

int main() {
    Student student;
    student.setName("John Doe");
    
    int sc[5] = {85, 90, 78, 92, 88};
    student.setScores(sc);
    
    student.display();

    return 0;
}
```
In this example, the `Student` class contains an array of integers `scores` to store scores in 5 subjects.

### 3. Static Data Members and Static Methods in C++

Static data members and static methods are associated with the class itself rather than any particular object.

- **Static Data Members**: There is only one copy of a static data member shared among all objects of the class.
- **Static Methods**: These can access only static data members and other static methods. They do not have access to instance data members.

Example:
```cpp
class MyClass {
public:
    static int count;

    MyClass() {
        count++;
    }

    static void showCount() {
        std::cout << "Count: " << count << std::endl;
    }
};

int MyClass::count = 0;

int main() {
    MyClass obj1;
    MyClass obj2;

    MyClass::showCount(); // Output: Count: 2

    return 0;
}
```
In this example, the static data member `count` is shared among all instances of `MyClass`. The static method `showCount` displays the current count.

### 4. Array of Objects in C++

You can create an array of objects in C++. This is useful when you need to manage multiple objects of the same class.

Example:
```cpp
class Employee {
private:
    std::string name;
    int id;

public:
    void setDetails(std::string empName, int empId) {
        name = empName;
        id = empId;
    }

    void display() {
        std::cout << "Name: " << name << ", ID: " << id << std::endl;
    }
};

int main() {
    Employee employees[3];

    employees[0].setDetails("Alice", 101);
    employees[1].setDetails("Bob", 102);
    employees[2].setDetails("Charlie", 103);

    for (int i = 0; i < 3; i++) {
        employees[i].display();
    }

    return 0;
}
```
In this example, we create an array of `Employee` objects and set details for each employee.

### 5. Passing Object as Function Argument

You can pass objects to functions either by value, by reference, or by pointer.

- **By Value**: A copy of the object is passed to the function.
- **By Reference**: A reference to the object is passed, allowing the function to modify the original object.
- **By Pointer**: A pointer to the object is passed.

Example:


In this code, you have a class `Comp` which represents a complex number with real and imaginary parts. The `sumData` function is used to sum two complex numbers and store the result in the object that calls the function.

Here's a detailed breakdown of the code:

### Class Definition

```cpp
#include<iostream>
using namespace std;

class Comp {
    int a, b; // Private members for real and imaginary parts

public:
    void setData(int n1, int n2) {
        a = n1;
        b = n2;
    }

    void putData() {
        cout << "\n Complex No:" << a << " + " << b << "i ";
    }

    void sumData(Comp o1, Comp o2) {
        a = o1.a + o2.a;
        b = o1.b + o2.b;
    }
};
```

- **Private Members**: `a` and `b` represent the real and imaginary parts of a complex number, respectively.
- **`setData` Function**: Sets the values of `a` and `b`.
- **`putData` Function**: Displays the complex number.
- **`sumData` Function**: Takes two `Comp` objects as arguments and calculates their sum. The result is stored in the calling object.

### Main Function

```cpp
int main() {
    Comp p1, p2, p3;

    p1.setData(4, 5);
    p1.putData();

    p2.setData(6, 7);
    p2.putData();

    p3.sumData(p1, p2);
    p3.putData();
    
    return 0;
}
```

- **Creating Objects**: `p1`, `p2`, and `p3` are objects of the `Comp` class.
- **Setting Data**: `setData` is called for `p1` and `p2` to initialize their values.
- **Displaying Data**: `putData` is called for `p1` and `p2` to display their initial values.
- **Summing Data**: `sumData` is called on `p3` with `p1` and `p2` as arguments. This calculates the sum of `p1` and `p2` and stores the result in `p3`.
- **Displaying Result**: `putData` is called on `p3` to display the resulting complex number after the sum.

### Output

The output of this code will be:

```
Complex No:4 + 5i 
Complex No:6 + 7i 
Complex No:10 + 12i 
```

This demonstrates how to pass objects as function arguments in C++, allowing functions to operate on the private data members of those objects. In the `sumData` function, the members `a` and `b` of the calling object (`p3` in this case) are updated with the sum of the corresponding members from the objects `o1` and `o2`.


-----



# Q3. Explain following in CPP
1. Friend Function in CPP? Its use?
2. Properties of Friend Function.
3. Member Friend Function and Friend Classes
4. SWAP in OOPS using friend function
5. What is Constructor in CPP ? Explain its Characteristics
6. Explain parametrized and default constructor with example


Let's go through each of these topics one by one:

### 1. **Friend Function in C++:**
A friend function in C++ is a function that is not a member of a class but has the privilege to access the class's private and protected members. A friend function is declared by using the keyword `friend` inside the class to which it needs access.

**Use:**
Friend functions are useful when:
- We need to access private or protected members of two or more different classes.
- We want to define a function that performs some operations that are not logically part of the class but still require access to its private members.

**Example Explanation:**

```cpp
#include <iostream>
using namespace std;

class Comp {
    int a, b;
    friend Comp hari(Comp, Comp); // Declare a friend function

public:
    void Set(int n1, int n2) {
        a = n1;
        b = n2;
    }
    void Show() {
        cout << "\n Complex No:" << a << " + " << b << "i ";
    }
};

Comp hari(Comp o1, Comp o2) {
    Comp o3;
    o3.Set((o1.a + o2.a), (o1.b + o2.b)); // Accessing private members of Comp
    return o3;
}

int main() {
    Comp p, q, r;
    p.Set(4, 5);
    p.Show();

    q.Set(6, 7);
    q.Show();

    r = hari(p, q);
    r.Show();

    return 0;
}
```
In this example:
- The function `hari` is a friend of the class `Comp`. It can access the private members `a` and `b` of objects `o1` and `o2` even though they are private.
- This function adds the real and imaginary parts of two complex numbers and returns the result.

### 2. **Properties of Friend Function:**
- **Access:** A friend function can access private and protected members of the class in which it is declared as a friend.
- **Not a Member Function:** It is not a member function of the class but can access its members.
- **Declared Inside Class:** It must be declared inside the class but defined outside the class.
- **Invocation:** A friend function can be called without using an object of the class, unlike member functions.
- **Scope:** The scope of a friend function is not limited to the class in which it is declared.

### 3. **Member Friend Function and Friend Classes with Program:**

**Member Friend Function:**
A member function of one class can be a friend function of another class.

**Friend Classes:**
A class can be made a friend of another class, which allows all member functions of the friend class to access the private and protected members of the other class.

**Example:**
```cpp
#include <iostream>
using namespace std;

class B; // Forward declaration

class A {
    int x;
public:
    A(int i) : x(i) {}
    friend void show(A, B); // Friend function
};

class B {
    int y;
public:
    B(int i) : y(i) {}
    friend void show(A, B); // Friend function
};

void show(A a, B b) {
    cout << "A's x: " << a.x << " and B's y: " << b.y << endl;
}

int main() {
    A objA(5);
    B objB(10);
    show(objA, objB); // Accessing private members of both classes
    return 0;
}
```
Here, `show` is a friend function of both `A` and `B`, allowing it to access the private members of both classes.

### 4. **SWAP in OOP using Friend Function with Code:**

**Example:**
```cpp
#include <iostream>
using namespace std;
class Y;
class X
{
    int a;

public:
    void SetData(int n1)
    {
        a = n1;
    }
    void show()
    {
        cout << "\n Value Of Class X:" << a;
    }
    friend void Exchange(X &, Y &);
};
class Y
{
    int a;

public:
    void SetData(int n1)
    {
        a = n1;
    }
    void show()
    {
        cout << "\n Value Of Class Y:" << a;
    }
    friend void Exchange(X &, Y &);
};
void Exchange(X &o1, Y &o2)
{
    int temp = o1.a;
    o1.a = o2.a;
    o2.a = temp;
}

int main()
{
    X ok1;
    Y ok2;

    ok1.SetData(10);
    ok2.SetData(50);

    cout << "\n Values Before Exchange:";
    ok1.show();
    ok2.show();
    Exchange(ok1, ok2);
    cout << "\n Values After Exchange:";
    ok1.show();
    ok2.show();

    return 0;
}
```
In this code, the `swap` function is a friend of `SwapClass` and swaps the private members of two objects.

### 5. **Constructor in C++:**
A constructor is a special member function of a class that is executed whenever new objects of that class are created. Constructors have the same name as the class and do not have a return type, not even `void`.

**Characteristics:**
- **Automatic Initialization:** Constructors are automatically called when an object is created.
- **Overloading:** Constructors can be overloaded to create multiple constructors with different parameters.
- **No Return Type:** Constructors do not return any value.
- **Default Constructor:** If no constructor is defined, C++ provides a default constructor.

### 6. **Parameterized and Default Constructor with Example:**

**Default Constructor:**
A default constructor is one that takes no arguments. If no constructor is provided, the compiler generates a default one.

**Parameterized Constructor:**
A constructor that takes parameters to initialize an object with specific values.

**Example:**

```cpp
#include <iostream>
using namespace std;

class Demo {
    int x;
public:
    Demo() { // Default constructor
        x = 0;
    }

    Demo(int val) { // Parameterized constructor
        x = val;
    }

    void show() {
        cout << "Value of x: " << x << endl;
    }
};

int main() {
    Demo obj1; // Calls default constructor
    Demo obj2(10); // Calls parameterized constructor

    obj1.show();
    obj2.show();

    return 0;
}
```
In this example:
- `obj1` uses the default constructor and initializes `x` to 0.
- `obj2` uses the parameterized constructor to initialize `x` to 10.
