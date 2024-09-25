# **C Programming for Embedded Systems (with Focus on Pointers)**

## 1. Pointer Basics and Arithmetic

**Pointers** in C are variables that store the address of another variable. They are essential in embedded systems for direct memory access, passing data efficiently, and working with hardware registers.

### Key Concepts:
- **Declaration:** `int *ptr;` declares a pointer to an integer.
- **Dereferencing:** Accessing the value at the address stored in the pointer (`*ptr`).
- **Pointer Arithmetic:** Allows manipulation of memory addresses (e.g., incrementing a pointer moves it to the next memory location based on the data type size).

### Example:
```c
int a = 10;
int *ptr = &a; // Pointer to variable 'a'

printf("Value of a: %d\n", *ptr); // Dereferencing pointer
```

#### Output:
```
Value of a: 10
```

---

## 2. Dynamic Memory Allocation (`malloc`, `calloc`, `free`)

Dynamic memory allocation allows for memory to be allocated at runtime using pointers. This is particularly useful in embedded systems with limited memory resources.

### Functions:
- **`malloc(size_t size)`**: Allocates a block of memory of the specified size.
- **`calloc(size_t nitems, size_t size)`**: Allocates memory for an array of `nitems`, initializes to zero.
- **`free(void *ptr)`**: Frees previously allocated memory.

### Example:
```c
int *arr;
arr = (int*) malloc(5 * sizeof(int)); // Allocate memory for an array of 5 integers
for (int i = 0; i < 5; i++) {
    arr[i] = i + 1;
}
free(arr); // Free the allocated memory
```

---

## 3. Pointer to Pointer and Arrays

Pointers to pointers are used in situations where multiple levels of indirection are required, such as in dynamic 2D array allocation. Arrays in C are closely related to pointers, with array names often being treated as pointers to their first element.

### Example of Pointer to Pointer:
```c
int x = 10;
int *p = &x;
int **pp = &p; // Pointer to pointer

printf("Value of x: %d\n", **pp); // Dereferencing pointer to pointer
```

#### Output:
```
Value of x: 10
```

### Pointer with Arrays:
```c
int arr[] = {1, 2, 3, 4};
int *ptr = arr;

for (int i = 0; i < 4; i++) {
    printf("%d ", *(ptr + i)); // Access array elements via pointer arithmetic
}
```

#### Output:
```
1 2 3 4
```

---

## 4. Function Pointers

**Function pointers** in C allow you to store the address of a function in a pointer and call the function via the pointer. This is useful in embedded systems for implementing callback functions or designing modular, flexible software.

### Example:
```c
#include <stdio.h>

void greet() {
    printf("Hello, World!\n");
}

int main() {
    void (*func_ptr)() = greet; // Declare function pointer
    func_ptr(); // Call function via pointer
    return 0;
}
```

#### Output:
```
Hello, World!
```

---

## 5. Structure Padding and Alignment

**Structure padding** occurs when the compiler adds extra memory between members of a structure to align data in memory. Alignment ensures that variables are stored in memory at addresses divisible by their size, optimizing access on the hardware.

### Example:
```c
struct Data {
    char a;
    int b;
    char c;
};

printf("Size of struct: %lu\n", sizeof(struct Data));
```

#### Output:
```
Size of struct: 12
```

Here, padding is added between members to align `int b` on a 4-byte boundary.

### Tip:
In embedded systems, use `#pragma pack(1)` or `__attribute__((packed))` to reduce memory wastage due to padding when needed.

---

## 6. Embedded C Concepts (Direct Memory Access, Interrupt Handling)

**Direct Memory Access (DMA)** and **interrupt handling** are crucial for efficient embedded systems design, allowing devices to transfer data directly to/from memory without CPU intervention, and respond to asynchronous events, respectively.

### DMA Concept:
- DMA allows peripheral devices to communicate directly with memory without burdening the CPU, improving efficiency.
  
### Interrupt Handling:
- Interrupts allow a microcontroller to pause its current task to handle an event (e.g., receiving data from a sensor).

```c
void __interrupt() ISR() {
    // Interrupt Service Routine for handling an interrupt
    // triggered by hardware event
}
```

### Tip:
Efficient handling of interrupts and DMA is essential for time-critical embedded systems like real-time sensors or motor control.

---

## 7. Memory Management in C for Embedded Systems

Memory management is crucial in embedded systems with limited resources. This involves managing both stack (local variables) and heap (dynamically allocated memory) effectively.

### Key Concepts:
- **Stack**: Automatically managed memory for local variables; fast but limited.
- **Heap**: Dynamically managed memory; allows flexibility but requires careful use (`malloc`/`free`).

### Example of Stack and Heap:
```c
void func() {
    int x = 10;  // Allocated on stack
    int *ptr = (int*) malloc(sizeof(int));  // Allocated on heap
    *ptr = 20;
    free(ptr);  // Freeing heap memory
}
```

---

## Conclusion

Mastering **pointers** and their associated concepts in C is crucial for embedded systems development. Pointers enable efficient memory access, dynamic memory management, and provide a deeper understanding of how embedded systems interact with hardware. Understanding these concepts will give you the tools needed to design and optimize embedded applications in a resource-constrained environment.
