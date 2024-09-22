# Explain 
1. Explain CPP template in cpp also Explain Why Templates
2. Provide Program of Without template and With Template
3. Explain Templates With multiple parameters with program
4. Explain Templates With default parameters with program
5. Explain Function Templates With parameters with program

### 1. **C++ Templates**

A **template** in C++ is a powerful feature that allows you to write generic code that can work with any data type. Instead of writing different code for different data types (like `int`, `float`, etc.), templates enable a function or class to operate with generic types. This is useful in scenarios where the logic is the same but the data type changes.

#### Why Templates?

- **Code Reusability**: You don't need to write the same logic multiple times for different data types.
- **Type Safety**: Unlike using `void*` or typecasting, templates ensure type safety during compile time.
- **Maintainability**: Easier to maintain because only one version of the function or class is required.
- **Performance**: Since templates are expanded at compile-time, they don’t incur runtime overhead (inlined functions).

### 2. **Program: Without Template and With Template**

#### Program Without Template:
You need to write separate functions for each data type, which can lead to redundancy.

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

int main() {
    cout << "Sum of integers: " << add(5, 10) << endl;
    cout << "Sum of doubles: " << add(5.5, 10.5) << endl;
    return 0;
}
```

#### Program With Template:
With templates, you can write one generic function for multiple data types.

```cpp
#include <iostream>
using namespace std;

template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << "Sum of integers: " << add(5, 10) << endl;
    cout << "Sum of doubles: " << add(5.5, 10.5) << endl;
    return 0;
}
```

### 3. **Templates with Multiple Parameters**

You can use multiple template parameters by specifying multiple `typename` or `class` keywords. This allows you to create functions or classes that work with different types simultaneously.

#### Example: Template with Multiple Parameters

```cpp
#include <iostream>
using namespace std;

template <typename T1, typename T2>
void display(T1 a, T2 b) {
    cout << "First parameter: " << a << endl;
    cout << "Second parameter: " << b << endl;
}

int main() {
    display(5, 10.5);         // int, double
    display('A', "Hello");    // char, string
    return 0;
}
```

Here, `T1` and `T2` are two different template parameters, allowing `display()` to work with multiple types.

### 4. **Templates with Default Parameters**

You can also provide default values to template parameters, similar to function default arguments.

#### Example: Template with Default Parameters

```cpp
#include <iostream>
using namespace std;

template <typename T1 = int, typename T2 = double>
void display(T1 a = 10, T2 b = 20.5) {
    cout << "First parameter: " << a << endl;
    cout << "Second parameter: " << b << endl;
}

int main() {
    display();               // Uses default parameters
    display(5);              // First parameter specified, second uses default
    display(5, 10.1);        // Both parameters specified
    return 0;
}
```

In this example, if you don't pass any arguments, the template uses the default types (`int` and `double`) and default values (`10` and `20.5`).

### 5. **Function Templates with Parameters**

Function templates can also accept additional arguments, just like regular functions. Template parameters are used for the types, and the remaining arguments are regular function parameters.

#### Example: Function Template with Parameters

```cpp
#include <iostream>
using namespace std;

template <typename T>
T maxValue(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    cout << "Max of 5 and 10: " << maxValue(5, 10) << endl;         // int
    cout << "Max of 3.5 and 2.1: " << maxValue(3.5, 2.1) << endl;   // double
    return 0;
}
```

In this example, `maxValue()` is a function template that accepts two parameters of the same type (`T`). The function returns the larger of the two.

### Summary:

- **Why Templates**: They allow code reusability, maintainability, and type safety while avoiding redundancy.
- **Without Template vs With Template**: Without templates, you need separate functions for each type, while templates enable you to create one function for all types.
- **Templates with Multiple Parameters**: Allow you to handle more than one type at a time in the same function or class.
- **Templates with Default Parameters**: Allow you to provide default types and values to template parameters.
- **Function Templates with Parameters**: Allows you to create generic functions that accept additional parameters.


---

# Explain
1. Explain Member function Templates & Overloading template function
2. Explain Standard Template Library( STL) with containers, algorithm and Iterators
3. Explain types of container in cpp,  Sequence,Associative and derived
4. Explain Vector in Cpp with program
5. Explain use of Iterator with program


### 1. **Member Function Templates & Overloading Template Functions**

#### **Member Function Templates**
A member function template is a template function defined inside a class, meaning that the class does not need to be a template itself, but one or more of its member functions can be templates.

##### Example:
```cpp
#include <iostream>
using namespace std;

