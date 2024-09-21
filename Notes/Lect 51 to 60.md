# Explain
1. Explain Pointer to Object in CPP
2. Explain Array of objects using pointers in cpp
3. Explain 'this' pointer in cpp

### 1. **Pointer to Object in C++ with Arrow operator**

A pointer to an object is similar to a pointer to any data type, but it points to a memory address where the object resides. This allows you to access the members of the object using the pointer.

#### Example:
```cpp
#include <iostream>
using namespace std;

class Box {
    public:
        int length;
        void setLength(int len) {
            length = len;
        }
        void displayLength() {
            cout << "Length: " << length << endl;
        }
};

int main() {
    Box box1;             // Creating an object of class Box
    Box* ptr;             // Pointer to Box object
    ptr = &box1;          // Storing address of box1 in pointer ptr
    
    // Accessing members using pointer
    ptr->setLength(10);   // Use -> to access members via a pointer
    ptr->displayLength(); // Output: Length: 10

    //New Way
    Box *newptr = new Box;
    // (*newptr).setLength(11);
    newptr->setLength(11);
    newptr->displayLength();

    return 0;
}
```
In this example, `ptr` is a pointer to an object of type `Box`. The arrow operator (`->`) is used to access members of the class through the pointer.

---

### 2. **Array of Objects Using Pointers in C++**

You can create an array of objects using pointers, which allows you to dynamically allocate memory and manage multiple objects at runtime.

#### Example:
```cpp
#include <iostream>
using namespace std;

class Box {
    public:
        int length;
        void setLength(int len) {
            length = len;
        }
        void displayLength() {
            cout << "Length: " << length << endl;
        }
};

int main() {
    int size = 3
    Box* boxes = new Box[size];  // Dynamically allocate an array of 3 Box objects

    // Accessing and setting values using pointers
    for(int i = 0; i < size; i++) {
        boxes[i].setLength((i + 1) * 10);  // Setting length for each object
    }

    // Displaying values
    for(int i = 0; i < size; i++) {
        boxes[i].displayLength();
    }

    delete[] boxes;  // Free the allocated memory

    return 0;
}
```

In this example, an array of `Box` objects is created using dynamic memory allocation (`new`). The objects are accessed and modified using the pointer `boxes`.

**Using Pointer Iterator:**
```

int main() {
    int size = 3;
    Box* boxes = new Box[size];  // Dynamically allocate an array of 3 Box objects
    Box* ptr = boxes;            // Pointer to iterate through the array

    // Accessing and setting values using pointer increment
    for(int i = 0; i < size; i++) {
        ptr->setLength((i + 1) * 10);  // Set length for each object
        ptr++;                         // Move to the next object
    }

    ptr = boxes;  // Reset pointer to the beginning of the array

    // Displaying values using pointer increment
    for(int i = 0; i < size; i++) {
        ptr->displayLength();  // Display length of each object
        ptr++;                 // Move to the next object
    }

    delete[] boxes;  // Free the allocated memory

    return 0;
}
```

### Explanation:
- `ptr->setLength()` is used to access the members of the object, and after setting the length for each object, `ptr++` moves the pointer to the next object in the array.
- The same process is followed when displaying the values. After each `displayLength()` call, the pointer is incremented to move to the next object.
- Finally, `ptr` is reset to `boxes` to start again from the beginning of the array when displaying the values.


---

### 3. **`this` Pointer in C++**

The `this` pointer is a hidden pointer passed to all non-static member functions. It points to the current object of the class. It is used when you want to refer to the current instance of the class from within a member function.

#### Example:
```cpp
#include <iostream>
using namespace std;

class Box {
    public:
        int length;
        Box(int length) {
            this->length = length;  // Using 'this' pointer to distinguish the instance variable
        }
        void displayLength() {
            cout << "Length: " << this->length << endl;  // Access current object's member
        }
};

int main() {
    Box box1(20);       // Creating an object with length 20
    box1.displayLength();  // Output: Length: 20

    return 0;
}
```
In this example, the `this` pointer is used to refer to the member variable `length` of the current object when there is a conflict between local and instance variables (both named `length`). The `this` pointer points to the object that calls the member function.


---
# Explain
1. Explain Polymorphism with types in  in detail
2. Explain Pointer to derived class with example
3. Explain Virtual Function and its use
4. Explain Pure Virtual Function and Abstract base class in cpp


### 1. **Polymorphism in C++**

**Polymorphism** means the ability to take many forms. In C++, it allows functions or objects to behave in different ways based on their input or class type. Polymorphism in C++ is primarily divided into two types:
- **Compile-time Polymorphism (Static Binding)**: Achieved through function overloading and operator overloading.
- **Runtime Polymorphism (Dynamic Binding)**: Achieved through inheritance and virtual functions.

