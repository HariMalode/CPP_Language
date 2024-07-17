### More Info at 
https://en.cppreference.com/w/

# Q1.Explain
1. Tell about Cpp
2. Usage of Cpp
3. Varibles in cpp
4. Example of local and global variable
5. Datattypes: 1.Built In 2. User defined 3. Derived  (Write a common program , write all above in it)
6. Write a program take input and show and explain how to run it in terminal

### 1. Tell About C++
C++ is a high-level programming language developed by Bjarne Stroustrup as an extension of the C language. It provides object-oriented features and is widely used for system/software development, game development, drivers, client-server applications, and embedded firmware.

### 2. Usage of C++
- **System Programming:** C++ is used for developing operating systems, file systems, and other low-level systems.
- **Game Development:** Due to its high performance, C++ is used in game development.
- **GUI Applications:** C++ is used to develop GUI-based applications such as Adobe Systems applications.
- **Web Browsers:** Browsers like Google Chrome and Mozilla Firefox are built using C++.
- **Embedded Systems:** C++ is used in developing firmware for embedded systems.

### 3. Variables in C++
Variables are containers for storing data values. In C++, a variable must be declared before it can be used. Variable declaration specifies the name and type of the variable.

### 4. Example of Local and Global Variables
```cpp
#include <iostream>

// Global variable
int globalVar = 10;

void display() {
    // Local variable
    int localVar = 20;
    std::cout << "Local Variable: " << localVar << std::endl;
}

int main() {
    std::cout << "Global Variable: " << globalVar << std::endl;
    display();
    return 0;
}
```

### 5. Data Types in C++
C++ has three types of data types:
1. **Built-in (Primitive) Data Types:** int, char, float, double, bool
2. **User-defined Data Types:** struct, union, enum, class
3. **Derived Data Types:** array, pointer, function

### Common Program Demonstrating All Types

```cpp
#include <iostream>
using namespace std;

// User-defined data type
struct Person {
    string name;
    int age;
};

// Global variable
int globalVar = 100;

int main() {
    // Built-in data types
    int num = 10;
    char grade = 'A';
    float percentage = 85.6;
    double pi = 3.14159;
    bool isStudent = true;
    
    // Derived data type - array
    int arr[5] = {1, 2, 3, 4, 5};

    // User-defined data type
    Person person;
    person.name = "John";
    person.age = 25;

    // Local variable
    int localVar = 20;

    cout << "Built-in Data Types:" << endl;
    cout << "int: " << num << endl;
    cout << "char: " << grade << endl;
    cout << "float: " << percentage << endl;
    cout << "double: " << pi << endl;
    cout << "bool: " << isStudent << endl;

    cout << "Derived Data Type - Array:" << endl;
    for(int i = 0; i < 5; i++) {
        cout << "arr[" << i << "] = " << arr[i] << endl;
    }

    cout << "User-defined Data Type - Struct:" << endl;
    cout << "Name: " << person.name << endl;
    cout << "Age: " << person.age << endl;

    cout << "Global Variable: " << globalVar << endl;
    cout << "Local Variable: " << localVar << endl;

    return 0;
}
```

### 6. Write a Program, Take Input and Show How to Run it in Terminal
```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    cout << "Enter a number: ";
    cin >> num;
    cout << "You entered: " << num << endl;
    return 0;
}
```

### Running the Program in Terminal

1. **Save the Program:**
   Save the program in a file with a `.cpp` extension, e.g., `input.cpp`.

2. **Compile the Program:**
   Open the terminal and navigate to the directory where the file is saved. Compile the program using a C++ compiler like `g++`:
   ```sh
   g++ input.cpp -o input
   ```

3. **Run the Program:**
   Execute the compiled program:
   ```sh
   ./input
   ```

4. **Program Execution:**
   The program will prompt you to enter a number. After entering a number, it will display the entered value.


-----

 

# Q2. Explain
1. Headers in CPP and its use
2. Operators in CPP : 1. Arithmetic 2. Assignment 3. Comparison 4. Logical
3. Program - Access of global and local variable in main() having same name 
4. Example of Reference variable
5. Typecasting
6. Manipulator endl and setw with output
7. Conditional statements (if else and switches with example)
8. Loops in Cpp: forloop, while loop, do while loop

### 1. Headers in C++ and Their Use
Headers in C++ contain declarations of functions and macros. They provide the necessary interfaces for standard libraries or user-defined libraries, enabling the program to use those functions and macros without needing to write their definitions. Commonly used headers include:
- `<iostream>` for input and output operations.
- `<cmath>` for mathematical functions.
- `<string>` for string manipulation.
- `<vector>` for using the vector container.

### 2. Operators in C++
Operators are special symbols used to perform operations on variables and values. The major categories are:

1. **Arithmetic Operators:**
   - `+` (Addition)
   - `-` (Subtraction)
   - `*` (Multiplication)
   - `/` (Division)
   - `%` (Modulus)
   - `++` (Increment)
   - `--` (Decrement)

2. **Assignment Operators:**
   - `=` (Assignment)
   - `+=` (Addition assignment)
   - `-=` (Subtraction assignment)
   - `*=` (Multiplication assignment)
   - `/=` (Division assignment)
   - `%=` (Modulus assignment)

3. **Comparison Operators:**
   - `==` (Equal to)
   - `!=` (Not equal to)
   - `>` (Greater than)
   - `<` (Less than)
   - `>=` (Greater than or equal to)
   - `<=` (Less than or equal to)

