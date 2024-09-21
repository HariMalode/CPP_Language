### Explain
1. Explain Multiple Inheritance with following example.
2. Explain ambiguity resolution in single Inheritance and multiple inheritance with example.
3. Explain Virtual Base Class in CPP with diagram
4. Explain following example for virtual base class.

### 1. **Multiple Inheritance Example Explanation**

The given code illustrates **multiple inheritance** in C++, where a derived class inherits from more than one base class. Here is an explanation of how it works:

```cpp
#include<iostream>
using namespace std;

// Base class 1
class Base1{
    protected:
    int base1int;
    public:
    void setBase1(int a){
        base1int = a;
    }
};

// Base class 2
class Base2{
    protected:
    int base2int;
    public:
    void setBase2(int a){
        base2int = a;
    }
};

// Base class 3
class Base3{
    protected:
    int base3int;
    public:
    void setBase3(int a){
        base3int = a;
    }
};

// Derived class inherits from Base1, Base2, and Base3
class Derived : public Base1, public Base2, public Base3 {
    public:
    void show(){
        // Accessing inherited members
        cout << "\n Value of Base1int: " << base1int;
        cout << "\n Value of Base2int: " << base2int;
        cout << "\n Value of Base3int: " << base3int;
        cout << "\n Sum of these values: " << base1int + base2int + base3int;
    }   
};

int main(){
    Derived obj;
    obj.setBase1(10);
    obj.setBase2(20);
    obj.setBase3(30);
    obj.show();
    return 0;
}
```

**Explanation:**
- Three base classes `Base1`, `Base2`, and `Base3` each have a protected member variable (`base1int`, `base2int`, `base3int`) and a public method to set their values.
- The `Derived` class inherits from all three base classes, which gives it access to all of the base class member functions and data members.
- In `main()`, an object of the `Derived` class sets values for each base class member using the respective `setBase1()`, `setBase2()`, and `setBase3()` methods. The `show()` method then displays the values and their sum.

### 2. **Ambiguity Resolution in Inheritance**

#### **Single Inheritance Ambiguity:**
Ambiguity can occur in **single inheritance** if both the base class and the derived class have methods or member variables with the same name.

Example:

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void show() {
        cout << "Base class show()" << endl;
    }
};

class Derived : public Base {
public:
    void show() {  // Method with the same name
        cout << "Derived class show()" << endl;
    }
};

int main() {
    Derived obj;
    obj.show();  // Calls the derived class method by default
    obj.Base::show();  // Resolves ambiguity by explicitly calling the base class method
    return 0;
}
```

**Explanation:**
- In this case, both the base and derived classes have a `show()` function.
- Calling `obj.show()` will invoke the derived class's method by default.
- The ambiguity is resolved by using `obj.Base::show()`, which explicitly calls the base class method.

#### **Multiple Inheritance Ambiguity:**
When a class inherits from multiple base classes, and they contain methods with the same name, ambiguity can arise.

Example:

```cpp
#include <iostream>
using namespace std;

class Base1 {
public:
    void greet() {
        cout << "Hello from Base1!" << endl;
    }
};

class Base2 {
public:
    void greet() {
        cout << "Hello from Base2!" << endl;
    }
};

class Derived : public Base1, public Base2 {
public:
    void greet() {
        Base1::greet();  // Resolves ambiguity
        Base2::greet();  // Resolves ambiguity
    }
};

int main() {
    Derived obj;
    obj.greet();  // Calls both Base1 and Base2 greet()
    return 0;
}
```

**Explanation:**
- Both `Base1` and `Base2` have a method `greet()`, which leads to ambiguity when called from `Derived`.
- The ambiguity is resolved by specifying `Base1::greet()` and `Base2::greet()` to call the respective base class methods.

### 3. **Virtual Base Class in C++ with Diagram**

A **virtual base class** solves the problem of **diamond inheritance** in multiple inheritance. Diamond inheritance occurs when a class is derived from two classes, both of which are derived from the same base class. Without virtual inheritance, the derived class would have two copies of the base class, leading to ambiguity.

**Diagram:**
```
   Student
     / \
    /   \
  Test   Sports
    \   /
     \ /
    Result
```

In this case, `Test` and `Sports` inherit from `Student`, and `Result` inherits from both `Test` and `Sports`. Without virtual inheritance, `Result` would have two copies of `Student`. Using a **virtual base class** ensures that there is only one instance of `Student` in `Result`.

### 4. **Virtual Base Class Example Explanation**

```cpp
#include <iostream>
using namespace std;

