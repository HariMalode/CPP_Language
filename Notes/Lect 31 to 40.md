1. What is Constructor Overloading, Explain with an example?
2. Explain dynamic initialization of objects, with an example?( depends on datatype which constructor is called)
3. Explain copy constructor and default copy constructor in C++ with example?
4. Explain Destructor in C++ with an example?

### 1. **Constructor Overloading in C++**

**Constructor Overloading** is a concept where a class can have multiple constructors with different parameter lists. The constructor that matches the number and type of arguments provided during object creation is invoked.

#### Example:

```cpp
#include<iostream>
using namespace std;

class Rectangle {
    int length, width;

public:
    // Constructor with no parameters
    Rectangle() {
        length = 0;
        width = 0;
    }

    // Constructor with two parameters
    Rectangle(int l, int w) {
        length = l;
        width = w;
    }

    // Constructor with one parameter
    Rectangle(int side) {
        length = side;
        width = side;
    }

    int area() {
        return length * width;
    }
};

int main() {
    Rectangle r1;          // Calls the default constructor
    Rectangle r2(10, 20);  // Calls the constructor with two parameters
    Rectangle r3(15);      // Calls the constructor with one parameter

    cout << "Area of r1: " << r1.area() << endl;
    cout << "Area of r2: " << r2.area() << endl;
    cout << "Area of r3: " << r3.area() << endl;

    return 0;
}
```

Here, three constructors are defined for the `Rectangle` class. Depending on the arguments passed, the correct constructor is invoked.

### 2. **Dynamic Initialization of Objects**

Dynamic initialization allows initializing objects at runtime based on input or other runtime values. You can use constructors with parameters to achieve dynamic initialization.

#### Example:
```cpp
#include<iostream>
using namespace std;
class BankDeposit{
    int principal,year;
    float interestRate,returnValue;
    public:
    BankDeposit(){}
    BankDeposit(int p,int y,float r);  
    BankDeposit(int p,int y,int r);
    void show(){
        cout<<"\n Principal amt :"<<principal<<". \n You Will Recieve  Rs "<<returnValue<<"  After "<<year<<" Years";
    }
};
BankDeposit::BankDeposit(int p,int y,float r){
        principal=p;
        year=y;
        interestRate=r;
        returnValue=principal;
        for (int i = 0; i < year; i++)
        {
            //returnValue=returnValue+(returnValue*interestRate);
            returnValue=returnValue*(1+interestRate);
        }
        
    }
BankDeposit::BankDeposit(int p,int y,int r){
        principal=p;
        year=y;
        interestRate=(float)r/100;
        returnValue=principal;
        for (int i = 0; i < year; i++)
        {
            //returnValue=returnValue+(returnValue*interestRate);
            returnValue=returnValue*(1+interestRate);
        }
        
    }
int main(){
    BankDeposit bd1,bd2,bd3;
    int p,y;
    float r;
    int R;
    cout<<"\n Enter Principal,Rate(Float),Year:";
    cin>>p>>r>>y;
    bd1=BankDeposit(p,y,r);
    bd1.show();


    cout<<"\n Enter Principal,Rate(int),Year:";
    cin>>p>>R>>y;
    bd2=BankDeposit(p,y,R);
    bd2.show();
     return 0;
}
```
The given C++ code demonstrates a BankDeposit class that calculates the return value of a bank deposit based on the principal amount, interest rate, and the number of years. It uses two constructors: one for a float interest rate and another for an integer rate. Here's a breakdown:
```
Enter Principal,Rate(Float),Year: 1000 0.05 3

Principal amt : 1000. 
You Will Receive Rs 1157.63 After 3 Years

Enter Principal,Rate(int),Year: 1000 5 3

Principal amt : 1000. 
You Will Receive Rs 1157.63 After 3 Years

```
### 3. **Copy Constructor and Default Copy Constructor**

A **Copy Constructor** is a special constructor used to create a new object as a copy of an existing object. The default copy constructor performs a shallow copy, which means copying the value of each data member from one object to another.
- If you don't provide a copy constructor, the compiler will generate a default copy constructor that performs a shallow copy.
- It is useful when you want to create a new object that is an exact copy of an existing object.

