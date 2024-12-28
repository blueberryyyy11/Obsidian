#flashcards
# C++ Flashcards for Exam Preparation

#pointers #references

Что такое ссылка в C++?::Ссылка — это алиас (другое имя) для переменной. Ссылка должна быть инициализирована и не может быть null.
<!--SR:!2024-12-31,3,250-->

Что такое указатель в C++?::Указатель — это переменная, которая хранит адрес памяти другой переменной.
<!--SR:!2024-12-31,3,250-->

Чем отличается указатель от ссылки в C++?::Ссылка — это алиас для существующей переменной и не может быть null. Указатель хранит адрес переменной, может быть переназначен и может быть null.
<!--SR:!2024-12-31,3,250-->

Что делает оператор `*`, когда используется с указателями?::Оператор `*` дереференсит указатель, предоставляя доступ к значению, хранящемуся по адресу.
<!--SR:!2024-12-31,3,250-->

Что такое нулевой указатель?::Указатель, который не указывает ни на какое действительное место в памяти. Его можно объявить с помощью ключевого слова `nullptr`.
<!--SR:!2024-12-31,3,250-->

Как объявить нулевой указатель?::Используя ключевое слово `nullptr`, например: `int* ptr = nullptr;`.
<!--SR:!2024-12-31,3,250-->

Для чего используется оператор `&` в C++?::Оператор `&` используется для получения адреса переменной.
<!--SR:!2024-12-31,3,250-->

Что произойдет, если дереференсить неинициализированный указатель?::Это приведет к неопределенному поведению, так как указатель может указывать на недопустимую или недоступную память.
<!--SR:!2024-12-31,3,250-->

Почему полезно передавать указатель по ссылке в функцию?::Это позволяет функции модифицировать сам указатель, например, перенаправить его на динамически выделенную память.
<!--SR:!2024-12-31,3,250-->

---

## Управление памятью: Stack и Heap

Что такое стековая память (Stack)?::Автоматически выделяемая и освобождаемая область памяти, используемая для локальных переменных и вызовов функций.
<!--SR:!2024-12-31,3,250-->

Что такое куча (Heap)?::Область памяти, используемая для динамического выделения памяти, которая требует явного освобождения.
<!--SR:!2024-12-31,3,250-->

Как выделить и освободить память в куче?::Используйте оператор `new` для выделения и `delete` для освобождения памяти.
<!--SR:!2024-12-31,3,250-->

Какие риски связаны с неправильным управлением памятью?::Могут возникнуть утечки памяти (когда выделенная память не освобождается) или висячие указатели (обращение к освобожденной памяти).
<!--SR:!2024-12-31,3,250-->

Чем отличается стек от кучи?::Память стека управляется автоматически, быстрее, но ограничена по размеру. Память кучи требует ручного управления, медленнее, но объем больше.
<!--SR:!2024-12-31,3,250-->

---

## Перегрузка функций и параметры по умолчанию

Что такое перегрузка функций?::Когда несколько функций имеют одинаковое имя, но различное число или тип аргументов.
<!--SR:!2024-12-31,3,250-->

Почему нельзя перегружать функции, различающиеся только возвращаемым типом?::Компилятор использует параметры функции, а не тип возвращаемого значения, чтобы отличать перегруженные функции.
<!--SR:!2024-12-31,3,250-->

Что такое параметры по умолчанию?::Параметры с установленными значениями, которые используются, если аргумент не указан при вызове функции.
<!--SR:!2024-12-31,3,250-->

---

## l-value и r-value

Что такое l-value в C++?::Выражение, представляющее местоположение в памяти, которое может быть использовано слева от знака присваивания.
<!--SR:!2024-12-31,3,250-->

Что такое r-value в C++?::Временное значение, которое может быть использовано только справа от знака присваивания.
<!--SR:!2024-12-31,3,250-->

Какой тип ссылки нужен для привязки к r-value?::Ссылка на r-value, объявляемая с помощью `&&`.
<!--SR:!2024-12-31,3,250-->

Пример r-value?::Литерал, например, `10`, или результат выражения, например, `x + y`.
<!--SR:!2024-12-31,3,250-->

---

## Важные концепции

Что делает тернарный оператор?::Оценивает условие и возвращает одно из двух значений в зависимости от результата. Пример: `a < b ? a : b`.
<!--SR:!2024-12-31,3,250-->

