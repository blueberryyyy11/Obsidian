### Unqualified Name

An **unqualified name** in C++ refers to a name (identifier) that is used without any qualifying context. It is simply a variable, function, or type name used without specifying its scope explicitly. The compiler determines its meaning based on the current scope or context.

#### Example:

```cpp
int x = 10; // 'x' is an unqualified name
void func() {
    int y = x; // 'y' and 'x' are both unqualified names
}
```

In the example above, `x` and `y` are unqualified names because they are referenced directly without specifying any namespace, class, or scope.

---

### Nested-Name-Specifier

A **nested-name-specifier** is the part of a name in C++ that qualifies an identifier to indicate that it belongs to a specific namespace, class, or scope. It uses the scope resolution operator (`::`) to explicitly specify where the name comes from.

#### Syntax:

```cpp
<namespace-or-class>::<name>
```

#### Example:

```cpp
namespace MyNamespace {
    class MyClass {
    public:
        static int value;
    };
}

int MyNamespace::MyClass::value = 42;

void func() {
    int x = MyNamespace::MyClass::value; // 'MyNamespace::MyClass::' is the nested-name-specifier
}
```

In this example, `MyNamespace::MyClass::` is the **nested-name-specifier** that qualifies `value` to indicate it belongs to `MyClass` inside `MyNamespace`.

---

### Unqualified-id

An **unqualified-id** is a term used in C++ grammar to describe an identifier that is not preceded by a **nested-name-specifier**. It refers to names such as variables, functions, or types when they are used in a local or global scope without any qualifying prefix.

#### Example:

```cpp
void func() {
    int x = 10;    // 'x' is an unqualified-id
    int y = x + 5; // 'y' is also an unqualified-id
}
```

An **unqualified-id** contrasts with a **qualified-id**, which uses a **nested-name-specifier**.

#### Example of Qualified-id:

```cpp
namespace MyNamespace {
    int value = 10;
}

void func() {
    int x = MyNamespace::value; // 'MyNamespace::value' is a qualified-id
}
```

In this case:

- `value` is an **unqualified-id** when used directly.
- `MyNamespace::value` is a **qualified-id** because it uses `MyNamespace::` as a nested-name-specifier.

---
