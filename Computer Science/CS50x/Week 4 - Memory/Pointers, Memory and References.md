 ---
## 1. **Pointers & References**

- A **pointer** is a variable that stores the **address** of another variable.
 
- Operators:
 
 - `&` → “address of” operator.

 - `*` → “dereference” operator (go to the address).
  
- In C, references (like in C++) don’t exist — instead we simulate them with pointers.
 

```c
int n = 50;
int *p = &n; // p stores address of n
printf("%p\n", p); // prints address
printf("%d\n", *p);// dereference → 50
```

---

## 2. **Memory**

- Computer memory is made of **bytes**, each with an **address** (usually shown in **hexadecimal**).
 
- Memory layout:
 
 - **Code segment** → program instructions.
  
 - **Global/Static** → global variables.
  
 - **Heap** → dynamic memory (`malloc`).
  
 - **Stack** → local variables, function calls.
  
- Important: addresses are big numbers (often printed with `%p`).
 

---

## 3. **Strings**

- Strings are just arrays of `char` ending with a **null terminator `\0`**.
 
- In C, `string` is not a real type — it’s just `char *`.
 
- Printing a string works because `printf("%s")` starts at the first character’s address and keeps going until `\0`.
 

```c
char *s = "HI!";
printf("%s\n", s); // HI!

// Show addresses
printf("%p\n", s);  // address of 'H'
printf("%p\n", &s[1]); // address of 'I'
```

---

## 4. **Pointer Arithmetic**

- Since arrays are stored in **contiguous memory**, pointers can be incremented.
 
- Adding 1 to a pointer moves it to the next element (size depends on type).
 

```c
int arr[3] = {10, 20, 30};
int *p = arr;

printf("%d\n", *p);  // 10
printf("%d\n", *(p+1)); // 20
printf("%d\n", *(p+2)); // 30
```

- Strings + pointer arithmetic:
 

```c
char *s = "HI!";
printf("%s\n", s+1); // prints "I!"
printf("%s\n", s+2); // prints "!"
```

---

## 5. **File I/O**

## 📂 **File I/O in C**

### 1. **Files as Streams**

- In C, files are handled as **streams** (a sequence of bytes).
 
- A **stream** is represented by a `FILE *` pointer (from `<stdio.h>`).
 
- Three standard streams exist by default:
 
 - `stdin` → standard input (usually the keyboard)
  
 - `stdout` → standard output (usually the screen)
  
 - `stderr` → standard error (usually the screen, but separate from stdout)
  

---

### 2. **Opening and Closing Files**

- Use `fopen(filename, mode)` to open a file.
 
- Returns a `FILE *` (pointer to the stream).
 
- Always check for `NULL` (if the file couldn’t be opened).
 
- Close with `fclose(fp)` to release system resources.
 

```c
FILE *f = fopen("data.txt", "r"); // open for reading
if (f == NULL) {
 printf("Error opening file\n");
 return 1;
}
fclose(f);
```

---

### 3. **File Modes**

- `"r"` → read (file must exist)
 
- `"w"` → write (creates file, overwrites if it exists)
 
- `"a"` → append (adds to end, creates if doesn’t exist)
 
- `"r+"` → read and write
 
- `"w+"` → read and write, truncates file
 
- `"a+"` → read and append
 

---

### 4. **Reading & Writing**

- **Text files** (formatted I/O):
 
 - `fprintf(fp, "...")` → write formatted text
  
 - `fscanf(fp, "...")` → read formatted text
  
 - `fgets(buffer, size, fp)` → read one line
  
 - `fputs(string, fp)` → write a string
  

```c
FILE *f = fopen("hello.txt", "w");
fprintf(f, "Hello, World!\n");
fclose(f);
```

- **Binary files** (raw data):
 
 - `fread(ptr, size, count, fp)` → read raw bytes
  
 - `fwrite(ptr, size, count, fp)` → write raw bytes
  

```c
int nums[3] = {1, 2, 3};
FILE *f = fopen("data.bin", "wb");
fwrite(nums, sizeof(int), 3, f);
fclose(f);
```

---

### 5. **Error Handling**

- Always check return values:
 
 - `fopen` returns `NULL` if it fails.
  
 - `fscanf` returns number of items read.
  
- Use `feof(fp)` to check end-of-file.
 
- Use `ferror(fp)` to check for errors.
 

---

### 6. **Why File I/O matters**

- Lets programs store data **persistently** (outside of memory).
 
- Enables interaction with external data sources.
- CS50 uses it later for programs like **recover.c** (JPEG recovery), where binary file I/O is critical.
---

## 6. **Heap & Stack**

- **Stack**
 
 - Stores local variables, function calls.
  
 - Fast, automatic, limited size.
  
- **Heap**
 
 - For dynamic memory allocation (`malloc`).
  
 - Must be managed manually (risk of leaks).
  

```c
// Stack
int x = 5;   // disappears when function ends

// Heap
int *p = malloc(sizeof(int));
*p = 42;
free(p);  // must free!
```

---

## 7. **malloc & free**

- **`malloc(size)`** allocates `size` bytes on the heap, returns a pointer.
 
- Memory is uninitialized (contains garbage values).
 
- Always check if `malloc` returned `NULL`.
 
- **`free(ptr)`** releases memory back to system.
 

```c
int *arr = malloc(5 * sizeof(int));
if (arr == NULL) {
 return 1; // allocation failed
}
for (int i = 0; i < 5; i++) {
 arr[i] = i * i;  // use like an array
}
free(arr);  // release memory
```

⚠️ Forgetting `free` causes a **memory leak**.

---

## 8. **Pass by Value vs Pass by Reference**

- **Pass by value** → a copy is passed, original unchanged.
 
- **Pass by reference** → using pointers, we pass the actual address, so changes persist.
 

```c
// Pass by value
void setToTen(int x) {
 x = 10;
}
int a = 5;
setToTen(a);
printf("%d\n", a);  // still 5

// Pass by reference
void setToTenRef(int *x) {
 *x = 10;
}
int b = 5;
setToTenRef(&b);
printf("%d\n", b);  // now 10
```

---
