# Primitive Data Types [6.2]

## Numeric Types:

- **Integer**: Fixed-point numbers supported in multiple sizes (e.g., `int`, `long`).
- **Floating-point**: Approximations of real numbers.

```c
int num = 42;  
float pi = 3.14f;
```

## Boolean Types:

- Represent `true`/`false` values.

```c
bool isOn = true;
```

## Character Types:

- Used for single characters or strings.

```c
char ch = 'A';
```

---

# Character String Types [6.3]

## Design Issues:

- Should strings be a special kind of character array or a primitive type?
- Should strings have static or dynamic length?

## Common Operations of Strings:

1. **Assignment**: Copying one string to another.
2. **Concatenation**: Combining two strings into one.
3. **Substring Reference**: Accessing a part of a string.
4. **Comparison**: Lexicographic comparison of strings.
5. **Pattern Matching**: Finding matches based on defined patterns (e.g., regular expressions).

## String Length Options:

1. **Static Length Strings**: Fixed length at compile-time.
2. **Limited Dynamic Length Strings**: Varying up to a maximum limit.
3. **Dynamic Length Strings**: No fixed maximum limit.

## Evaluation:

1. **Writability**: String types improve simplicity and reduce errors in code. Libraries for string handling (e.g., C standard string library) are helpful but prone to security issues (e.g., buffer overflow in `strcpy`).
2. **Cost and Complexity**: Adding primitive string types has minimal impact on language or compiler complexity.

## Implementation:

1. **Static Length String (Python):**
   ```python
   static_string = "Hello, World!"
   print(f"Static String: {static_string}")
   ```
2. **Limited Dynamic Length String (C):**
   ```c
   #include <stdio.h>
   #include <string.h>

   int main() {
       char str[20];
       strcpy(str, "Hello");
       printf("String: %s\n", str);
       return 0;
   }
   ```
3. **Dynamic Length String (C++):**
   ```cpp
   #include <iostream>
   #include <string>

   int main() {
       std::string dynamicStr = "Hello";
       dynamicStr += ", World!";
       std::cout << "Dynamic String: " << dynamicStr << std::endl;
       return 0;
   }
   ```
4. **Dynamic Allocation (Java):**
   ```java
   public class Main {
       public static void main(String[] args) {
           String dynamicStr = "Hello";
           dynamicStr += ", World!";
           System.out.println("Dynamic String: " + dynamicStr);
       }
   }
   ```

---

# Enumeration Types [6.4]

## Design Issues:

- Is an enumeration constant allowed to appear in more than one type definition, and if so, how is the type of an occurrence of that constant in the program checked?
- Are enumeration values coerced to integers?
- Are any other types coerced to an enumeration type?

## Implementation Example:

```cpp
enum Color { Red, Green, Blue };
Color c = Green;
```

## Evaluation:

1. **Readability**: Named constants (e.g., `Red`, `Blue`) are more meaningful than numeric literals (e.g., `0`, `1`).
2. **Reliability**: Modern implementations prevent unintended operations (e.g., arithmetic), and type-checking ensures validity.

---

# Array Types [6.5]

## Design Issues:

- What types are legal for subscripts?
- Are subscripting expressions in element references range-checked?
- When are subscript ranges bound?
- When does array allocation take place?
- Are ragged or rectangular multidimensioned arrays allowed, or both?
- Can arrays be initialized when they have their storage allocated?
- What kinds of slices are allowed, if any?

## Subscript Bindings:

- **Static**: Subscript range fixed at compile-time.
- **Dynamic**: Subscript range changes during execution.

## Array Categories:

1. **Static Arrays**: Fixed subscript ranges and allocated before runtime.

```c
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    printf("First element: %d\n", arr[0]);
    return 0;
}
```
2. **Fixed Stack-Dynamic Arrays**: Allocated at declaration elaboration time during execution.

```c
#include <stdio.h>

void printArray(int n) {
    int arr[n];
    for (int i = 0; i < n; i++) {
        arr[i] = i * 10;
    }
    printf("Last element: %d\n", arr[n-1]);
}

int main() {
    printArray(5);
    return 0;
}
```

3. **Fixed Heap-Dynamic Arrays**: Allocated at runtime using heap memory.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> arr = {1, 2, 3, 4, 5};
    std::cout << "First element: " << arr[0] << std::endl;
    return 0;
}
```

4. **Heap-Dynamic Arrays**: Fully dynamic subscript ranges and allocation during execution.

```cpp
#include <iostream>

int main() {
    int size;
    std::cout << "Enter size: ";
    std::cin >> size;

    int* arr = new int[size];
    for (int i = 0; i < size; i++) arr[i] = i * 2;

    std::cout << "Last element: " << arr[size-1] << std::endl;
    delete[] arr;
    return 0;
}
```

---

# Record Types [6.7]

## Design Issues:

- What is the syntactic form of references to fields?
- Are elliptical references allowed?

## Implementation:

```cpp
#include <iostream>

struct Person {
    std::string name;
    int age;
};

int main() {
    Person person = {"Jane", 30};
    std::cout << "Name: " << person.name << ", Age: " << person.age << std::endl;
    return 0;
}
```

## Evaluation:

- **Readability and Writability**: Descriptive field names simplify understanding and use.
- **Reliability**: Type safety ensures predictable and robust behavior.

---

# Union Types [6.10]

## Design Issues:

- Should unions support type safety?
- How is memory shared among fields?

## Implementation Example:

```c
union Data {
    int i;
    float f;
};

int main() {
    union Data d;
    d.i = 10;
    printf("Union integer value: %d\n", d.i);
    return 0;
}
```

## Evaluation:

- **Memory-efficient**: Reduces cost by reusing memory.
- **Potentially Unsafe**: Harder to manage, leading to unintended behavior.

---

# Pointers [6.11]

## Design Issues:

- How are dangling pointers and memory leaks handled?
- Should pointers be used for array indexing?

## Implementation in C:

```c
#include <stdio.h>

int main() {
    int x = 10;
    int *p = &x;
    printf("Value: %d\n", *p);
    return 0;
}
```

## Implementation in C++:

```cpp
#include <iostream>

int main() {
    int x = 20;
    int &ref = x;
    std::cout << "Reference Value: " << ref << std::endl;
    return 0;
}
```

