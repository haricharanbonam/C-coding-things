

---

# 🔴 FIRST: very important confirmation
### ✅ ONLY STRINGS end with `\0`
### ✅ ONLY character arrays used as strings

---

## Example

```c
char c = 'A';
```

❌ No `\0`

```c
char s[] = "A";
```

✅ Stored as:

```
'A'  '\0'
```

👉 **Only strings have `\0`.**

This is FINAL. Remember this forever.

---

# 🧠 Now the big clarity table (very important)

## 🔵 Memory + mutability clarity

| Type                | Example           | Memory used | Has `\0`? | Can modify value? |
| ------------------- | ----------------- | ----------- | --------- | ----------------- |
| int                 | `int a = 10;`     | stack       | ❌         | ✅ yes             |
| float               | `float f = 2.5;`  | stack       | ❌         | ✅ yes             |
| char                | `char c = 'A';`   | stack       | ❌         | ✅ yes             |
| string constant     | `"Hello"`         | read-only   | ✅         | ❌ no              |
| char array (string) | `char s[]="Hi";`  | stack       | ✅         | ✅ yes             |
| pointer to string   | `char *s="Hi";`   | read-only   | ✅         | ❌ no              |
| array               | `int a[5];`       | stack       | ❌         | elements yes      |
| structure           | `struct S {...};` | stack       | ❌         | ✅ yes             |
| union               | `union U {...};`  | stack       | ❌         | ⚠ partially       |

Now let’s understand each one slowly.

---

# 🔹 int / float / char

```c
int a = 10;
a = 20;   // allowed
```

* Stored in **stack memory**
* Direct value
* Completely **modifiable**
* No `\0` concept at all

Same for:

```c
float f = 3.14;
char c = 'A';
```

---

# 🔹 String constant

```c
"Hello"
```

* Stored in **read-only memory**
* Ends with `\0`
* Cannot be modified

❌ Wrong:

```c
"Hello"[0] = 'h';   // illegal
```

---

# 🔹 char array string

```c
char s[] = "Hello";
```

Memory:

```
H  e  l  l  o  \0
```

* Stored in **stack**
* Ends with `\0`
* Fully **modifiable**

✅ Allowed:

```c
s[0] = 'h';
```

---

# 🔹 char pointer string

```c
char *s = "Hello";
```

Here:

* `"Hello"` → read-only memory
* `s` → stack (pointer)

So:

```c
s[0] = 'h';  ❌
```

But:

```c
s = "World";  ✅
```

👉 You cannot change characters
👉 You can change where pointer points

This is **very important interview + exam concept**.

---

# 🔹 Arrays (int array, float array)

```c
int a[5] = {1,2,3,4,5};
```

* Stored in stack
* Size fixed
* Elements modifiable
* No `\0` unless char array used as string

---

# 🔹 Array of strings

```c
char names[3][10] = {"Ram", "Sam", "Tom"};
```

Each string:

```
R a m \0
S a m \0
T o m \0
```

* Each string has its own `\0`
* Modifiable
* Stored in stack

---

# 🔹 Structure

```c
struct Student {
    int id;
    float marks;
};
```

* Stored in stack
* Members modifiable
* No `\0` automatically
* If structure has char array → then that array has `\0`

Example:

```c
struct Student s;
strcpy(s.name, "Hari"); // name ends with \0
```

---

# 🔹 Union

```c
union Data {
    int i;
    float f;
    char c;
};
```

* All members share **same memory**
* Only one valid at a time
* Modifiable
* No `\0` concept unless char array

---

# 🔥 Final golden rule (never forget)

### ✅ `\0` exists ONLY for STRINGS

Which means:

* char array used as string
* string literal

Nothing else.

---

# 🧠 One-line memory trick

> **If it is not a character array string → no `\0`.**

---