// Base class
class Student {
protected:
    int roll;
public:
    void setRoll(int a) {
        roll = a;
    }
    void printRoll() {
        cout << "\n Your Roll no: " << roll;
    }
};

// Test inherits from Student using virtual inheritance
class Test : public virtual Student {
protected:
    int phy, che;
public:
    void setMarks(int a, int b) {
        phy = a;
        che = b;
    }
    void printMarks() {
        cout << "\n Your Academics Marks:";
        cout << "\n Physics: " << phy;
        cout << "\n Chemistry: " << che;
    }
};

// Sports also inherits from Student using virtual inheritance
class Sports : virtual public Student {
protected:
    int score;
public:
    void setScore(int a) {
        score = a;
    }
    void printScore() {
        cout << "\n Your Sports Marks:";
        cout << "\n BasketBall: " << score;
    }
};

// Result class inherits from both Test and Sports
class Result : public Test, public Sports {
public:
    void Show() {
        int total = phy + che + score;
        printRoll();    // No ambiguity as there is a single instance of Student
        printMarks();
        printScore();
        cout << "\n Your Total Score: " << total;
    }
};

int main() {
    Result obj;
    obj.setRoll(11);
    obj.setMarks(78, 45);
    obj.setScore(96);
    obj.Show();
    return 0;
}
```

**Explanation:**
- `Student` is the base class that holds the `roll` number of a student.
- Both `Test` and `Sports` inherit from `Student` using **virtual inheritance**, ensuring only one copy of `Student` exists when `Result` inherits from both.
- In `Result`, there is no ambiguity in accessing the `roll` number, as virtual inheritance prevents multiple copies of `Student` from being created.


---

### Explain
1. Explain Constructors in inheritance, Specify the rules of which constructor will run.
2. Solve Inheritance Question
3. Explain following example constructor in derived class.
4. Explain Initialization List in constructor with following example.
5. Explain pointers in cpp. Also Explain Keyword "new" and its use

### 1. **Constructors in Inheritance:**

In C++, constructors in inheritance follow specific rules regarding the order in which they are called.

- **Base Class Constructor**: When a derived class object is created, the base class's constructor is always called first, followed by the derived class's constructor.
- **Order of Constructor Calls**: 
  - If there is a single inheritance chain (one base class), the base class constructor is called first.
  - In multiple inheritance, constructors are called in the order in which the base classes are inherited.
- **Constructor Overloading**: Constructors can be overloaded (having more than one version), and the appropriate constructor will be called based on the arguments passed when the derived class object is created.

#### **Rules for Which Constructor Will Run:**
1. The base class constructor is invoked before the derived class constructor.
2. If the base class has a parameterized constructor, you must explicitly call it from the derived class constructor.
3. In case of multiple inheritance, constructors are called in the order of base class inheritance in the derived class.

#### Example:

```cpp
#include<iostream>
using namespace std;

class Base {
public:
    Base() {
        cout << "Base class constructor called" << endl;
    }
};

class Derived : public Base {
public:
    Derived() {
        cout << "Derived class constructor called" << endl;
    }
};

int main() {
    Derived obj;  // First, Base constructor is called, then Derived constructor
    return 0;
}
```

### 2. **Hybrid Calculator - Inheritance Example**

This problem demonstrates how to use inheritance in a hybrid calculator that can perform both simple and scientific calculations.

```cpp
#include <iostream>
#include <cmath>  // For sin, cos, tan, exp functions
using namespace std;

class SimpleCalculator {
protected:
    float num1, num2;
public:
    void setSimpleNumbers(float a, float b) {
        num1 = a;
        num2 = b;
    }
    void performOperations() {
        cout << "Addition: " << num1 + num2 << endl;
        cout << "Subtraction: " << num1 - num2 << endl;
        cout << "Multiplication: " << num1 * num2 << endl;
        cout << "Division: " << num1 / num2 << endl;
    }
};

class ScientificCalculator {
protected:
    float num;
public:
    void setScientificNumber(float x) {
        num = x;
    }
    void performScientificOperations() {
        cout << "Sine: " << sin(num) << endl;
        cout << "Cosine: " << cos(num) << endl;
        cout << "Tangent: " << tan(num) << endl;
        cout << "Exponential: " << exp(num) << endl;
    }
};

// HybridCalculator inherits from both SimpleCalculator and ScientificCalculator
class HybridCalculator : public SimpleCalculator, public ScientificCalculator {
public:
    void showResults() {
        performOperations();
        performScientificOperations();
    }
};