#### Types of Polymorphism:

**a. Compile-time Polymorphism (Static Polymorphism):**
   - **Function Overloading**: Same function name with different parameter types.
   - **Operator Overloading**: Custom behavior for operators when applied to objects of a user-defined class.

   **Example: Function Overloading**
   ```cpp
   #include <iostream>
   using namespace std;

   class Print {
       public:
           void display(int i) {
               cout << "Integer: " << i << endl;
           }
           void display(double f) {
               cout << "Float: " << f << endl;
           }
           void display(string s) {
               cout << "String: " << s << endl;
           }
   };

   int main() {
       Print obj;
       obj.display(5);        // Integer
       obj.display(3.14);     // Float
       obj.display("Hello");  // String
       return 0;
   }
   ```

**b. Runtime Polymorphism (Dynamic Polymorphism):**
   - Achieved via **inheritance** and **virtual functions**. It allows a derived class to override a base class function. Function resolution is done at runtime based on the object type.

   **Example: Virtual Function (Runtime Polymorphism)**
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
       Base* basePtr;
       Derived derivedObj;

       basePtr = &derivedObj;
       basePtr->show();  // Output: Derived class (runtime polymorphism)

       return 0;
   }
   ```

---

### 2. **Pointer to Derived Class**

A pointer to a derived class can access members of both the base and derived classes. However, a pointer to a base class cannot directly access members of the derived class unless the member is defined as `virtual` in the base class.

#### Example:
```cpp
#include <iostream>
using namespace std;

class Base {
    public:
        void showBase() {
            cout << "Base class method" << endl;
        }
};

class Derived : public Base {
    public:
        void showDerived() {
            cout << "Derived class method" << endl;
        }
};

int main() {
    Base* basePtr;       // Base class pointer
    Derived derivedObj;  // Derived class object

    basePtr = &derivedObj;   // Base class pointer pointing to derived class object

    basePtr->showBase();  // Works: Calls base class method
    // basePtr->showDerived();  // Error: Base class pointer cannot access derived class methods

    Derived* derivedPtr = &derivedObj;  // Derived class pointer pointing to derived object
    derivedPtr->showBase();             // Works: Calls base class method
    derivedPtr->showDerived();          // Works: Calls derived class method

    return 0;
}
```

In this example, the base class pointer (`basePtr`) can only call base class methods, even though it's pointing to a derived class object.

---

### 3. **Virtual Function**

A **virtual function** is a function in a base class that you expect to be overridden in derived classes. It allows for **runtime polymorphism**, meaning the function that gets called is determined by the type of the object pointed to by a base class pointer, not by the type of the pointer itself.

#### Use of Virtual Functions:
- Allows derived classes to provide their own implementations of functions.
- Supports polymorphism where different classes can implement the same interface differently.

#### Example:
```cpp
#include <iostream>
using namespace std;

class Base {
    public:
        virtual void show() {  // Virtual function
            cout << "Base class" << endl;
        }
};

class Derived : public Base {
    public:
        void show() override {  // Override in derived class
            cout << "Derived class" << endl;
        }
};

int main() {
    Base* basePtr;
    Derived derivedObj;

    basePtr = &derivedObj;
    basePtr->show();  // Output: Derived class (due to virtual function)

    return 0;
}
```

Here, `show()` is a virtual function in the base class, and it is overridden in the derived class. When `basePtr` points to `derivedObj`, it calls the derived class version of `show()`.

---

### 4. **Pure Virtual Function and Abstract Base Class**

A **pure virtual function** is a function that has no implementation in the base class and must be overridden in any derived class. A class containing at least one pure virtual function becomes an **abstract base class**, and you cannot instantiate objects of this class directly. It is used to define a common interface for derived classes.

#### Syntax of Pure Virtual Function:
```cpp
virtual void functionName() = 0;
```

#### Example:
```cpp
#include <iostream>
using namespace std;

class Shape {
    public:
        virtual void draw() = 0;  // Pure virtual function, making Shape an abstract class
};

class Circle : public Shape {
    public:
        void draw() override {
            cout << "Drawing Circle" << endl;
        }
};

class Square : public Shape {
    public:
        void draw() override {
            cout << "Drawing Square" << endl;
        }
};

