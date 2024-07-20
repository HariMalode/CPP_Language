# Q1. Explain 
1. Break and Continue keywords in cpp
2. Explain Pointers
3. Pointer to pointer
4. Arrays in cpp
5. For loop in array
6. Pointer in Array

Certainly! Here are the explanations, code snippets, and their expected outputs:

### 1. Break and Continue Keywords in C++
- **`break`:** The `break` statement terminates the nearest enclosing loop or `switch` statement in which it appears.
- **`continue`:** The `continue` statement skips the rest of the code inside the current loop iteration and proceeds with the next iteration of the loop.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    // Using break
    for (int i = 1; i <= 5; ++i) {
        if (i == 3) {
            break; // Terminates the loop when i is 3
        }
        cout << "Iteration (break): " << i << endl;
    }

    // Using continue
    for (int i = 1; i <= 5; ++i) {
        if (i == 3) {
            continue; // Skips the rest of the loop body when i is 3
        }
        cout << "Iteration (continue): " << i << endl;
    }

    return 0;
}
```

**Output:**
```
Iteration (break): 1
Iteration (break): 2
Iteration (continue): 1
Iteration (continue): 2
Iteration (continue): 4
Iteration (continue): 5
```

### 2. Explain Pointers
Pointers are variables that store the memory address of another variable. They are used for dynamic memory allocation, arrays, and function arguments.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int var = 10;
    int *ptr = &var; // Pointer ptr holds the address of var

    cout << "Value of var: " << var << endl;
    cout << "Address of var: " << &var << endl;
    cout << "Pointer ptr points to address: " << ptr << endl;
    cout << "Value at the address ptr points to: " << *ptr << endl; // Dereferencing

    return 0;
}
```

**Output:**
```
Value of var: 10
Address of var: 0x7ffeea3b8b1c
Pointer ptr points to address: 0x7ffeea3b8b1c
Value at the address ptr points to: 10
```
(Note: The actual address will vary each time you run the program.)

### 3. Pointer to Pointer
A pointer to a pointer is a form of multiple indirection, or a chain of pointers. It means that you can have a pointer that points to another pointer, which in turn points to the actual variable.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int var = 10;
    int *ptr = &var;
    int **ptr2 = &ptr; // Pointer to pointer

    cout << "Value of var: " << var << endl;
    cout << "Value via ptr: " << *ptr << endl;
    cout << "Value via ptr2: " << **ptr2 << endl; // Double dereferencing

    return 0;
}
```

**Output:**
```
Value of var: 10
Value via ptr: 10
Value via ptr2: 10
```

### 4. Arrays in C++
Arrays are collections of elements of the same type placed in contiguous memory locations. The elements are accessed using indices.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5}; // An array of 5 integers

    for (int i = 0; i < 5; ++i) {
        cout << "Element at index " << i << " is " << arr[i] << endl;
    }

    return 0;
}
```

**Output:**
```
Element at index 0 is 1
Element at index 1 is 2
Element at index 2 is 3
Element at index 3 is 4
Element at index 4 is 5
```

### 5. For Loop in Array
A for loop is commonly used to iterate over the elements of an array.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};

    for (int i = 0; i < 5; ++i) {
        cout << "Element at index " << i << " is " << arr[i] << endl;
    }

    return 0;
}
```

**Output:**
```
Element at index 0 is 1
Element at index 1 is 2
Element at index 2 is 3
Element at index 3 is 4
Element at index 4 is 5
```

### 6. Pointer in Array
Pointers can be used to access and manipulate array elements.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    int *ptr = arr; // Pointer to the first element of the array

    for (int i = 0; i < 5; ++i) {
        cout << "Element at index " << i << " is " << *(ptr + i) << endl; // Accessing elements using pointer arithmetic
    }

    return 0;
}
```

**Output:**
```
Element at index 0 is 1
Element at index 1 is 2
Element at index 2 is 3
Element at index 3 is 4
Element at index 4 is 5
```

These explanations and outputs should help clarify how these concepts work in C++.


---


# Q2. Explain
1. Structures in Cpp
2. Typedef ,Union, Enum keywords
3. Function in cpp (A proper example Void int etc)
4. Call by Value and Call by Ref Example
5. Explain Inline function and its use
6. Static Variable in Cpp
7. Default argument in function Example
8. Recursion in Cpp

Sure! Let's cover each concept with explanations, code snippets, and their expected outputs.

### 1. Structures in C++
Structures in C++ are user-defined data types that group different types of variables under a single name. They are used to represent a record.

**Example:**
```cpp
#include <iostream>
using namespace std;

struct Person {
    string name;
    int age;
};

int main() {
    Person person1;
    person1.name = "John";
    person1.age = 30;

    cout << "Name: " << person1.name << endl;
    cout << "Age: " << person1.age << endl;

    return 0;
}
```

**Output:**
```
Name: John
Age: 30
```

### 2. `typedef`, `union`, `enum` Keywords
- **`typedef`:** Used to create an alias for another data type.
- **`union`:** Allows storing different data types in the same memory location.
- **`enum`:** Defines a set of named integer constants.

**Example:**
```cpp
#include <iostream>
using namespace std;

typedef int myint;

union Data {
    int intValue;
    float floatValue;
};

enum Color { RED, GREEN, BLUE };

int main() {
    // typedef example
    myint x = 10;
    cout << "x: " << x << endl;

    // union example
    Data data;
    data.intValue = 5;
    cout << "data.intValue: " << data.intValue << endl;
    data.floatValue = 10.5;
    cout << "data.floatValue: " << data.floatValue << endl; // Overwrites intValue

    // enum example
    Color color = RED;
    cout << "color: " << color << endl; // Outputs 0 for RED

    return 0;
}
```