int main() {
    HybridCalculator calc;
    calc.setSimpleNumbers(5, 3);
    calc.setScientificNumber(45);  // Assuming angle in radians
    calc.showResults();
    return 0;
}
```

### 3. **Constructor in Derived Class Example Explanation**

**Three Cases:**
```
CASE1:
class B: public A{
    ORDER of Execution: A() then B()
}
CASE2: B is written first then const of B will run first
class B: public B, public C{
    ORDER of Execution:  B(),C() then A()
}
CASE1: VIRTAUL ALWAYS ON TOP
class B: public B, Virtual public C{
    ORDER of Execution: C(), B() then A()
}
```

```cpp
#include<iostream>
using namespace std;

class base1 {
    int data1;
public:
    base1(int a) {
        data1 = a;
        cout << "\n Base1 Constructor called";
    }
    void printData1() {
        cout << "\n Value Of Data1: " << data1;
    }
};

class base2 {
    int data2;
public:
    base2(int b) {
        data2 = b;
        cout << "\n Base2 Constructor called";
    }
    void printData2() {
        cout << "\n Value Of Data2: " << data2;
    }
};

class Derived : public base1, public base2 {  //this affect on which const will run first ,sequence this
    int data3, data4;
public:
    // Calling base class constructors using initialization list
    Derived(int p, int q, int r, int s) : base1(p), base2(q) { 
        data3 = r;
        data4 = s;
        cout << "\n Derived Constructor called";
    }
    void printData34() {
        cout << "\n Value Of Data3, Data4: " << data3 << ", " << data4;
    }
};

int main() {
    Derived obj(1, 2, 3, 4);
    obj.printData1();
    obj.printData2();
    obj.printData34();
    return 0;
}
```

**Explanation**:
- The `Derived` class inherits from `base1` and `base2`.
- The derived class constructor calls the base class constructors using an **initialization list**.
- The output demonstrates that the base class constructors are invoked before the derived class constructor.

### 4. **Initialization List in Constructor**

An **initialization list** is used to initialize data members and call base class constructors before the body of the constructor executes.

```cpp
#include<iostream>
using namespace std;

class base {
    int a, b;
public:
    // Initialization list is used to initialize a and b
    base(int p, int q) : a(p), b(q) {
        cout << "\n Constructor Executed!!";
        cout << "\n Value Of A & B: " << a << " , " << b;
    }
};

int main() {
    base obj(3, 4);
    return 0;
}
```


- base(int p, int q) : a(p), b(q) => works as a=p and b=q
- base(int p, int q) : a(p), b(p+q) => works as a=p and b=p+q
- base(int p, int q) : a(p), b(q*2) => works as a=p and b=q*2
- base(int p, int q) : a(p), b(a+q) => works 
- base(int p, int q) : b(q), a(p+b) => Not works as a declared first so vo phle hona
- 


**Explanation**:
- In the initialization list `: a(p), b(q)`, `a` is initialized with `p` and `b` with `q`.
- This method of initializing members before the constructor body executes is more efficient and necessary for certain scenarios, such as initializing `const` or reference members.

### 5. **Pointers in C++**

A **pointer** is a variable that stores the memory address of another variable. Pointers are a powerful feature in C++ used for dynamic memory allocation, passing arrays to functions, and more.

```cpp
int x = 10;
int* ptr = &x;  // ptr stores the address of x
cout << *ptr;   // Dereferencing pointer to access value at address
```

#### **Keyword `new`**
The `new` keyword is used for dynamic memory allocation in C++. It allocates memory on the **heap** and returns a pointer to the memory location.

```cpp
int* ptr = new int;   // Dynamically allocate an integer
*ptr = 5;
cout << *ptr;         // Output: 5
delete ptr;           // Free the allocated memory
```
```
#include <iostream>
using namespace std;

int main()
{
     // normal
     int a = 6;
     int *b = &a;
     cout << "\n Adrees Of A:" << b;
     cout << "\n Value Of A:" << *b;

     // new
     int *p = new int(10);
     cout << "\n Value Of P:" << *p;
     cout << "\n Adress Of P:" << p;

     int *arr = new int[3];
     arr[0] = 11;
     arr[1] = 22;
     *(arr + 2) = 33;
     cout << "\n\n  value of arr[0]:" << arr[0];
     cout << "\n  value of arr[1]:" << arr[1];
     cout << "\n  value of arr[2]:" << arr[2];
     cout << "\n\n  Address of arr[0]:" << arr;
     cout << "\n Address of arr[0]:" << arr + 1;
     cout << "\n  Address of arr[0]:" << arr + 2;

     return 0;
}
```
**Usage**:
- `new` allocates memory during runtime.
- It returns a pointer to the newly allocated memory block.
- **Memory management**: When `new` is used, you must free the allocated memory using `delete` to avoid memory leaks.