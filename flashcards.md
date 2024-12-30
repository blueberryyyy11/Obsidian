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
<!--SR:!2025-01-01,3,251-->

Q: What is encapsulation?::Combining data and functions into a single unit (class/struct) and controlling access using access specifiers (`public`, `private`, `protected`).
<!--SR:!2025-01-02,4,273-->

Q: What is inheritance?::A mechanism that allows a class to inherit properties and behavior from another class.
<!--SR:!2025-01-01,3,251-->

Q: What is polymorphism?::The ability of methods to behave differently based on the object, achieved using method overriding and virtual functions.
<!--SR:!2025-01-01,3,252-->

Q: What is abstraction?::Hiding complexity by exposing only the essential details, often implemented with abstract classes and pure virtual functions.
<!--SR:!2025-01-01,3,252-->

---

## Struct in C++

Q: What is a struct in C++?::A user-defined type that groups data together. It can have member functions, access specifiers, and constructors in C++.
<!--SR:!2025-01-02,4,272-->

Q: What is the default access modifier in a struct?::`public`.
<!--SR:!2025-01-01,3,252-->

Q: What is the main difference between struct and class in C++?::The default access in a `struct` is `public`, while in a `class` it is `private`.
<!--SR:!2025-01-02,4,272-->

---

## Member Variables and Member Functions

Q: What are member variables?::Variables declared inside a class/struct, representing the state of the object.

Q: What are member functions?::Functions defined in a class/struct, representing the behavior of the object.
<!--SR:!2025-01-02,4,273-->

Q: What are the access specifiers in C++?::`public`, `private`, and `protected`.
<!--SR:!2025-01-02,4,274-->

Q: What does the `public` access specifier mean?::Allows access to the member from anywhere in the program.

Q: What does the `private` access specifier mean?::Restricts access to the member to only within the class or struct.
<!--SR:!2025-01-02,4,271-->

Q: What does the `protected` access specifier mean?::Allows access to the member within the class and its derived classes.
<!--SR:!2025-01-01,3,251-->

---

## Constructors

Q: What is a constructor in C++?::A special member function called automatically when an object is created.
<!--SR:!2025-01-01,3,251-->

Q: What is a default constructor?::A constructor with no parameters, provided by C++ if no other constructor is defined.
<!--SR:!2025-01-01,3,252-->

Q: What is a parameterized constructor?::A constructor that takes arguments to initialize member variables.
<!--SR:!2025-01-01,3,254-->

Q: What is constructor overloading?::Defining multiple constructors with different parameter lists in the same class.
<!--SR:!2025-01-01,3,252-->

Q: Provide an example of a parameterized constructor.::
<!--SR:!2025-01-01,3,252-->
```cpp
class Rectangle {
    int width, height;
    public:
        Rectangle(int w, int h) : width(w), height(h) {}
};
```

---

## Operator Overloading
#flashcards 

Q: What is operator overloading in C++?::The process of redefining operators to work with user-defined types.
<!--SR:!2025-01-01,3,254-->

Q: Which operators cannot be overloaded in C++?::`sizeof`, `::`, `.*`, `.`, `typeid`.
<!--SR:!2025-01-01,3,252-->

Q: What is the syntax for operator overloading?::ReturnType operatorSymbol(Arguments) { /* Implementation */ }
<!--SR:!2025-01-01,3,254-->

## Flashcards: Operator Overloading in C++

Q: How is the `+` operator overloaded?:: The `+` operator is overloaded by defining a member function that returns the sum of the calling object's value and another object's value as a new object: `Demo operator+(const Demo& obj) { return Demo(value + obj.value); }`.

Q: How is the `-` operator overloaded?:: The `-` operator is overloaded by defining a member function that returns the difference between the calling object's value and another object's value as a new object: `Demo operator-(const Demo& obj) { return Demo(value - obj.value); }`.

Q: How is the `*` operator overloaded?:: The `*` operator is overloaded by defining a member function that returns the product of the calling object's value and another object's value as a new object: `Demo operator*(const Demo& obj) { return Demo(value * obj.value); }`.