class MyClass {
public:
    // Member function template
    template <typename T>
    void display(T value) {
        cout << "Value: " << value << endl;
    }
};

int main() {
    MyClass obj;
    obj.display(10);         // Calls display<int>
    obj.display(10.5);       // Calls display<double>
    obj.display("Hello");    // Calls display<const char*>
    return 0;
}
```

In this example, the `display` function is a template, but the class `MyClass` itself is not templated.

#### **Overloading Template Functions**
You can overload template functions by providing multiple versions of the same function, either templated or non-templated.

##### Example:
```cpp
#include <iostream>
using namespace std;

// Function template
template <typename T>
void print(T value) {
    cout << "Template function: " << value << endl;
}

// Overloaded non-template function
void print(int value) {
    cout << "Non-template function: " << value << endl;
}

int main() {
    print(10);         // Calls non-template version (since exact match)
    print(10.5);       // Calls template version
    return 0;
}
```

In this example, when `print(10)` is called, it prefers the non-template version as it is an exact match. For `print(10.5)`, the template function is called since there is no non-template version for `double`.

---

### 2. **Standard Template Library (STL)**

The **Standard Template Library (STL)** is a powerful library in C++ that provides generic classes and functions to implement common data structures and algorithms. It is built around three main components:

1. **Containers**: Structures used to hold collections of data.
2. **Algorithms**: Functions used to perform operations on containers like searching, sorting, etc.
3. **Iterators**: Objects that act as a pointer to access elements of a container.

#### **Containers**
Containers in STL store collections of objects. The most common types of containers are:
- **Sequence containers**: Vectors, Lists, Deques, Arrays.
- **Associative containers**: Set, Multiset, Map, Multimap.
- **Derived containers**: Stack, Queue, Priority Queue.

#### **Algorithms**
STL provides many built-in algorithms like `sort()`, `find()`, `count()`, etc., that operate on containers.

#### **Iterators**
Iterators are used to point to elements of containers. They provide a way to access and traverse the elements in a container.

---

### 3. **Types of Containers in C++**

#### **Sequence Containers**
- **Vector**: Dynamic array, which can grow in size.
- **List**: Doubly linked list.
- **Deque**: Double-ended queue, allowing fast insertion/removal from both ends.

#### **Associative Containers**
- **Set**: Stores unique elements in sorted order.
- **Map**: Stores key-value pairs, where keys are unique and sorted.
- **Multiset/Multimap**: Similar to Set/Map but allows duplicate keys.

#### **Derived Containers**
- **Stack**: LIFO (Last-In-First-Out) structure.
- **Queue**: FIFO (First-In-First-Out) structure.
- **Priority Queue**: Elements are stored based on priority, not insertion order.

---

### 4. **Vector in C++**

A `vector` is a dynamic array in C++ that can grow or shrink in size. Vectors provide random access to elements and allow fast insertion/removal at the end of the sequence.

#### Example Program:
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;  // Declare a vector of integers

    // Adding elements to the vector
    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    // Accessing elements using a loop
    for (int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";  // Random access using index
    }
    cout << endl;

    // Removing the last element
    v.pop_back();

    // Displaying elements after pop_back()
    for (int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    cout << endl;

    return 0;
}
```

In this example:
- `push_back()` adds elements to the end of the vector.
- `pop_back()` removes the last element.
- `v[i]` allows random access to elements using the index.

---

### 5. **Use of Iterator in C++**

Iterators are used to traverse elements in a container like a vector, list, etc. They act as pointers to elements in the container.

#### Example Program with Iterator:
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};  // Initializing a vector

    // Declare an iterator for the vector
    vector<int>::iterator it;

    // Traverse the vector using iterator
    for (it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";  // Dereference iterator to get value
    }
    cout << endl;

    return 0;
}
```

In this example:
- `v.begin()` returns an iterator pointing to the first element of the vector.
- `v.end()` returns an iterator pointing to the position after the last element.
- `*it` dereferences the iterator to access the element.

---

### Summary:
1. **Member Function Templates** allow functions within a class to be templated, enabling them to work with various types. Overloading template functions allows multiple versions of a function to exist for different types.
2. **STL** provides containers, algorithms, and iterators to work with collections of data efficiently.
3. **Containers** are categorized into **sequence**, **associative**, and **derived containers**, each serving different purposes in data handling.
4. **Vector** is a dynamic array that supports random access and efficient resizing.
5. **Iterators** are used to access elements of containers, behaving like pointers to facilitate traversal.


----

# Explain
1. Explain Iterator use without for loop (use it++ to iterate)
2. Provide some important modifies like push_back, pop_back, remove etc
3. Explain List in Cpp and What makes a list different from an array
4. Provide a program of list. Inserting in list using iterator
5. Explain Map in CPP STL with program

### 1. **Iterator Use Without `for` Loop**

You can use iterators outside of a `for` loop to traverse containers using manual iteration. Using `it++`, you can manually move through elements of a container like `vector`, `list`, or `map`.

#### Example: Iterating with `it++`
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30, 40, 50};

    vector<int>::iterator it = v.begin();  // Iterator pointing to the first element

    // Iterating manually using it++
    cout << *it << endl;  // First element
    it++;  // Move to the next element
    cout << *it << endl;  // Second element
    it++;  // Move to the third element
    cout << *it << endl;

    return 0;
}
```