4. **Logical Operators:**
   - `&&` (Logical AND)
   - `||` (Logical OR)
   - `!` (Logical NOT)

Here is a sample code demonstrating these operators:

```cpp
#include<iostream>
using namespace std;

int main() {
    int a = 9, b = 6;

    // Arithmetic Operators
    cout << "\n Addition: " << a + b;        // 15
    cout << "\n Sub: " << a - b;             // 3
    cout << "\n Mul: " << a * b;             // 54
    cout << "\n Div: " << (float)a / b;      // 1.5
    cout << "\n Modulus: " << a % b;         // 3

    cout << "\n____________INCR/DECR________________________";
    cout << "\n Value Of A: " << a;          // 9
    cout << "\n Pre Increment: " << ++a;     // 10 (a becomes 10)
    cout << "\n Value Of A: " << a;          // 10
    cout << "\n Post Increment: " << a++;    // 10 (a becomes 11 after this line)
    cout << "\n Value Of A: " << a;          // 11
    cout << "\n Pre Decrement: " << --a;     // 10 (a becomes 10)
    cout << "\n Value Of A: " << a;          // 10
    cout << "\n Post Decrement: " << a--;    // 10 (a becomes 9 after this line)
    cout << "\n Value Of A: " << a;          // 9

    cout << "\n____________COMPARISON________________________";
    a = 6;
    b = 9;
    cout << "True: 1 & False: 0";
    cout << "\n Value Of a == b: " << (a == b);  // 0
    cout << "\n Value Of a != b: " << (a != b);  // 1
    cout << "\n Value Of a > b: " << (a > b);    // 0
    cout << "\n Value Of a < b: " << (a < b);    // 1
    cout << "\n Value Of a >= b: " << (a >= b);  // 0
    cout << "\n Value Of a <= b: " << (a <= b);  // 1

    cout << "\nLogical";
    cout << "\n Value Of ((a == b) && (a > b)): " << ((a == b) && (a > b));  // 0
    cout << "\n Value Of ((a == b) && (a < b)): " << ((a == b) && (a < b));  // 0
    cout << "\n Value Of ((a == b) || (a > b)): " << ((a == b) || (a > b));  // 0
    cout << "\n Value Of ((a == b) || (a < b)): " << ((a == b) || (a < b));  // 1
    cout << "\n Value Of !((a == b) || (a < b)): " << !((a == b) || (a < b)); // 0

    return 0;
}
```

### 3. Program - Access of Global and Local Variable in main() Having Same Name
```cpp
#include<iostream>
using namespace std;

int c = 60;  // Global variable

int main() {
    int a, b, c;  // Local variable
    cout << "\n Enter A & B:";
    cin >> a >> b;
    c = a + b;  // Assign to local variable
    cout << "\n Local C is: " << c;
    cout << "\n Global C is: " << ::c;  // Access global variable using scope resolution operator

    return 0;
}
```

### 4. Example of Reference Variable
```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 10;
    int &ref = x;  // ref is a reference to x

    cout << "x: " << x << endl;    // Output: 10
    cout << "ref: " << ref << endl; // Output: 10

    ref = 20;  // Modifies x through the reference

    cout << "x: " << x << endl;    // Output: 20
    cout << "ref: " << ref << endl; // Output: 20

    return 0;
}
```

### 5. Typecasting
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 5, b = 2;
    float result;

    result = (float)a / b;  // Typecasting int to float

    cout << "Result: " << result << endl;  // Output: 2.5

    return 0;
}
```

### 6. Manipulator `endl` and `setw` with Output
```cpp
#include <iostream>
#include <iomanip>  // For setw
using namespace std;

int main() {
    cout << "Hello" << endl;  // Moves to the next line
    cout << "World" << endl;

    int width = 10;
    cout << setw(width) << "Right aligned" << endl;  // Output with width 10, right aligned
    cout << setw(width) << "123" << endl;

    return 0;
}
```

### 7. Conditional Statements

**if-else Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    cout << "Enter a number: ";
    cin >> num;

    if (num > 0) {
        cout << "Positive number" << endl;
    } else if (num < 0) {
        cout << "Negative number" << endl;
    } else {
        cout << "Zero" << endl;
    }

    return 0;
}
```

**switch Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int choice;
    cout << "Enter your choice (1-3): ";
    cin >> choice;

    switch (choice) {
        case 1:
            cout << "You chose option 1" << endl;
            break;
        case 2:
            cout << "You chose option 2" << endl;
            break;
        case 3:
            cout << "You chose option 3" << endl;
            break;
        default:
            cout << "Invalid choice" << endl;
            break;
    }

    return 0;
}
```

### 8. Loops in C++

**for loop:**
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; ++i) {
        cout << "Iteration: " << i << endl;
    }

    return 0;
}
```

**while loop:**
```cpp
#include <iostream>
using namespace std;

int main

```cpp
{
    int i = 1;
    while (i <= 5) {
        cout << "Iteration: " << i << endl;
        ++i;
    }

    return 0;
}
```

**do-while loop:** Runs at least once at any condition
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    do {
        cout << "Iteration: " << i << endl;
        ++i;
    } while (i <= 5);

    return 0;
}
```

These examples cover the various operators, variables, typecasting, conditional statements, and loops in C++. By understanding and practicing these concepts, you can gain a solid foundation in C++ programming.