Q: How is the `/` operator overloaded?:: The `/` operator is overloaded by defining a member function that returns the quotient of the calling object's value and another object's value as a new object, with error handling for division by zero: `Demo operator/(const Demo& obj) { if (obj.value == 0) throw runtime_error("Division by zero!"); return Demo(value / obj.value); }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the `==` operator overloaded?:: The `==` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if they are equal: `bool operator==(const Demo& obj) { return value == obj.value; }`.

Q: How is the `!=` operator overloaded?:: The `!=` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if they are not equal: `bool operator!=(const Demo& obj) { return value != obj.value; }`.

Q: How is the `<` operator overloaded?:: The `<` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if the calling object's value is less: `bool operator<(const Demo& obj) { return value < obj.value; }`.

Q: How is the `>` operator overloaded?:: The `>` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if the calling object's value is greater: `bool operator>(const Demo& obj) { return value > obj.value; }`.

Q: How is the `<=` operator overloaded?:: The `<=` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if the calling object's value is less than or equal: `bool operator<=(const Demo& obj) { return value <= obj.value; }`.

Q: How is the `>=` operator overloaded?:: The `>=` operator is overloaded by defining a member function that compares the calling object's value with another object's value and returns `true` if the calling object's value is greater than or equal: `bool operator>=(const Demo& obj) { return value >= obj.value; }`.

Q: How is the prefix `++` operator overloaded?:: The prefix `++` operator is overloaded by defining a member function that increments the calling object's value and returns the modified object by reference: `Demo& operator++() { ++value; return *this; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the postfix `++` operator overloaded?:: The postfix `++` operator is overloaded by defining a member function that returns a copy of the object before incrementing the calling object's value: `Demo operator++(int) { Demo temp = *this; value++; return temp; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the prefix `--` operator overloaded?:: The prefix `--` operator is overloaded by defining a member function that decrements the calling object's value and returns the modified object by reference: `Demo& operator--() { --value; return *this; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the postfix `--` operator overloaded?:: The postfix `--` operator is overloaded by defining a member function that returns a copy of the object before decrementing the calling object's value: `Demo operator--(int) { Demo temp = *this; value--; return temp; }`.

Q: How is the `!` operator overloaded?:: The `!` operator is overloaded by defining a member function that returns `true` if the calling object's value is zero: `bool operator!() { return value == 0; }`.

Q: How is the `&&` operator overloaded?:: The `&&` operator is overloaded by defining a member function that returns the logical AND of the calling object's value and another object's value: `bool operator&&(const Demo& obj) { return value && obj.value; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the `||` operator overloaded?:: The `||` operator is overloaded by defining a member function that returns the logical OR of the calling object's value and another object's value: `bool operator||(const Demo& obj) { return value || obj.value; }`.

Q: How is the `[]` operator overloaded?:: The `[]` operator is overloaded by defining a member function that performs a custom operation using an index, such as returning the index multiplied by the calling object's value: `int operator[](int index) { return value * index; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the `()` operator overloaded?:: The `()` operator is overloaded by defining a member function that allows the object to act like a function, performing a custom operation such as multiplying the value by a factor: `void operator()(int factor) { value *= factor; }`.

Q: How is the `<<` operator overloaded?:: The `<<` operator is overloaded by defining a friend function that outputs the calling object's value to an output stream: `friend ostream& operator<<(ostream& out, const Demo& obj) { out << obj.value; return out; }`.
<!--SR:!2025-01-01,3,254-->

Q: How is the `>>` operator overloaded?:: The `>>` operator is overloaded by defining a friend function that inputs a value from an input stream into the calling object: `friend istream& operator>>(istream& in, Demo& obj) { in >> obj.value; return in; }`.

Q: How is the `*` operator overloaded?:: The `*` operator is overloaded by defining a member function that returns the calling object's value, simulating pointer dereferencing: `int operator*() { return value; }`.


## Additional Key Concepts

Q: What is the difference between a struct and a class?::Structs default to `public` access, while classes default to `private`.
<!--SR:!2025-01-02,4,274-->

Q: Why do we use constructors?::To initialize objects when they are created.
<!--SR:!2025-01-01,3,252-->

Q: Why is operator overloading useful?::To make user-defined types behave like built-in types, improving code readability and functionality.

Q: What is the purpose of access specifiers in C++?::To control how and where class/struct members can be accessed.
<!--SR:!2025-01-02,4,272-->

# Flashcards: Object-Oriented Programming (OOP) in C++

#flashcards 

## Flashcard 1
What is Object-Oriented Programming (OOP):: OOP is a programming paradigm that models real-world problems using objects and classes, focusing on principles like encapsulation, inheritance, polymorphism, and abstraction to structure programs efficiently and logically.
<!--SR:!2025-01-02,4,272-->

## Flashcard 2
What is encapsulation in OOP:: Encapsulation is the concept of bundling data and functions that operate on that data within a single unit, typically a class or struct, while restricting direct access to the data through access specifiers like `public`, `private`, and `protected`.
<!--SR:!2025-01-01,3,252-->

## Flashcard 3
What is inheritance in OOP:: Inheritance is a mechanism where one class, known as the derived or child class, inherits attributes and methods from another class, called the base or parent class, allowing code reuse and the extension of existing functionality.
<!--SR:!2025-01-01,3,252-->

## Flashcard 4
What is polymorphism in OOP:: Polymorphism is the ability of a function or method to behave differently based on the object it is called on, achieved through method overloading, method overriding, and the use of virtual functions.

## Flashcard 5
What is abstraction in OOP:: Abstraction is the principle of hiding complex implementation details and exposing only the necessary functionality through abstract classes, interfaces, or pure virtual functions, simplifying system design and increasing flexibility.

## Flashcard 6
What is the role of access specifiers in OOP:: Access specifiers in OOP, such as `public`, `private`, and `protected`, define the scope and accessibility of class members, ensuring data security and controlled access within and outside of the class hierarchy.

## Flashcard 7
What is a class in OOP:: A class in OOP is a blueprint or template that defines the properties (attributes) and behaviors (methods) that objects created from the class will have, encapsulating data and functionality in one unit.

## Flashcard 8
What is an object in OOP:: An object is an instance of a class in OOP that represents a specific entity with state and behavior, defined by the attributes and methods of the class it is created from.

## Flashcard 9
What is the default access specifier for a class and a struct in C++:: In C++, the default access specifier for a class is `private`, while for a struct, it is `public`.
<!--SR:!2025-01-01,3,254-->

## Flashcard 10
How is abstraction achieved in C++:: Abstraction in C++ is achieved through abstract classes and pure virtual functions, where a pure virtual function is declared by using `= 0` in its declaration, forcing derived classes to provide specific implementations.
<!--SR:!2025-01-01,3,252-->

## Flashcard 11
What is method overriding in OOP:: Method overriding occurs when a derived class provides a specific implementation of a function that is already defined in its base class, typically using the `virtual` keyword in C++ to support runtime polymorphism.
<!--SR:!2025-01-01,3,254-->

## Flashcard 12
What is the difference between a struct and a class in C++:: In C++, the key difference between a struct and a class is their default access level: struct members are `public` by default, while class members are `private` by default. Structs are generally used for simple data grouping, whereas classes are used for more complex OOP designs.
<!--SR:!2025-01-02,4,272-->

## Flashcard 13
What are constructors in OOP:: Constructors are special member functions in a class that are automatically called when an object is created, initializing the object’s attributes and allowing different setups through constructor overloading.

## Flashcard 14
What is the purpose of a destructor in OOP:: A destructor is a special member function in a class that is automatically invoked when an object is destroyed, used to release resources, such as dynamically allocated memory, and perform cleanup operations.
<!--SR:!2025-01-01,3,252-->

## Flashcard 15
What is the difference between compile-time and runtime polymorphism:: Compile-time polymorphism, also called static binding, is achieved through function overloading and operator overloading, whereas runtime polymorphism, or dynamic binding, is achieved using virtual functions and inheritance.
<!--SR:!2025-01-01,3,252-->

## Flashcard 16
What is a pure virtual function in C++:: A pure virtual function in C++ is a function declared within a class that has no implementation and is defined with `= 0`, making the class abstract and enforcing derived classes to override and implement the function.

## Flashcard 17
How does inheritance support code reusability in OOP:: Inheritance allows derived classes to reuse code from base classes, enabling developers to extend or modify existing functionality without rewriting the code, thus promoting efficient and modular design.
<!--SR:!2025-01-01,3,252-->

## Flashcard 18
What is the significance of the `protected` access specifier in OOP:: The `protected` access specifier allows class members to be accessible within the class itself and in derived classes, providing a middle ground between `private` and `public` access levels.

## Flashcard 19
What are the key principles of OOP:: The key principles of OOP are encapsulation, which combines data and functions into a single unit; inheritance, which allows reuse of code; polymorphism, which provides flexibility in behavior; and abstraction, which hides complexity and exposes essential details.

## Flashcard 20
Why are virtual functions important in C++:: Virtual functions are important in C++ because they enable runtime polymorphism, allowing the program to determine the function to call at runtime based on the type of the object, supporting flexible and dynamic behavior in inheritance hierarchies.

## Flashcard 21
Virtual functions are...:: Virtual functions are member functions in a base class that can be overridden in a derived class to achieve runtime polymorphism. They allow the program to determine the appropriate function to call based on the type of the object at runtime, rather than the type of the pointer or reference used to invoke the function.
<!--SR:!2024-12-30,1,232-->

## Flashcard 22
Abstract classes are...:: Абстрактный класс — это класс, который содержит хотя бы одну чисто виртуальную функцию (объявленную с помощью = 0). Он не может быть инстанцирован, то есть нельзя создать объект этого класса. Абстрактные классы используются для определения интерфейсов, которые должны быть реализованы в производных классах.

## Flashcard 23
Pure virtual functions are...:: Pure virtual functions are member functions declared within an abstract class that have no implementation in the base class. They are defined by using `= 0` in their declaration and must be overridden in derived classes to provide specific functionality.

------------------------------------------------------------------------------
#flashcards 

Q: Какова цель использования шаблонов в C++?::Шаблоны позволяют создавать обобщённые классы или функции, которые работают с любым типом данных.

Q: Как определить шаблон функции в C++?::Используйте синтаксис `template <typename T>` для определения обобщённой функции, заменяя конкретные типы на `T`.
<!--SR:!2025-01-01,3,254-->

Q: Какой синтаксис используется для создания шаблона класса в C++?::Используйте `template <typename T>` перед определением класса, чтобы сделать класс обобщённым.

Q: Как специализировать шаблон функции в C++?::Определите конкретную реализацию для определённого типа, явно указав тип шаблона.
<!--SR:!2024-12-30,1,234-->

Q: Можно ли использовать несколько параметров типов в шаблоне?::Да, используйте `template <typename T1, typename T2>` для определения нескольких параметров типов.

Q: Какой синтаксис используется для создания экземпляра шаблона класса в C++?::Используйте синтаксис `ClassName<Type>` для создания экземпляра шаблона класса с конкретным типом.

Q: Как определить шаблон с параметром, не являющимся типом?::Используйте `template <typename T, int N>` для определения шаблона с параметром, не являющимся типом, например, для фиксированного размера.

Q: Что такое специализация шаблона в C++?::Специализация шаблона позволяет настраивать поведение шаблона для определённого типа.
<!--SR:!2025-01-01,3,254-->

Q: Что такое инстанцирование шаблона?::Инстанцирование шаблона создаёт конкретную функцию или класс из шаблона, указывая тип.
<!--SR:!2025-01-01,3,254-->

Q: Как реализовать функцию-член вне шаблона класса?::Используйте синтаксис `template <typename T> ReturnType ClassName<T>::FunctionName(...)`.

Q: Можно ли использовать шаблоны для операторов в C++?::Да, вы можете определить шаблоны операторов так же, как и шаблоны функций.

Q: В чём разница между шаблоном функции и шаблоном класса?::Шаблон функции делает отдельные функции обобщёнными, а шаблон класса делает обобщённым весь класс.

Q: Можно ли использовать аргументы по умолчанию в шаблонах?::Да, вы можете задавать типы или значения по умолчанию для параметров шаблона.

Q: Что такое вариативный шаблон в C++?::Вариативный шаблон позволяет принимать переменное количество параметров шаблона с использованием `template <typename... Args>`.

Q: Что такое ограничения для шаблонов?::Ограничения для шаблонов задают правила для типов, которые можно передавать в шаблоны, часто с использованием `concepts` или SFINAE ("Неудача подстановки не является ошибкой").

Q: Какова цель использования шаблонов в C++?::Шаблоны позволяют создавать обобщённые классы или функции, которые работают с любым типом данных.

Q: Как определить шаблон функции в C++?::Используйте синтаксис `template <typename T>` для определения обобщённой функции, заменяя конкретные типы на `T`.

Q: Какой синтаксис используется для создания шаблона класса в C++?::Используйте `template <typename T>` перед определением класса, чтобы сделать класс обобщённым.

Q: Как специализировать шаблон функции в C++?::Определите конкретную реализацию для определённого типа, явно указав тип шаблона.

Q: Можно ли использовать несколько параметров типов в шаблоне?::Да, используйте `template <typename T1, typename T2>` для определения нескольких параметров типов.

Q: Какой синтаксис используется для создания экземпляра шаблона класса в C++?::Используйте синтаксис `ClassName<Type>` для создания экземпляра шаблона класса с конкретным типом.

Q: Как определить шаблон с параметром, не являющимся типом?::Используйте `template <typename T, int N>` для определения шаблона с параметром, не являющимся типом, например, для фиксированного размера.

Q: Что такое специализация шаблона в C++?::Специализация шаблона позволяет настраивать поведение шаблона для определённого типа.

Q: Что такое инстанцирование шаблона?::Инстанцирование шаблона создаёт конкретную функцию или класс из шаблона, указывая тип.

Q: Как реализовать функцию-член вне шаблона класса?::Используйте синтаксис `template <typename T> ReturnType ClassName<T>::FunctionName(...)`.

Q: Можно ли использовать шаблоны для операторов в C++?::Да, вы можете определить шаблоны операторов так же, как и шаблоны функций.

Q: В чём разница между шаблоном функции и шаблоном класса?::Шаблон функции делает отдельные функции обобщёнными, а шаблон класса делает обобщённым весь класс.

Q: Можно ли использовать аргументы по умолчанию в шаблонах?::Да, вы можете задавать типы или значения по умолчанию для параметров шаблона.

Q: Что такое вариативный шаблон в C++?::Вариативный шаблон позволяет принимать переменное количество параметров шаблона с использованием `template <typename... Args>`.

Q: Что такое ограничения для шаблонов?::Ограничения для шаблонов задают правила для типов, которые можно передавать в шаблоны, часто с использованием `concepts` или SFINAE ("Неудача подстановки не является ошибкой").

Q: Что такое l-value в C++?::l-value (left value) — это объект, который занимает определённое место в памяти и имеет адрес.

Q: Что такое r-value в C++?::r-value (right value) — это временное значение, которое не имеет адреса в памяти. Например, литералы или результат выражений.

Q: Как использовать ссылки на r-value?::Для работы с r-value используется `T&&`, что позволяет ссылаться на временные объекты. int&& r = 5 + 10; // r ссылается на временное значение 15.
<!--SR:!2025-01-01,3,254-->

Q: Что делает std::move в C++?::`std::move` преобразует l-value в r-value, позволяя передать временный объект в функции или конструкторы перемещения.

Q: Что такое конструктор перемещения?::Конструктор перемещения используется для переноса ресурсов (например, динамической памяти) от одного объекта к другому вместо копирования.

Q: Что такое оператор присваивания с перемещением?::Оператор присваивания с перемещением освобождает старые ресурсы объекта и перемещает ресурсы из другого объекта.

Q: Для чего используется static_cast в C++?::`static_cast` выполняет проверяемое преобразование типов, например, преобразование между указателями базового и производного классов.

Q: Для чего используется reinterpret_cast в C++?::`reinterpret_cast` выполняет небезопасное преобразование типов, которое позволяет интерпретировать битовое представление одного типа как другого.

Q: Для чего используется const_cast в C++?::`const_cast` убирает или добавляет квалификатор `const` к переменной.

Q: Чем отличается l-value от r-value?::l-value имеет адрес в памяти и может быть изменено, а r-value — это временное значение без адреса.
Что такое виртуальная функция? :: Виртуальная функция — это функция, объявленная с ключевым словом `virtual` в базовом классе, которая может быть переопределена в производных классах. Это позволяет определить вызов функции во время выполнения (полиморфизм).

Какая ключевая особенность виртуальной функции? :: Вызов виртуальной функции определяется во время выполнения (runtime polymorphism).

Почему базовый класс должен иметь виртуальный деструктор? :: Чтобы гарантировать корректное освобождение ресурсов производного класса при удалении объекта через указатель на базовый класс.

Что такое перегрузка функций? :: Перегрузка функций — это создание нескольких функций с одинаковым именем, но разными параметрами. Это определяется на этапе компиляции.

Что такое переопределение функций? :: Переопределение функций — это предоставление новой реализации виртуальной функции базового класса в производном классе. Это определяется во время выполнения.

В чем разница между перегрузкой и переопределением функций? :: Перегрузка функций происходит на этапе компиляции и основывается на различиях в сигнатурах функций. Переопределение происходит на этапе выполнения и требует использования ключевого слова `virtual` в базовом классе.

Какие основные случаи использования виртуальных функций? :: Реализация полиморфизма для обработки объектов разных типов через общий интерфейс. Определение интерфейсов или базовых классов для наследования.
<!--SR:!2025-01-01,3,254-->

Что такое чисто виртуальная функция? :: Чисто виртуальная функция — это функция в базовом классе, которая не имеет реализации и должна быть реализована в производных классах. Она объявляется с помощью `= 0` в определении функции.

Для чего нужен виртуальный деструктор? :: Виртуальный деструктор обеспечивает корректный порядок вызова деструкторов при удалении объекта производного класса через указатель на базовый класс. Сначала должен вызваться деструктор производного класса, а потом базового.
<!--SR:!2025-01-01,3,254-->

Что такое обработка исключений в C++? :: Обработка исключений — это механизм управления ошибками или неожиданными ситуациями в программе с помощью конструкции `try`, `catch` и `throw`.

Каковы ключевые особенности обработки исключений? :: Исключения используются для обработки критических ошибок. Не рекомендуется выбрасывать исключения в конструкторах или деструкторах.

Что такое виртуальная функция и как она используется для реализации полиморфизма? :: Виртуальная функция — это функция, объявленная с ключевым словом `virtual` в базовом классе. Она используется для реализации полиморфизма, позволяя производным классам переопределять поведение функции. Вызов такой функции определяется во время выполнения, что позволяет обрабатывать объекты производных классов через указатели или ссылки на базовый класс.
<!--SR:!2025-01-01,3,254-->

Как работает виртуальная таблица (vtable) в C++? :: Виртуальная таблица — это структура данных, создаваемая компилятором для управления вызовами виртуальных функций. Каждый класс с виртуальными функциями имеет свою таблицу vtable, содержащую указатели на функции, доступные для данного класса. При вызове виртуальной функции программа обращается к vtable для определения, какую функцию вызывать во время выполнения.
<!--SR:!2025-01-01,3,254-->

Какие ограничения и риски связаны с использованием виртуальных функций? :: Виртуальные функции увеличивают размер объектов класса за счет добавления указателя на vtable. Кроме того, их использование может снизить производительность из-за косвенного вызова функции. Также неправильное управление памятью, например, отсутствие виртуального деструктора, может привести к утечкам памяти.
<!--SR:!2025-01-01,3,254-->

Почему виртуальный деструктор важен при использовании виртуальных функций? :: Если базовый класс с виртуальными функциями не имеет виртуального деструктора, удаление объекта производного класса через указатель на базовый класс приведет к вызову только деструктора базового класса. Это может привести к утечкам памяти или неправильному освобождению ресурсов.

Что произойдет, если класс с чисто виртуальной функцией не реализует её в производных классах? :: Если производный класс не реализует чисто виртуальную функцию, он также станет абстрактным классом и не может быть инстанцирован. Чтобы использовать такой класс, все чисто виртуальные функции должны быть реализованы.
<!--SR:!2025-01-01,3,254-->

Как перегрузка функций отличается от переопределения в контексте наследования? :: Перегрузка функций происходит внутри одного класса, где методы имеют одинаковое имя, но разные параметры. Переопределение происходит в наследуемом классе, где производный класс предоставляет новую реализацию виртуальной функции базового класса.

Что произойдет, если объявить функцию виртуальной в базовом классе, но не использовать override в производном? :: Если в производном классе не используется `override`, функция все равно переопределит виртуальную функцию базового класса. Однако отсутствие `override` может привести к ошибкам, если сигнатура функции изменена случайно.

Что такое множественное наследование, и как виртуальные функции влияют на него? :: Множественное наследование — это механизм, позволяющий классу наследоваться от нескольких базовых классов. Если в обоих базовых классах есть виртуальные функции с одинаковыми именами, производный класс должен явно указать, какую реализацию использовать, чтобы избежать конфликта.

Как чисто виртуальная функция может иметь реализацию? :: Хотя чисто виртуальная функция определяется с `= 0`, её можно реализовать в базовом классе. Производные классы по-прежнему обязаны переопределять её, но базовый класс может предоставить общую реализацию, которую производные могут вызвать.

Что произойдет, если вызвать виртуальную функцию из конструктора базового класса? :: Если виртуальная функция вызывается из конструктора базового класса, будет вызвана её версия из базового класса, даже если производный класс переопределяет эту функцию. Это связано с тем, что во время вызова конструктора производный объект еще не создан.

Что такое final для виртуальных функций и классов? :: Ключевое слово `final` запрещает дальнейшее переопределение виртуальной функции или наследование от класса. Если функция помечена как `final`, компилятор выдаст ошибку при попытке её переопределить.

Как виртуальные функции влияют на производительность программы? :: Виртуальные функции могут немного снижать производительность из-за необходимости косвенного вызова через vtable. Однако эта потеря обычно незначительна по сравнению с преимуществами, которые дают полиморфизм и гибкость дизайна.

Что такое виртуальный конструктор, и существует ли он в C++? :: Виртуальные конструкторы не поддерживаются в C++, так как конструкторы не могут быть виртуальными. Однако паттерн "виртуального конструктора" можно реализовать с помощью фабричных методов, которые возвращают указатели на базовый класс.

Как происходит разрешение конфликтов при использовании виртуальных функций в случае множественного наследования? :: При множественном наследовании, если виртуальная функция определена в нескольких базовых классах, производный класс должен явно переопределить функцию или указать, какую версию использовать, чтобы избежать неопределенности.
<!--SR:!2025-01-01,3,254-->

Какие проблемы могут возникнуть при передаче исключений через виртуальные функции? :: Если виртуальная функция выбрасывает исключение, производный класс обязан соблюдать те же спецификации исключений или более ограниченные. Нарушение этого правила может привести к неопределенному поведению или ошибкам компиляции.

Почему важно использовать ключевое слово override? :: Ключевое слово `override` позволяет компилятору проверить, переопределяет ли функция виртуальную функцию базового класса. Это помогает избежать ошибок, связанных с неправильной сигнатурой или орфографическими ошибками.

Что произойдет, если в базовом классе виртуальная функция будет приватной? :: Виртуальная функция может быть приватной, но она по-прежнему может быть переопределена в производном классе. Однако доступ к ней из объектов базового класса будет невозможен напрямую.

Что такое объектный срез (object slicing), и как виртуальные функции помогают его избежать? :: Объектный срез происходит, когда объект производного класса копируется в переменную базового класса, теряя данные и методы производного класса. Виртуальные функции помогают избежать среза, так как они позволяют вызывать функции производного класса через указатель или ссылку на базовый класс.
<!--SR:!2024-12-30,1,234-->

Чем отличается класс от структуры?::Класс по умолчанию имеет private доступ к членам, а структура — public. Также тип наследования у классов private, а у структур — public, если явно не указано иное.  

Что такое интерфейс класса?::Интерфейс класса — это всё, что позволяет взаимодействовать с классом извне, например, функции и методы с модификатором доступа public. Это точка контакта между внутренней реализацией и внешним использованием объекта.  

Почему стоит разделять декларацию и реализацию?::Разделение декларации и реализации улучшает читаемость кода, уменьшает его связанность и соответствует принципу разделения интерфейсов (Interface Segregation). Это также упрощает внесение изменений в код без затрагивания внешнего интерфейса.  

Зачем m_arr и m_size имеют модификатор private?::Чтобы предотвратить прямое изменение их значений извне. Это обеспечивает согласованность внутреннего состояния объекта, так как изменение m_arr или m_size напрямую могло бы нарушить логику фиксированного размера массива.  

Что такое std::size_t и зачем он используется?::std::size_t — это беззнаковый тип, определённый в заголовке <cstddef>. Он используется для хранения индексов и размеров, так как может представлять наибольший поддерживаемый системой размер памяти.  

Что делает конструктор FixedSizeArray(std::size_t size)?::Создаёт массив фиксированного размера size, выделяя память в куче (heap), но не инициализирует элементы массива, оставляя их в неинициализированном состоянии.  

Что делает конструктор FixedSizeArray(std::size_t size, int val)?::Создаёт массив фиксированного размера size, выделяя память в куче (heap), и инициализирует все элементы массива значением val, проходя по ним в цикле.  

Для чего служит метод size()?::Метод size() возвращает размер массива, позволяя пользователю узнать количество элементов без доступа к внутренним полям объекта.  

Почему operator[] возвращает ссылку?::Возврат ссылки позволяет не только читать, но и изменять элементы массива напрямую через оператор. Если бы возвращался не ссылочный, а временный объект (r-value), то невозможно было бы присваивать новые значения элементам массива.  

Почему operator[] перегружен для const и non-const объектов?::Const-версия используется, чтобы обеспечить доступ к элементам массива для константных объектов, возвращая ссылку на неизменяемые данные. Non-const-версия позволяет изменять элементы массива для неконстантных объектов.  

Что делает деструктор FixedSizeArray?::Деструктор освобождает память, выделенную для массива в куче, чтобы предотвратить утечки памяти. Он вызывается автоматически при удалении объекта или выходе из его области видимости.
<!--SR:!2025-01-01,3,254-->

Что делает конструктор копирования FixedSizeArray?::Конструктор копирования создаёт новый массив того же размера, что и у переданного объекта, и копирует в него содержимое другого массива. Это позволяет избежать ситуации, когда два объекта ссылаются на один и тот же участок памяти.  

Почему нужен конструктор копирования?::Без конструктора копирования при копировании объекта создаётся дублирующая ссылка на один и тот же участок памяти. Это может привести к двойному освобождению памяти при удалении объектов, что является undefined behavior.  

Почему в деструкторе используется delete[]?::Память для массива выделяется через new[], поэтому для корректного освобождения памяти используется delete[], чтобы избежать неопределённого поведения.  

Чем отличается конструктор копирования от присваивания?::Конструктор копирования создаёт новый объект на основе существующего, тогда как оператор присваивания переписывает данные уже существующего объекта другим объектом, возможно освобождая ресурсы перед этим.  

Почему нельзя обойтись без const для size()?::Без const метод size() не мог бы вызываться для константных объектов, ограничивая гибкость и правильность использования класса.  

Почему FixedSizeArray нельзя копировать без конструктора копирования?::Без конструктора копирования массивы внутри объектов не копировались бы корректно, что могло бы привести к разделению одной памяти между объектами и к последующим проблемам, например, двойному освобождению.  

Что произойдёт, если забыть про деструктор в FixedSizeArray?::Если забыть про деструктор, память, выделенная под массив, не будет освобождена, что приведёт к утечке памяти (memory leak).
<!--SR:!2025-01-01,3,254-->

Почему важно правильно реализовывать деструктор?::Правильная реализация деструктора обеспечивает освобождение ресурсов, предотвращая утечки памяти и других ресурсов, используемых объектом.  

Что будет, если оператор operator[] не возвращает ссылку?::Если оператор operator[] возвращает не ссылку, а значение, то невозможно будет изменить элементы массива, так как вернётся временный (r-value) объект.  

Какая альтернатива перегрузке operator[] для const и non-const объектов?::Альтернатива — не предоставлять доступ к элементам для константных объектов, но это ограничит функциональность класса, делая его менее универсальным.  

Почему нельзя использовать конструктор FixedSizeArray(std::size_t size, int val) для инициализации объекта с пустым массивом?::Конструктор требует значения val, чтобы заполнить массив, поэтому он не подходит для создания массива без значений.  

Чем опасен вызов delete для m_arr, если память не была выделена?::Вызов delete для указателя, который не указывает на валидный участок памяти, приводит к неопределённому поведению, что может вызвать сбои программы.  

Что делает FixedSizeArray(const FixedSizeArray& other) при копировании объекта?::Создаёт новый массив с таким же размером и копирует элементы из массива объекта other в новый массив, чтобы они были независимы.  

Почему FixedSizeArray(const FixedSizeArray& other) выделяет новую память?::Чтобы каждый объект имел свою собственную память, предотвращая конфликты при модификации данных и освобождении памяти.  

Что будет, если забыть о конструкторе FixedSizeArray(const FixedSizeArray& other)?::Копирование объекта будет происходить автоматически, с копированием указателя, что приведёт к разделению памяти между объектами и вызовет ошибки при удалении.  

Чем отличается деструктор от конструктора?::Конструктор инициализирует объект, выделяя ресурсы, тогда как деструктор освобождает ресурсы, завершая жизненный цикл объекта.  

Почему перегрузка operator[] безопаснее, чем прямой доступ к m_arr?::Перегрузка operator[] позволяет проверять корректность индекса, в отличие от прямого доступа, который может вызвать ошибку при некорректных значениях индекса.
<!--SR:!2025-01-01,3,254-->

Почему важно проверять индексы в методе operator[]?::Неправильный индекс может привести к выходу за пределы массива и вызвать undefined behavior, что может повредить данные или привести к сбоям.  

Какие проблемы могут возникнуть, если не написать const версию operator[]?::Const объекты не смогут обращаться к элементам массива, что сделает использование класса неудобным и ограничит его применимость.  

Почему FixedSizeArray использует new и delete?::Класс должен выделять память динамически, так как размер массива известен только во время выполнения, а для этого используются new и delete.  

Что делает оператор = по умолчанию в FixedSizeArray?::Оператор = по умолчанию копирует указатели на массив, но не данные, что приводит к совместному использованию памяти между объектами и потенциальным ошибкам.  

Почему std::size_t лучше для индексов, чем int?::std::size_t является беззнаковым типом, поэтому он гарантирует отсутствие отрицательных значений и лучше подходит для работы с размерами и индексами массивов.  

Что произойдёт, если не реализовать правильный конструктор копирования?::Объекты будут делить одну и ту же память, что вызовет ошибки при их удалении, так как память будет освобождена дважды.  

Почему FixedSizeArray использует delete[] в деструкторе?::Потому что массив был выделен с помощью new[], а для освобождения массивов используется delete[].  

Какой размер массива создаст FixedSizeArray(std::size_t size)?::Он создаст массив длиной size, выделив память в куче.  

Почему FixedSizeArray нельзя использовать как контейнер с динамическим изменением размера?::Класс предназначен для работы с фиксированным размером массива, и его структура не поддерживает изменение размера массива после создания.  

