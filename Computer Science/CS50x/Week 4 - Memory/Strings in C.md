

- In C, strings are **arrays of characters terminated by a null character `'\0'`**.

- A string variable (e.g., `char *s`) holds the **address of the first character**.

- Since characters in an array are stored in consecutive memory, functions can start from the first character and keep moving forward until they encounter `'\0'`.

- Example:
```c
	char *s = "HI!";   // pointer to string literal (read-only)
	char t[] = "HI!";  // array containing a copy (modifiable)
```
---