#### Example:
```cpp
#include<iostream>
using namespace std;

class copyC{
    int a;  // Private member variable to store an integer 'a'

    public:
    // Default constructor that initializes 'a' to 0
    copyC(){
        a = 0;
    }

    // Parameterized constructor that sets 'a' to a given value 'p'
    copyC(int p){
        a = p;
    }

    // Function to display the value of 'a'
    void show(){
        cout << "\n Value Of A:" << a;
    }

    // Copy constructor: It takes a reference of another object 'obj' to create a copy
    copyC(copyC &obj){
        cout << "\n Copy Cons Called!!!"; // Display message when the copy constructor is called
        a = obj.a;  // Copy the value of 'a' from the passed object to the new object
    }
};

int main(){
    copyC ob1, ob2(4);  // Create two objects: ob1 with default constructor, ob2 with value 4
    ob1.show();   // Display the value of 'a' in ob1 (0)
    ob2.show();   // Display the value of 'a' in ob2 (4)

    // Call copy constructor to create ob3 as a copy of ob2
    copyC ob3(ob2);
    ob3.show();  // Display the value of 'a' in ob3 (4)

    // Call copy constructor to create ob4 as a copy of ob3
    copyC ob4(ob3);
    ob4.show();  // Display the value of 'a' in ob4 (4)

    return 0;
}
```
```

Value Of A: 0
Value Of A: 4
Copy Cons Called!!!
Value Of A: 4
Copy Cons Called!!!
Value Of A: 4

```


### 4. **Destructor in C++**

A **Destructor** is a special member function that is executed when an object goes out of scope or is explicitly deleted. It is used to release resources like memory or file handles that the object might have acquired during its lifetime.

#### Example:

```
#include<iostream>
using namespace std;

int count = 0;  // Global variable to track the number of object creations

class Des {
    public:
    // Constructor: Increments 'count' each time an object is created
    Des() {
        count++;
        cout << "\n This is the time when Constructor is called for obj no " << count;
    }

    // Destructor: Decrements 'count' each time an object is destroyed
    ~Des() {
        count--;
        cout << "\n This is the time when Destructor is called for obj no " << count;
    }
};

int main() {
    cout << "\n We are in Main Func";

    cout << "\n Creating First Obj";
    Des o1;  // First object is created, calling the constructor

    // A block scope is defined here
    {
        cout << "\n We are in Block";
        cout << "\n Creating 2 more objects";

        Des o2, o3;  // Two more objects are created, calling the constructor for both

        cout << "\n Exiting the Block";
        // When the block ends, destructors will be called for o2 and o3 as they go out of scope
    }

    // After exiting the block, control is back to the main function
    cout << "\n Back to Main Func";

    // The destructor for o1 will be called when the main function ends
    return 0
}
```
Output (Sample):
```
We are in Main Func
Creating First Obj
This is the time when Constructor is called for obj no 1
We are in Block
Creating 2 more objects
This is the time when Constructor is called for obj no 2
This is the time when Constructor is called for obj no 3
Exiting the Block
This is the time when Destructor is called for obj no 2
This is the time when Destructor is called for obj no 1
Back to Main Func
This is the time when Destructor is called for obj no 0
```

---

1. Explain What is Inheritance in C++ in detail.
2. Explain types of inheritance in C++ with diagrams
3. Explain Inheritance syntax and visibility mode rules, Explain Example
4. Explain Single inheritance in C++, consider following example:
5. Explain Protected Access modifiers and its rules. Explain Example.
6. Explain Multilevel inheritance in C++, consider following example:

### 1. **What is Inheritance in C++?**

**Inheritance** is a fundamental concept in object-oriented programming (OOP) that allows a new class (derived class) to inherit properties and behaviors (data members and member functions) from an existing class (base class). This helps in reusing code and establishing a hierarchical relationship between classes.

- **Base Class**: The class being inherited from.
- **Derived Class**: The class that inherits from the base class.

Inheritance promotes code reuse, logical hierarchy, and a more modular approach to programming.

### 2. **Types of Inheritance in C++**

Inheritance can be categorized into several types, each with its specific use cases and characteristics. Here are the primary types with diagrams:

#### **1. Single Inheritance**

A derived class inherits from a single base class.

```
    Base
     |
   Derived
```

**Example**: `class Derived : public Base { ... };`

#### **2. Multiple Inheritance**

A derived class inherits from more than one base class.

```
    Base1     Base2
      \        /
       \      /
        Derived
```

**Example**: `class Derived : public Base1, public Base2 { ... };`

#### **3. Multilevel Inheritance**

A derived class inherits from another derived class, forming a chain of inheritance.

```
    Base
     |
   Derived1
     |
   Derived2
```

**Example**: `class Derived2 : public Derived1 { ... };`

#### **4. Hierarchical Inheritance**

Multiple derived classes inherit from a single base class.

```
      Base
     /    \
   D1      D2
```

**Example**: `class Derived1 : public Base { ... };` and `class Derived2 : public Base { ... };`

#### **5. Hybrid Inheritance**

A combination of two or more types of inheritance. It is often a mix of multiple and hierarchical inheritance.

```
        Base1     Base2
          \        /
           \      /
            Derived1
               |
            Derived2
```