Что такое шаблон (template) в C++?::Способ определения функций или классов, которые могут работать с любым типом данных.
<!--SR:!2024-12-31,3,250-->

Что делает `std::move`?::Позволяет реализовать семантику перемещения, передавая объект в качестве r-value ссылки, для оптимизации передачи ресурсов.

---

## Практические примеры

Почему опасно возвращать ссылку на локальную переменную?::Локальная переменная уничтожается при выходе из функции, оставляя ссылку висячей【.
<!--SR:!2025-01-01,4,270-->

Что произойдет, если вызвать `delete` дважды для одного указателя?::Приведет к неопределенному поведению, часто вызывающему сбой программы【5:1†source】.
<!--SR:!2025-01-01,4,270-->

Как предотвратить утечки памяти?::Используйте умные указатели, такие как `std::unique_ptr` или `std::shared_ptr`.
<!--SR:!2024-12-31,3,250-->

#oop
Q: What are the core principles of OOP in C++?::Encapsulation, Inheritance, Polymorphism, and Abstraction.

Q: What is encapsulation?::Combining data and functions into a single unit (class/struct) and controlling access using access specifiers (`public`, `private`, `protected`).

Q: What is inheritance?::A mechanism that allows a class to inherit properties and behavior from another class.

Q: What is polymorphism?::The ability of methods to behave differently based on the object, achieved using method overriding and virtual functions.

Q: What is abstraction?::Hiding complexity by exposing only the essential details, often implemented with abstract classes and pure virtual functions.

---

## Struct in C++

Q: What is a struct in C++?::A user-defined type that groups data together. It can have member functions, access specifiers, and constructors in C++.

Q: What is the default access modifier in a struct?::`public`.

Q: What is the main difference between struct and class in C++?::The default access in a `struct` is `public`, while in a `class` it is `private`.

---

## Member Variables and Member Functions

Q: What are member variables?::Variables declared inside a class/struct, representing the state of the object.

Q: What are member functions?::Functions defined in a class/struct, representing the behavior of the object.

Q: What are the access specifiers in C++?::`public`, `private`, and `protected`.

Q: What does the `public` access specifier mean?::Allows access to the member from anywhere in the program.

Q: What does the `private` access specifier mean?::Restricts access to the member to only within the class or struct.

Q: What does the `protected` access specifier mean?::Allows access to the member within the class and its derived classes.

---

## Constructors

Q: What is a constructor in C++?::A special member function called automatically when an object is created.

Q: What is a default constructor?::A constructor with no parameters, provided by C++ if no other constructor is defined.

Q: What is a parameterized constructor?::A constructor that takes arguments to initialize member variables.

Q: What is constructor overloading?::Defining multiple constructors with different parameter lists in the same class.

Q: Provide an example of a parameterized constructor.::
```cpp
class Rectangle {
    int width, height;
    public:
        Rectangle(int w, int h) : width(w), height(h) {}
};
```

---

## Operator Overloading

Q: What is operator overloading in C++?::The process of redefining operators to work with user-defined types.

Q: Which operators cannot be overloaded in C++?::`sizeof`, `::`, `.*`, `.`, `typeid`.

Q: What is the syntax for operator overloading?::
```cpp
ReturnType operatorSymbol(Arguments) { /* Implementation */ }
```

Q: Provide an example of overloading the `+` operator.::
```cpp
class Complex {
    int real, imag;
    public:
        Complex(int r, int i) : real(r), imag(i) {}
        Complex operator+(const Complex& c) {
            return Complex(real + c.real, imag + c.imag);
        }
};
```

Q: Provide an example of overloading the `==` operator.::
```cpp
class Point {
    int x, y;
    public:
        Point(int a, int b) : x(a), y(b) {}
        bool operator==(const Point& p) {
            return x == p.x && y == p.y;
        }
};
```

---

## Additional Key Concepts

Q: What is the difference between a struct and a class?::Structs default to `public` access, while classes default to `private`.

Q: Why do we use constructors?::To initialize objects when they are created.

Q: Why is operator overloading useful?::To make user-defined types behave like built-in types, improving code readability and functionality.

Q: What is the purpose of access specifiers in C++?::To control how and where class/struct members can be accessed.