In this example, `it++` is used to manually move to the next element in the `vector`.

---

### 2. **Important Modifiers in STL Containers**

Here are some important modifiers that apply to various STL containers like `vector`, `list`, etc.:

- **`push_back()`**: Adds an element to the end of the container.
    ```cpp
    v.push_back(10);
    ```

- **`pop_back()`**: Removes the last element of the container.
    ```cpp
    v.pop_back();
    ```

- **`insert()`**: Inserts an element at a specific position (iterator).
    ```cpp
    v.insert(it, 25);  // Insert 25 at position pointed by iterator
    ```

- **`erase()`**: Removes an element or a range of elements.
    ```cpp
    v.erase(it);  // Removes the element at position pointed by iterator
    ```

- **`clear()`**: Removes all elements from the container.
    ```cpp
    v.clear();
    ```

- **`remove()`**: Removes all instances of a particular value in `list` (works with `list` specifically).
    ```cpp
    l.remove(30);  // Removes all elements with the value 30 in a list
    ```

---

### 3. **List in C++ and Difference from Array**

A **`list`** in C++ is a doubly linked list, meaning each element is linked to both the previous and the next element. This makes it efficient for insertions and deletions anywhere in the list. However, unlike arrays or vectors, lists do not provide direct access to elements using an index (random access).

#### Differences Between `list` and `array`:
- **Memory Structure**:
  - `list`: Uses a linked list structure, where each element points to the next and previous elements.
  - `array`: Contiguous memory allocation.
  
- **Insertion/Deletion**:
  - `list`: Efficient insertion and deletion at any point (O(1) at the beginning and middle).
  - `array`: Inserting or deleting in the middle requires shifting elements (O(n)).

- **Access**:
  - `list`: No direct access using an index, must use iterators.
  - `array`: Allows random access to elements using indexing (`arr[i]`).

---

### 4. **Program: Inserting in a List Using an Iterator**

You can insert elements in a `list` using the `insert()` function with iterators.

#### Example Program:
```cpp
#include <iostream>
#include <list>
using namespace std;

int main() {
    list<int> l = {10, 20, 30, 40};

    list<int>::iterator it = l.begin();
    advance(it, 2);  // Move iterator to the 3rd element

    l.insert(it, 25);  // Insert 25 before the 3rd element

    // Displaying list using iterator
    for (it = l.begin(); it != l.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

In this program, we use `advance()` to move the iterator to the desired position and then insert a new element using `insert()`.

---

### 5. **Map in C++ STL**

A **`map`** in C++ STL is an associative container that stores elements in key-value pairs. The keys are unique, and each key is associated with only one value. Maps are implemented as balanced binary trees, meaning they are sorted by keys and allow fast lookup, insertion, and deletion (O(log n)).

#### Key Features of `map`:
- **Unique Keys**: Every key must be unique.
- **Sorted**: Keys are stored in sorted order.
- **Key-Value Pair**: Each element is a combination of a key and a value (`pair`).

#### Example Program:
```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    // Declare a map
    map<int, string> myMap;

    // Insert key-value pairs into the map
    myMap[1] = "Apple";
    myMap[2] = "Banana";
    myMap[3] = "Cherry";

    // Display the map using an iterator
    map<int, string>::iterator it;
    for (it = myMap.begin(); it != myMap.end(); ++it) {
        cout << "Key: " << it->first << ", Value: " << it->second << endl;
    }

    // Accessing a specific element
    cout << "Value with key 2: " << myMap[2] << endl;

    return 0;
}
```

In this example:
- `myMap[1] = "Apple";` inserts the key-value pair `1: "Apple"` into the map.
- `it->first` gives the key, and `it->second` gives the corresponding value.
