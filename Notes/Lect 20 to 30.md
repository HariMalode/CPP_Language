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