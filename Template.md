t's a blueprint or a mold that allows you to write code that works with **any data type** without having to rewrite the same logic for each type.

### The Core Idea: "Write Once, Use with Any Type"
The main purpose of a template is to enable **generic programming**. You write a function or a class once, and the compiler generates the specific versions for the data types you actually use.
There are two primary kinds of templates you'll encounter: **Function Templates** and **Class Templates**.
#### Function templates
A function template lets you write a single function that works on different data types.
instead of:
```cpp
int max(int a, int b) {
    return (a > b) ? a : b;
}

double max(double a, double b) {
    return (a > b) ? a : b;
}

string max(string a, string b) {
    return (a > b) ? a : b;
}
// ... and so on for every type you need!
```
we use:
```cpp
// T is a placeholder for the actual type
template <typename T>
T max(T a, T b) {
    return (a > b) ? a : b;
}
```
The compiler automatically generates the `int max(int, int)`, `double max(double, double)`, etc.(based on the input type),  functions for you behind the scenes. This process is called **template instantiation**.

#### Class templates
A class template lets you define a class where the data type of its members is a parameter.
instead of:
```cpp
class Box {
private:
    int content;
public:
    void setContent(int c) { content = c; }
    int getContent() { return content; }
};
```
we use:
```cpp
template <typename T>
class Box {
private:
    T content; // T is the placeholder for the type
public:
    void setContent(T c) { content = c; }
    T getContent() { return content; }
};
```

- The most famous example of a class template is the [C++] Standard Template Library (STL) `vector`. `vector<int>`, `vector<string>`, etc., are all generated from the same `vector` class template. 
### Where are Templates Used?

Templates are a cornerstone of several programming paradigms and libraries:

- **[[C++]]:** This is where templates are most powerful and complex (as shown in the examples above). The entire **Standard Template Library (STL)** (with `vector`, `list`, `map`, `sort`, etc.) is built on templates.
    
- **[[Java]]:** Called **Generics**. The syntax is slightly different (e.g., `List<Integer> list = new ArrayList<>();`), but the core idea is the same: type safety and code reuse.
    
- **[[C#]]:** Also called **Generics** (e.g., `List<int> list = new List<int>();`).
    
- **[[Python]]:** Uses a concept called **"duck typing"** which achieves similar flexibility but in a different, dynamic way. Python also has **type hints** for generics (e.g., `def max(a: T, b: T) -> T: ...`) to provide better clarity and tooling support.
### The key benefits:
1. **Code Reusability:** Write the algorithm or container once, use it for any type.
    
2. **Type Safety:** Templates (in languages like C++ and Java) are checked at compile time. This is safer than using `void*` pointers in C or losing type information in dynamically-typed languages.
    
3. **Performance:** Since the code is generated for the specific type at compile time, it is often as fast as if you had written the specialized code by hand. This is a major advantage over runtime mechanisms.

![[Pasted image 20251120230644.png]]

## Template expression
A **[template expression]** is a special syntax, often using placeholders, that allows you to embed dynamic values and logic directly inside a static template (like HTML, XML, or a string). When the template is processed, these expressions are evaluated, and their results are inserted into the final output.
Think of it as a recipe where you have fixed instructions and ingredients, but you leave a blank space for a variable item (e.g., "Add `{number_of_guests}` cups of flour"). The baker (the template engine) fills in the blank when they know how many guests are coming.
The simplest way to understand a template expression is as a **"fill-in-the-blank"** inside a larger piece of text.

- **The Template:** `"Hello, {name}! Welcome to {city}."`
    
- **The Data:** `{ name: "Alice", city: "Paris" }`
    
- **The Result:** `"Hello, Alice! Welcome to Paris."`
    

Here, `{name}` and `{city}` are the template expressions.
exp in [[java]]:
```java
String name = "Alice";
int age = 30;
double score = 95.5;

// Using positional placeholders
String message = String.format("Hello, %s! You are %d years old. Score: %.2f", name, age, score);
System.out.println(message);
// Output: Hello, Alice! You are 30 years old. Score: 95.50

// Different format specifiers
String template = "Name: %s, Age: %d, Height: %.2f, Hex: %x";
String result = String.format(template, "Bob", 25, 175.5, 255);
System.out.println(result);
// Output: Name: Bob, Age: 25, Height: 175.50, Hex: ff
```