**Output:**
```
x: 10
data.intValue: 5
data.floatValue: 10.5
color: 0
```

### 3. Functions in C++ (Void, int, etc.)
Functions are blocks of code that perform specific tasks and can return values or be void (no return value).

**Example:**
```cpp
#include <iostream>
using namespace std;

// Function that returns an int
int add(int a, int b) {
    return a + b;
}

// Void function
void printMessage() {
    cout << "Hello, World!" << endl;
}

int main() {
    int result = add(5, 3);
    cout << "Sum: " << result << endl; // Outputs 8

    printMessage(); // Outputs "Hello, World!"

    return 0;
}
```

**Output:**
```
Sum: 8
Hello, World!
```

### 4. Call by Value and Call by Reference Example
**Example:**
```cpp
#include <iostream>
using namespace std;

void SwapPointer(int *, int *);
void SwapReference(int &, int &);

int main() {
    int a = 21, b = 14;
    cout << "\nValue OF A&B: " << a << "," << b << "";
    SwapPointer(&a, &b);
    cout << "\nValue OF A&B: " << a << "," << b << "";
    SwapReference(a, b);
    cout << "\nValue OF A&B: " << a << "," << b << "";
    return 0;
}

void SwapPointer(int *p, int *q) {
    int temp = *p;
    *p = *q;
    *q = temp;
}

void SwapReference(int &p, int &q) {
    int temp = p;
    p = q;
    q = temp;
}
```

**Output:**
```
Value OF A&B: 21,14
Value OF A&B: 14,21
Value OF A&B: 21,14
```

### 5. Explain Inline Function and Its Use
Inline functions are functions that are expanded in line when they are invoked. The compiler replaces the function call with the function code itself to reduce the overhead of a function call.

**Example:**
```cpp
#include <iostream>
using namespace std;

inline int square(int x) {
    return x * x;
}

int main() {
    cout << "Square of 5: " << square(5) << endl;
    return 0;
}
```

**Output:**
```
Square of 5: 25
```

### 6. Static Variable in C++
A static variable retains its value between function calls and is shared by all instances of a class.

**Example:**
```cpp
#include <iostream>
using namespace std;

void counter() {
    static int count = 0; // Static variable
    count++;
    cout << "Count: " << count << endl;
}

int main() {
    counter(); // Outputs 1
    counter(); // Outputs 2
    counter(); // Outputs 3
    return 0;
}
```

**Output:**
```
Count: 1
Count: 2
Count: 3
```

### 7. Default Argument in Function Example
Default arguments are used when you want to provide a default value to function parameters.

**Example:**
```cpp
#include <iostream>
using namespace std;

void greet(string name = "Guest") {
    cout << "Hello, " << name << "!" << endl;
}

int main() {
    greet();           // Uses default argument
    greet("Alice");    // Overrides default argument
    return 0;
}
```

**Output:**
```
Hello, Guest!
Hello, Alice!
```

### 8. Recursion in C++
Recursion is a process in which a function calls itself directly or indirectly.

**Example:**
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n <= 1) {
        return 1; // Base case
    } else {
        return n * factorial(n - 1); // Recursive case
    }
}

int main() {
    int num = 5;
    cout << "Factorial of " << num << " is " << factorial(num) << endl;
    return 0;
}
```

**Output:**
```
Factorial of 5 is 120
```

These explanations, code snippets, and outputs should help you understand the concepts thoroughly.

---

# Q3. Explain Function Overloading with Suitable example

### Function Overloading in C++
Function overloading is a feature in C++ that allows you to have multiple functions with the same name but different parameters (either in number or type). The correct function to be called is determined by the arguments passed.

**Example:**

```cpp
#include <iostream>
using namespace std;

// Function to add two integers
int add(int a, int b) {
    return a + b;
}

// Overloaded function to add three integers
int add(int a, int b, int c) {
    return a + b + c;
}

// Overloaded function to add two doubles
double add(double a, double b) {
    return a + b;
}

int main() {
    // Calling the first add function
    int sum1 = add(5, 3);
    cout << "Sum of 5 and 3 (int): " << sum1 << endl;

    // Calling the second add function
    int sum2 = add(5, 3, 2);
    cout << "Sum of 5, 3 and 2 (int): " << sum2 << endl;

    // Calling the third add function
    double sum3 = add(5.5, 3.3);
    cout << "Sum of 5.5 and 3.3 (double): " << sum3 << endl;

    return 0;
}
```

**Output:**
```
Sum of 5 and 3 (int): 8
Sum of 5, 3 and 2 (int): 10
Sum of 5.5 and 3.3 (double): 8.8
```

### Explanation:
1. **First `add` Function:**
   - Parameters: Two integers (`int a`, `int b`)
   - Returns: Sum of the two integers.

2. **Second `add` Function:**
   - Parameters: Three integers (`int a`, `int b`, `int c`)
   - Returns: Sum of the three integers.

3. **Third `add` Function:**
   - Parameters: Two doubles (`double a`, `double b`)
   - Returns: Sum of the two doubles.

When you call `add(5, 3)`, the compiler matches it to the first `add` function because it has two integer arguments. Similarly, `add(5, 3, 2)` matches the second function, and `add(5.5, 3.3)` matches the third function. This is how function overloading works, allowing the same function name to be used for different purposes based on the parameter list.