List that uses pointers to link things together in the computers memory.

```C
typedef struct node
{
  int number;
  struct node *next;
} node;
```