**Example**: `class Derived1 : public Base1, public Base2 { ... };` and `class Derived2 : public Derived1 { ... };`

### 3. **Inheritance Syntax and Visibility Mode Rules**

#### **Syntax:**

```cpp
class DerivedClass : accessSpecifier BaseClass {
    // Members of DerivedClass
};
```

**Access Specifiers:**
- **public**: Base class members accessible as public in derived class.
- **protected**: Base class members accessible as protected in derived class.
- **private**: Base class members inaccessible in derived class.

**Example:**

```cpp
class Base {
public:
    int pubData;
protected:
    int protData;
private:
    int privData;
};

class Derived : public Base {
    // pubData is accessible
    // protData is accessible
    // privData is not accessible
};
```

### 4. **Single Inheritance Example**

#### Code:

```cpp
#include <iostream>
using namespace std;

class Base {
    int data1;

public:
    int data2;
    void setData();
    int getData1();
    int getData2();
};

void Base::setData() {
    data1 = 10;
    data2 = 20;
}

int Base::getData1() {
    return data1;
}

int Base::getData2() {
    return data2;
}

class Derived : public Base {
    int data3;

public:
    void Process();
    void Display();
};

void Derived::Process() {
    data3 = data2 * getData1();
}

void Derived::Display() {
    cout << "\nData 1: " << getData1();
    cout << "\nData 2: " << data2;
    cout << "\nData 3: " << data3;
}

int main() {
    Derived der;
    der.setData();
    der.Process();
    der.Display();
    return 0;
}
```

#### Output:

```plaintext
Data 1: 10
Data 2: 20
Data 3: 200
```

### 5. **Protected Access Modifiers and Rules**

**Protected** access modifier allows derived classes to access the members of the base class but prevents access from outside the class hierarchy.

- **Rules:**
  - **Protected members** of the base class can be accessed by derived classes.
  - **Protected members** cannot be accessed directly from outside the class hierarchy.

**Example:**

```cpp
#include <iostream>
using namespace std;

class Base {
protected:
    int protectedData;
public:
    Base() : protectedData(10) {}
};

class Derived : public Base {
public:
    void showData() {
        cout << "Protected Data: " << protectedData << endl;
    }
};

int main() {
    Derived d;
    d.showData();  // Accessible within derived class
    // cout << d.protectedData;  // Error: protectedData is protected
    return 0;
}
```

#### Output:

```plaintext
Protected Data: 10
```

Here’s a table summarizing how different access specifiers affect the inheritance of members in C++:

| **Access Specifier**   | **Public Derivation** | **Private Derivation** | **Protected Derivation** |
|------------------------|------------------------|-------------------------|---------------------------|
| **Private Members**    | Not Inherited           | Not Inherited            | Not Inherited             |
| **Protected Members**  | Protected               | Private                 | Protected                 |
| **Public Members**     | Public                  | Private                 | Protected                 |

### Explanation:

1. **Public Derivation**:
   - **Private Members**: Not inherited by the derived class.
   - **Protected Members**: Remain protected in the derived class.
   - **Public Members**: Remain public in the derived class.

2. **Private Derivation**:
   - **Private Members**: Not inherited by the derived class.
   - **Protected Members**: Become private in the derived class.
   - **Public Members**: Become private in the derived class.

3. **Protected Derivation**:
   - **Private Members**: Not inherited by the derived class.
   - **Protected Members**: Remain protected in the derived class.
   - **Public Members**: Become protected in the derived class.

This table helps to understand how access specifiers affect the visibility of base class members in the derived class based on the type of inheritance used.

### 6. **Multilevel Inheritance Example**

#### Code:

```cpp
#include<iostream>
using namespace std;

class Student {
protected:
    int rollNo;
public:
    void setRoll(int r) {
        rollNo = r;
    }
    void getRoll() {
        cout << "\nRoll NO: " << rollNo;
    }
};

class Exam : public Student {
protected:
    float math;
    float phy;
public:
    void setMark(float a, float b) {
        math = a;
        phy = b;
    }
    void getMark() {
        cout << "\nMath Mark: " << math;
        cout << "\nPhy Mark: " << phy;
    }
};

class Result : public Exam {
    float Percentage;
public:
    void Show() {
        getRoll();
        getMark();
        cout << "\nYour Result: " << (math + phy) / 2 << " %";
    }
};

int main() {
    Result Luv;
    Luv.setRoll(45);
    Luv.setMark(92, 96);
    Luv.Show();
    return 0;
}
```

#### Output:

```plaintext
Roll NO: 45
Math Mark: 92
Phy Mark: 96
Your Result: 94 %
```

These explanations and examples should give you a comprehensive understanding of inheritance in C++ and its various types and rules.
---