int main() {
    Shape* shape1 = new Circle();
    Shape* shape2 = new Square();

    shape1->draw();  // Output: Drawing Circle
    shape2->draw();  // Output: Drawing Square

    delete shape1;
    delete shape2;

    return 0;
}
```

#### Explanation:
- `Shape` is an abstract class because it has a pure virtual function `draw()`.
- Derived classes like `Circle` and `Square` must override the `draw()` function.
- You cannot instantiate `Shape` directly, but you can use it to reference objects of derived classes, allowing for runtime polymorphism.

---

# Explain
1. Explain File I/O in cpp
2. Explain File Reading and Writing with example
3. Explain some function like eof()


### 1. **File I/O in C++**

File I/O (Input/Output) in C++ allows a program to store data permanently on a disk and retrieve it later. C++ provides file handling through the **fstream** library, which includes three main classes:

- **ifstream**: Used for reading from a file (input stream).
- **ofstream**: Used for writing to a file (output stream).
- **fstream**: Used for both reading from and writing to a file.

#### File Modes:
While opening files, you can specify different file modes:
- `ios::in`: Open for reading.
- `ios::out`: Open for writing.
- `ios::app`: Append to the end of the file.
- `ios::ate`: Open a file for output and move the file pointer to the end.
- `ios::trunc`: If the file exists, truncate its content before opening.
- `ios::binary`: Open in binary mode.

#### Example of File Opening:
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream outFile;             // Create object for writing to a file
    outFile.open("example.txt");  // Open a file for writing
    if (!outFile) {
        cout << "File not opened!" << endl;
        return 1;
    }
    outFile << "Hello, World!" << endl;  // Write to the file
    outFile.close();                     // Close the file

    return 0;
}
```

In this example, `ofstream` is used to write data to a file named `example.txt`.

---

### 2. **File Reading and Writing with Example**

#### Writing to a File:
We can write data into a file using the `ofstream` class.

#### Example: Writing to a File
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream outFile("output.txt");  // Create and open a file for writing
    if (!outFile) {
        cout << "Error opening file for writing!" << endl;
        return 1;
    }

    // Writing data to the file
    outFile << "This is line 1" << endl;
    outFile << "This is line 2" << endl;

    outFile.close();  // Close the file after writing
    cout << "Data written to file successfully." << endl;

    return 0;
}
```

In this example:
- The `ofstream` object `outFile` is used to write data to `output.txt`.
- `outFile <<` writes text into the file.
- The `close()` function closes the file after the operation.

#### Reading from a File:
We can read data from a file using the `ifstream` class.

#### Example: Reading from a File
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    ifstream inFile("output.txt");  // Open file for reading
    if (!inFile) {
        cout << "Error opening file for reading!" << endl;
        return 1;
    }

    string line;
    // Reading data line by line
    while (getline(inFile, line)) {
        cout << line << endl;  // Display each line read from the file
    }

    inFile.close();  // Close the file after reading
    return 0;
}
```

In this example:
- The `ifstream` object `inFile` is used to read data from `output.txt`.
- `getline()` is used to read each line from the file until the end.
- The `close()` function is used to close the file after reading.

#### Example: Reading and Writing Using `fstream`
`fstream` can be used for both reading and writing in a file.

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    fstream file;  // Declare fstream object

    // Writing to file
    file.open("data.txt", ios::out);  // Open file for writing
    if (!file) {
        cout << "File not created!" << endl;
        return 1;
    }
    file << "C++ File I/O Example" << endl;
    file << "Writing and reading from file using fstream." << endl;
    file.close();

    // Reading from file
    file.open("data.txt", ios::in);  // Open file for reading
    if (!file) {
        cout << "File not found!" << endl;
        return 1;
    }

    string line;
    while (getline(file, line)) {
        cout << line << endl;  // Display content line by line
    }
    file.close();

    return 0;
}
```

### Key Points:
- **File Modes**: Use `ios::in`, `ios::out`, `ios::app`, etc., to control file operations.
- Always check if a file was opened successfully by checking the file stream object (`if (!file)`).
- Always close a file after reading or writing to release system resources.


### EOF

In C++, several useful functions are provided for handling file operations, particularly when using file streams such as `ifstream`, `ofstream`, and `fstream`. These functions help in managing input/output operations effectively. Below are some of the commonly used functions in file handling:

### 1. **eof()**

The `eof()` function is used to check if the end of the file has been reached. It returns `true` if the end of the file has been reached, otherwise it returns `false`.

#### Syntax:
```cpp
bool eof();
```

#### Example:
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ifstream file("example.txt");

    if (!file) {
        cout << "Error opening file!" << endl;
        return 1;
    }

    char ch;
    while (!file.eof()) {  // Check for the end of file
        file.get(ch);       // Read character by character
        cout << ch;
    }

    file.close();
    return 0;
}
```

In this example, `file.eof()` checks if the end of the file has been reached while reading each character from the file.

---
