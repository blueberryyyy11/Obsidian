
## 1. C++ Basics: References, Pointers, Memory Segments, and Operators

 ==References and Pointers==
	
| **`*` (Указатели)**          | **`&` (Ссылки и адреса)**                |
| ---------------------------- | ---------------------------------------- |
| `int *x;`                    | `int &x = y;`                            |
| **Указатель** на переменную. | **Ссылка** на переменную.                |
| `int *x = new int{5};`       | `int y = 10;`                            |
| `std::cout << *x;`           | `&y;` (Получение адреса переменной `y`). |
| **Разыменование** указателя. | **Адрес** переменной.                    |

```cpp
int x = 5;       // Объявление переменной x и инициализация значением 5
int& y = x;      // Ссылка y на переменную x
int* ptr = &x;   // Указатель ptr, указывающий на адрес переменной x
```
+---------+         +---------+
|   x, y  | ----->  |    5    |  // Значение 5
+---------+         +---------+
      ^
      |
+---------+
|   ptr   | ----->  // Указывает на адрес x
+---------+


- **Ссылка**: Это алиас (другое имя) для переменной. Ссылка должна быть инициализирована и не может быть null.
    ```cpp
    int x = 5; 
	int& ref = x; // ref — это ссылка на x
    ```
- **Указатель**: Переменная, которая хранит адрес памяти другой переменной.
    ```cpp
    int x = 10;
    int* ptr = &x; // ptr stores the address of x
    *ptr; // Dereferencing
    ptr = nullptr; // Null pointer
```
 
	
```cpp
void f(int* &p) { 
    // Используем &, чтобы передать ptr в функцию по ссылке, p станет другим именем для ptr
    p = new int{5}; // В heap создается участок памяти типа int со значением 5
                    // После возврата из функции p исчезнет, но ptr в main останется
	}
	int main() {
	    int* ptr;
	    f(ptr);        
	    std::cout << *ptr; // 5        
	    return 0;
	    }	
```


```cpp
// если переменная уже объявлена
int* x = new int{5};

std::cout << * x;  // dereference (обращение к куску памяти, на который ссылается, указывает переменная)
```
  
- если создать переменную и писать * слева от имени переменной - это **указатель**  
  
- если создать переменную и слева писать & - это **ссылка**  
  
- если переменная УЖЕ создана и писать * слева от имени переменной - это **dereference** 
- переменная УЖЕ создана и слева писать & - это **адрес** данной переменной

```cpp
int y = 10;
int* x = &y; (так как * стоит при создании переменной - это указатель
              так как y уже создан, то & - это не референс, а адрес
              то есть х есть указатель на у)
```

```cpp
void f(int* &p) { 
    *p = 5 // т.к p - это другое имя для ptr и мы не знаем на какой адрес ptr указывало (а этот кусок памяти может вообще быть не из нашей программы), то так писать НЕЛЬЗЯ
}

int main()
{
    int* ptr; // ptr - это указатель, но мы не знаем на какой кусок памяти он указывает
    
    f(ptr);
    
    std::cout << * ptr; //5

    return 0;
}
```

```cpp
void f(int* &p) { 
    int x = 5;
    p = &x;
}
// если так написать, то после возвращения из функции переменная х удалится и это может привести к undefined behavior

int main()
{
    int* ptr; // ptr - это указатель, но мы не знаем на какой кусок памяти он указывает
    
    f(ptr);
    
    std::cout << * ptr; //5

    return 0;
}
```
 
 ==**Сегменты памяти: Stack и Heap**
- **Стековая память (Stack)**: Автоматически выделяется и освобождается. Используется для локальных переменных и вызовов функций.
- **Куча (Heap)**: Память выделяется динамически с помощью `new` и освобождается с помощью `delete`.
    ```cpp
	int* p = new int(10); // Память выделяется в куче
	delete p;             // Память освобождается

    ```

==Function Overloading and Default Parameters==
**Function Overloading**
***когда несколько функций имеют одинаковое имя, но различное число или тип аргументов***

**Example:**
```cpp
int add(int a, int b);      // Function that adds two integers

double add(double a, double b); // Function that adds two doubles

int min(int a, int b) {
    return a < b ? a : b;  // тернарный оператор
}

int min(int a, int b, int c){
    return min(min(a,b), c);
}

double min(double a, double b){
    return a < b ? a : b;
}

// кто-то сказал можно и с template, но это на потом

int main() {
    int x;
    int y;
    std::cin >> x >> y;
    std::cout << min(x, y);
    
    int z;
    std::cin >> z;
    std::cout << min(x,y,z);
    return 0;
}
```

***ВАЖНО:***
- НО нельзя проводить перегрузку функций, которые отличаются лишь возвращаемым типом
	```cpp
	int func(int a);
	double func(int a); // Ошибка
	```
	
	могут ли быть две функции с одинаковым названием, с одинаковым числом аргументов, с одинаковым типом аргументов, но с различными возвращаемыми типами  
	  
	ответ:  
	могут, 
	- **Ковариантные типы возврата в виртуальных функциях**:
		```cpp
		class Base {
		public:
		    virtual Base* clone() const;
		};
		
		class Derived : public Base {
		public:
		    Derived* clone() const override; // Разный возвращаемый тип
		};
		```
    
- **Шаблонные функции и специализации**:
	```cpp
	template <typename T>
	void bar(T t);
	
	void bar(int x); // Специализация

```
    
- **Разные пространства имен**:
	```cpp
	namespace A { void func(int); }
	namespace B { double func(int); }

```
    
- **Перегрузка оператора вызова функций (`operator()`)**.
    

---

==**Параметры по умолчанию**==
Параметры по умолчанию задаются при объявлении функции. Если аргумент не указан, используется значение по умолчанию.

**Пример:**
```cpp
void greet(const std::string& name = "Guest") {
    std::cout << "Hello, " << name << "!\n";
}

int main() {
    greet();        // Hello, Guest!
    greet("John");  // Hello, John!
    return 0;
}

```

---
**Example of Conflict:**
```
void print(int x, int y = 10); // Function with default parameter
void print(int x);            // Overloaded function

int main() {
    print(5); // Error: Ambiguity, compiler cannot decide which version to call
    return 0;
}
```


==***l-value vs r-value***==
- **l-value**: это то выражение, которое ХОТЬ ОДНАЖДЫ может оказаться слева от знака =.
- **r-value**: это то выражение, которое ЛИШЬ может оказаться справа от знака =.
    ```cpp
    int x = 10;   // x is an l-value, 10 is an r-value 
    int&& r = 20; // r binds to r-value 20
    ```


---
==**достаточное но не необходимое условие, чтобы быть l-value**: ==
если у выражения есть имя, то оно 100% l-value
но может не иметь имени и все равно быть l-value, нпр dereference *ptr

```cpp
int postfix(int& x) // эта функция делает то же самое что и х++
{
    int y = x;
    x += 1;
    return y;
}

int prefix(int& x) 
{
    x += 1;
    return x;
}

int main(){
    int x = 10;
    x++; // r-value
    ++x; // l-value
}
```

у каждого выражения в с++ есть **тип, значение и побочный эффект**
например :  
  
1. **x++**  
тип: int  
значение: старое значение х (до инкремента)  
побочный эффект: увеличение на единицу  
  
2. **++x**  
тип: int  
значение: новое значение х (после инкремента)  
побочный эффект: увеличение на единицу

3. **х = y** : l-value  
как проверить? брать и приравнять к чему-то  
  
среди всех бинарных операций оператор = работает справа на лево  
x = y = 15 - сначала приравнивает у, а потом х  
  
4. **x + y**: r-value  
никак не может оказаться слева  
  
! const переменные всегда l-value  
  
обычный reference можно создать только и только на l-value  
а const reference можно


## **2. Object-Oriented Programming (OOP) in C++**

OOP is a programming paradigm that uses objects and classes to model real-world problems. It includes the following core principles:

==1. ***Core Concepts***==

1. **Encapsulation**:
    - Combines data and functions into a single unit (class/struct).
    - Access to data is controlled using access specifiers (`public`, `private`, `protected`).
    
2. **Inheritance**:
    
    - Allows one class to derive (inherit) properties and behavior from another class.
    - Example:
	     ```cpp
	    class Base {     
	    public: 
		    int x;        
		}; 
		class Derived : public Base {     
		public:         
			void show() { std::cout << x; } 
		};`
```
        
3. **Polymorphism**:
    
    - Allows methods to behave differently based on the object (e.g., method overriding).
    - Achieved using virtual functions.
        ```cpp
        class Base {     
        public:         
	        virtual void print() { std::cout << "Base"; } 
		}; 
		
		class Derived : public Base {     
		public:         
			void print() override { std::cout << "Derived"; } 
		};
```
         
4. **Abstraction**:
    
    - Hides complexity by exposing only the essential details.
    - Achieved using abstract classes or interfaces (pure virtual functions).

---
==2. ***Structs in C++***==
- A `struct` is a user-defined type in C++ that groups data together.
- Unlike in C, in C++ a `struct` can have **member functions**, **access specifiers**, and **constructors**.

**Default Access Modifier**
- The default access in a `struct` is `public`.
- Example:
	```cpp
	struct Point {
    int x, y;

    void display() {
        std::cout << "x: " << x << ", y: " << y << std::endl;
    }
};

```
    

**Difference Between Class and Struct**

|**Struct**|**Class**|
|---|---|
|Default access is `public`.|Default access is `private`.|
|Typically used for simpler data structures.|Used for more complex, OOP-based designs.|
|Less overhead conceptually.|Fully OOP-focused.|

---
==3. ***Member Variables and Member Functions***

**Member Variables**
- Variables declared inside a class/struct.
- Represent the state of the object.

**Member Functions**
- Functions defined in the class/struct.
- Represent the behavior of the object.

**Access Specifiers**
- `public`: Accessible from anywhere.
- `private`: Accessible only within the class/struct.
- `protected`: Accessible within the class and its derived classes.

Example:
```cpp
struct Circle {     
	double radius; // Member variable      
	double area() { // Member function         
		return 3.14 * radius * radius;     
	} 
};
```
---

==***4. Constructors***==
Constructors are special member functions called automatically when an object is created.

**Default Constructor**
- A constructor with no parameters.
- If no constructor is defined, C++ provides a default constructor.
- Example:
```cpp
    class Box {     
	    public:         
	    Box() { std::cout << "Default Constructor called"; } 
	};`
```

**Constructor with Parameters**
- Allows initializing member variables with specific values.
- Example:
  ```cpp
  class Rectangle {     
	  int width, height;      
  public:         
	  Rectangle(int w, int h) : width(w), height(h) {}         
	  int area() { return width * height; } 
  };
```

**Constructor Overloading**
- Multiple constructors with different parameter lists.
- Example:
	```cpp
	class Shape {     
		int x, y;      
	public:         
	Shape() : x(0), y(0) {}         
	Shape(int a, int b) : x(a), y(b) {} };
```
---
### ==5. **Operator Overloading**==
- Operators in C++ can be redefined for user-defined types.
- Example: Overloading the `+` operator for adding two objects.

**Syntax**
```cpp
ReturnType operatorSymbol(Arguments) { /* Implementation */ }`
```

**Rules**
1. You cannot overload `sizeof`, `::`, `.*`, `.` (direct member selection), or `typeid`.
2. At least one operand must be a user-defined type.
3. Overloading does not change operator precedence.

```cpp
#include <iostream>
using namespace std;

class Demo {
private:
    int value;

public:
    // Constructor
    Demo(int val = 0) : value(val) {}

    // 1. Arithmetic Operators (+, -, *, /)
    Demo operator+(const Demo& obj) {
        return Demo(value + obj.value);
    }

    Demo operator-(const Demo& obj) {
        return Demo(value - obj.value);
    }

    Demo operator*(const Demo& obj) {
        return Demo(value * obj.value);
    }

    Demo operator/(const Demo& obj) {
        if (obj.value == 0) {
            throw runtime_error("Division by zero!");
        }
        return Demo(value / obj.value);
    }

    // 2. Comparison Operators (==, !=, <, >, <=, >=)
    bool operator==(const Demo& obj) {
        return value == obj.value;
    }

    bool operator!=(const Demo& obj) {
        return value != obj.value;
    }

    bool operator<(const Demo& obj) {
        return value < obj.value;
    }

    bool operator>(const Demo& obj) {
        return value > obj.value;
    }

    bool operator<=(const Demo& obj) {
        return value <= obj.value;
    }

    bool operator>=(const Demo& obj) {
        return value >= obj.value;
    }

    // 3. Increment/Decrement Operators (++, --)
    // Prefix
    Demo& operator++() {
        ++value;
        return *this;
    }

    // Postfix
    Demo operator++(int) {
        Demo temp = *this;
        value++;
        return temp;
    }

    Demo& operator--() {
        --value;
        return *this;
    }

    Demo operator--(int) {
        Demo temp = *this;
        value--;
        return temp;
    }

    // 4. Logical Operators (!, &&, ||)
    bool operator!() {
        return value == 0;
    }

    bool operator&&(const Demo& obj) {
        return value && obj.value;
    }

    bool operator||(const Demo& obj) {
        return value || obj.value;
    }

    // 5. Bitwise Operators (&, |, ^, ~, <<, >>)
    Demo operator&(const Demo& obj) {
        return Demo(value & obj.value);
    }

    Demo operator|(const Demo& obj) {
        return Demo(value | obj.value);
    }

    Demo operator^(const Demo& obj) {
        return Demo(value ^ obj.value);
    }

    Demo operator~() {
        return Demo(~value);
    }

    Demo operator<<(int shift) {
        return Demo(value << shift);
    }

    Demo operator>>(int shift) {
        return Demo(value >> shift);
    }

    // 6. Assignment Operators (=, +=, -=, *=, /=, etc.)
    Demo& operator=(const Demo& obj) {
        if (this != &obj) {
            value = obj.value;
        }
        return *this;
    }

    Demo& operator+=(const Demo& obj) {
        value += obj.value;
        return *this;
    }

    Demo& operator-=(const Demo& obj) {
        value -= obj.value;
        return *this;
    }

    Demo& operator*=(const Demo& obj) {
        value *= obj.value;
        return *this;
    }

    Demo& operator/=(const Demo& obj) {
        if (obj.value == 0) {
            throw runtime_error("Division by zero!");
        }
        value /= obj.value;
        return *this;
    }

    // 7. Subscript Operator ([])
    int operator[](int index) {
        // A simple example: return index multiplied by value
        return value * index;
    }

    // 8. Function Call Operator (())
    void operator()(int factor) {
        value *= factor;
    }

    // 9. Stream Operators (<<, >>)
    friend ostream& operator<<(ostream& out, const Demo& obj) {
        out << obj.value;
        return out;
    }

    friend istream& operator>>(istream& in, Demo& obj) {
        in >> obj.value;
        return in;
    }

    // 10. Pointer Dereference (*)
    int operator*() {
        return value;
    }
};

int main() {
    Demo a(10), b(20), c;

    // Arithmetic operators
    c = a + b;
    cout << "a + b = " << c << endl;
    c = a - b;
    cout << "a - b = " << c << endl;

    // Comparison operators
    cout << "a == b: " << (a == b) << endl;
    cout << "a != b: " << (a != b) << endl;

    // Increment/Decrement
    ++a;
    cout << "++a: " << a << endl;
    a++;
    cout << "a++: " << a << endl;

    // Logical operators
    cout << "a && b: " << (a && b) << endl;
    cout << "!a: " << !a << endl;

    // Bitwise operators
    c = a & b;
    cout << "a & b: " << c << endl;
    c = a | b;
    cout << "a | b: " << c << endl;

    // Assignment operators
    a += b;
    cout << "a += b: " << a << endl;

    // Subscript operator
    cout << "a[2]: " << a[2] << endl;

    // Function call operator
    a(3);
    cout << "a(3): " << a << endl;

    // Stream operators
    cout << "Enter a value for c: ";
    cin >> c;
    cout << "You entered: " << c << endl;

    // Pointer dereference
    cout << "*c: " << *c << endl;

    return 0;
}

```
---
**Key Notes**
- **Struct and Class Differences**:
    - Remember default access levels and typical use cases.
- **Constructors**:
    - Understand default constructors, parameterized constructors, and constructor overloading.
- **Operator Overloading**:
    - Focus on how to overload arithmetic and comparison operators.
    - Know the rules of operator overloading (e.g., at least one operand must be user-defined).OP


## **3. Function/class templates, Basic implementation of a fixed size array in C++, destructor, copy constructor, assignment operator, private/public/protected, classes, class vs struct, const member functions.**
	
## Function/Class Templates
Templates allow creating generic classes or functions that work with any data type.

**==Function Templates==**
```cpp
#include <iostream>

// Function Template
template <typename T>
T add(T a, T b) {
	return a + b;
}

int main() {
	std::cout << add<int>(5, 10) << std::endl;   // 15
	std::cout << add<double>(5.5, 10.1) << std::endl; // 15.6
	return 0;
}
```

**==Class Templates==**
```cpp
#include <iostream>

// Class Template
template <typename T>
class Box {
private:
	T value;

public:
	Box(T v) : value(v) {}

	T getValue() const {
		return value;
	}
};

int main() {
	Box<int> intBox(123);
	Box<std::string> strBox("Hello");

	std::cout << intBox.getValue() << std::endl;   // 123
	std::cout << strBox.getValue() << std::endl;  // Hello
	return 0;
}
```

**==Специализация шаблона==**

Специализация шаблона позволяет изменять или настраивать стандартное поведение шаблона для конкретного типа данных.

*Что это значит*

Когда вы создаете шаблон, он обычно обрабатывает все типы одинаковым образом. Однако, иногда для определенных типов данных требуется особое поведение. В таких случаях используется **специализация шаблона**, которая предоставляет уникальную реализацию для конкретного типа.

---

**Пример шаблона**
```cpp
template<typename T>
class Example {
public:
    void show() {
        std::cout << "General template" << std::endl;
    }
};
```
Этот шаблон обрабатывает любой тип `T`, выводя "General template".

**Пример специализации**
```cpp
// Специализация для int
template<>
class Example<int> {
public:
    void show() {
        std::cout << "Specialized template for int" << std::endl;
    }
};

```
теперь:
```cpp
Example<double> obj1;
obj1.show(); // Вывод: General template

Example<int> obj2;
obj2.show(); // Вывод: Specialized template for int

```

***Что происходит в памяти***

- **Общий шаблон**: Компилятор генерирует один набор инструкций для обработки любого типа.
- **Специализация**: Компилятор создает отдельную реализацию для типа `int`, которая отличается от стандартного поведения.
---

**==Fixed-Size Array Implementation in C++==**
```cpp
#include <iostream>

template <typename T, size_t N>
class FixedArray {
private:
	T data[N];

public:
	T& operator[](size_t index) {
		if (index >= N) throw std::out_of_range("Index out of bounds");
		return data[index];
	}

	const T& operator[](size_t index) const {
		if (index >= N) throw std::out_of_range("Index out of bounds");
		return data[index];
	}

	size_t size() const {
		return N;
	}
};

int main() {
	FixedArray<int, 5> arr;

	for (size_t i = 0; i < arr.size(); ++i) {
		arr[i] = i * 2;
	}

	for (size_t i = 0; i < arr.size(); ++i) {
		std::cout << arr[i] << " ";
	}
	return 0;
}
```

---

## Destructor, Copy Constructor, and Assignment Operator

**==Destructor==**
- A special member function used to release resources when an object is destroyed.
```cpp
class MyClass {
public:
	~MyClass() {
		std::cout << "Destructor called" << std::endl;
	}
};
```

**==Copy Constructor==**
- Creates a new object as a copy of an existing object.
```cpp
class MyClass {
private:
	int value;

public:
	MyClass(int v) : value(v) {}

	// Copy Constructor
	MyClass(const MyClass& other) : value(other.value) {
		std::cout << "Copy Constructor called" << std::endl;
	}
};
```

**==Assignment Operator==**
- Assigns the values from one object to another after both have been created.
```cpp
class MyClass {
private:
	int value;

public:
	MyClass(int v) : value(v) {}

	// Assignment Operator
	MyClass& operator=(const MyClass& other) {
		if (this != &other) {
			value = other.value;
		}
		std::cout << "Assignment Operator called" << std::endl;
		return *this;
	}
};
```

---

## Access Specifiers: Private, Public, Protected

**==Public==**
- Members are accessible from outside the class.
```cpp
class MyClass {
public:
	int value;
};
```

**==Private==**
- Members are accessible only within the class.
```cpp
class MyClass {
private:
	int value;
};
```

**==Protected==**
- Members are accessible within the class and its derived classes.
```cpp
class Base {
protected:
	int value;
};
```

---

## Classes vs. Structs
- **Class**: Members are private by default.
- **Struct**: Members are public by default.
```cpp
class MyClass {
private:
	int value;
};

struct MyStruct {
public:
	int value;
};
```

---

## Const Member Functions
- Functions that do not modify the state of the object.
```cpp
class MyClass {
private:
	int value;

public:
	MyClass(int v) : value(v) {}

	int getValue() const {
		return value;
	}

	void setValue(int v) {
		value = v;
	}
};
```




### **4. l-value/r-value references, std::move, move constructor, move assignment operator, Type casting in c++: static_cast, reinterpret_cast, const_cast.**
## l-value и r-value

**==l-value==**
- **Определение**: l-value (left value) — это объект, который занимает определённое место в памяти и имеет адрес.
- **Примеры**:
  ```cpp
  int x = 10; // x — это l-value
  int& ref = x; // Ссылка на l-value
  ```
- **Особенности**:
  - l-value всегда можно использовать как левую часть присваивания (`=`).
  - l-value имеет продолжительное время жизни.

**==r-value==**
- **Определение**: r-value (right value) — это временное значение, которое не имеет адреса в памяти (например, литералы или результат выражений).
- **Примеры**:
  ```cpp
  int y = 5 + 3; // 5 + 3 — это r-value
  ```
- **Особенности**:
  - r-value нельзя использовать как левую часть присваивания.
  - r-value имеет временное время жизни и может быть использовано только один раз.

**==r-value ссылки==
- Использование `T&&` позволяет работать с r-value:
  ```cpp
  void process(int&& temp) {
	  std::cout << temp << std::endl;
  }
  process(5); // Передача r-value
  ```
- r-value ссылки полезны для оптимизации производительности (например, в конструкторах перемещения).

---

## ==std::move==

- **Определение**: `std::move` — это функция, которая преобразует l-value в r-value, позволяя передать временный объект в функции или конструкторы перемещения.
- **Пример**:
  ```cpp
  std::string str = "Hello";
  std::string movedStr = std::move(str); // str теперь пустой
  ```
- **Особенности**:
  - После вызова `std::move` исходный объект теряет свои данные (но остаётся валидным).
  - Используется для оптимизации копирования больших объектов.

---

## ==Конструктор перемещения (move constructor)==

- **Определение**: Конструктор перемещения позволяет передавать ресурсы (например, динамическую память) от одного объекта к другому без копирования.
- **Синтаксис**:
  ```cpp
  class MyClass {
  private:
	  int* data;

  public:
	  MyClass(int value) {
		  data = new int(value);
	  }

	  // Конструктор перемещения
	  MyClass(MyClass&& other) noexcept : data(other.data) {
		  other.data = nullptr; // Обнуляем указатель в исходном объекте
	  }

	  ~MyClass() {
		  delete data;
	  }
  };
  ```
- **Особенности**:
  - Конструктор перемещения вызывается, если объект передаётся как r-value.

---

## ==Оператор присваивания с перемещением (move assignment operator)==

- **Определение**: Оператор перемещающего присваивания используется для переноса ресурсов между объектами.
- **Синтаксис**:
  ```cpp
  MyClass& operator=(MyClass&& other) noexcept {
	  if (this != &other) {
		  delete data;
		  data = other.data;
		  other.data = nullptr;
	  }
	  return *this;
  }
  ```
- **Особенности**:
  - Необходимо очищать текущие ресурсы перед переносом.
  - Обеспечивает защиту от самоприсваивания.

---

## ==Приведение типов в C++ (type casting in c++)==

### static_cast
- **Определение**: Используется для проверяемого преобразования типов во время компиляции.
- **Пример**:
  ```cpp
  double d = 3.14;
  int i = static_cast<int>(d); // Убрана дробная часть
  ```
- **Особенности**:
  - Используется для приведения указателей между базовым и производным классами.

### reinterpret_cast
- **Определение**: Используется для небезопасного преобразования типов.
- **Пример**:
  ```cpp
  int* p = reinterpret_cast<int*>(0x1234);
  ```
- **Особенности**:
  - Позволяет интерпретировать битовое представление одного типа как другого.
  - Используется с осторожностью, так как может привести к неопределённому поведению.

### const_cast
- **Определение**: Убирает или добавляет квалификатор `const` к переменной.
- **Пример**:
  ```cpp
  const int x = 10;
  int& y = const_cast<int&>(x);
  y = 20; // Изменение константного значения
  ```
- **Особенности**:
  - Может использоваться для работы с функциями, которые не принимают `const` параметры.

---
### 5. Virtual functions, function overloading vs function overriding, usage of virtual functions, examples, pure virtual functions, virtual destructors, exception handling.

### ==Виртуальные функции==

==Что такое виртуальная функция?==
- **Определение**: Виртуальная функция — это функция, объявленная с использованием ключевого слова `virtual` в базовом классе, которая может быть переопределена в производных классах.
- **Пример**:
  ```cpp
  class Base {
  public:
      virtual void display() {
          std::cout << "Base class" << std::endl;
      }
  };

  class Derived : public Base {
  public:
      void display() override {
          std::cout << "Derived class" << std::endl;
      }
  };

  int main() {
      Base* basePtr = new Derived();
      basePtr->display(); // Вывод: Derived class
      delete basePtr;
  }
  ```
- **Особенности**:
  - Вызов функции определяется во время выполнения (runtime polymorphism).
  - Базовый класс должен иметь виртуальный деструктор, чтобы избежать утечек памяти.

---

### ==Перегрузка функций vs Переопределение функций==

==Перегрузка функций (Function Overloading)==
- **Определение**: Перегрузка функций — это создание нескольких функций с одним и тем же именем, но с разными параметрами.
- **Пример**:
  ```cpp
  void print(int i) {
      std::cout << "Integer: " << i << std::endl;
  }
  void print(double d) {
      std::cout << "Double: " << d << std::endl;
  }
  ```
- **Особенности**:
  - Происходит на этапе компиляции.
  - Различается по сигнатурам функций.

==Переопределение функций (Function Overriding)==
- **Определение**: Переопределение — это предоставление новой реализации функции в производном классе.
- **Пример**:
  ```cpp
  class Base {
  public:
      virtual void show() {
          std::cout << "Base show" << std::endl;
      }
  };
  class Derived : public Base {
  public:
      void show() override {
          std::cout << "Derived show" << std::endl;
      }
  };
  ```
- **Особенности**:
  - Используется ключевое слово `virtual` в базовом классе.
  - Производный класс может дополнительно использовать `override` для явного указания переопределения.

---

### ==Использование виртуальных функций==
- **Основные случаи применения**:
  - Создание интерфейсов или базовых классов для наследования.
  - Реализация полиморфизма для обработки объектов различных типов через общий интерфейс.

==Пример==
```cpp
class Animal {
public:
    virtual void sound() {
        std::cout << "Some generic animal sound" << std::endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        std::cout << "Woof!" << std::endl;
    }
};

class Cat : public Animal {
public:
    void sound() override {
        std::cout << "Meow!" << std::endl;
    }
};

int main() {
    Animal* a1 = new Dog();
    Animal* a2 = new Cat();

    a1->sound(); // Вывод: Woof!
    a2->sound(); // Вывод: Meow!

    delete a1;
    delete a2;
}
```

---

### ==Чисто виртуальные функции (Pure Virtual Functions)==
- **Определение**: Чисто виртуальная функция — это функция, объявленная в базовом классе, которая не имеет реализации и должна быть реализована в производных классах.
- **Синтаксис**:
  ```cpp
  virtual void functionName() = 0;
  ```
- **Пример**:
  ```cpp
  class Shape {
  public:
      virtual void draw() = 0; // Чисто виртуальная функция
  };

  class Circle : public Shape {
  public:
      void draw() override {
          std::cout << "Drawing Circle" << std::endl;
      }
  };

  class Square : public Shape {
  public:
      void draw() override {
          std::cout << "Drawing Square" << std::endl;
      }
  };
  ```

---

### ==Виртуальные деструкторы==
- **Определение**: Виртуальный деструктор позволяет корректно освобождать ресурсы производных классов через указатели на базовый класс.
- **Пример**:
  ```cpp
  class Base {
  public:
      virtual ~Base() {
          std::cout << "Base destructor" << std::endl;
      }
  };

  class Derived : public Base {
  public:
      ~Derived() {
          std::cout << "Derived destructor" << std::endl;
      }
  };

  int main() {
      Base* obj = new Derived();
      delete obj;
      return 0;
  }
  ```
- **Вывод**:
  - Сначала вызывается деструктор `Derived`.
  - Затем вызывается деструктор `Base`.

---

### ==Обработка исключений (Exception Handling)==

==Что такое исключения?==
- **Определение**: Исключения используются для обработки ошибок или неожиданных ситуаций в программе.

==Синтаксис==
```cpp
try {
    // Код, который может вызвать исключение
} catch (Type& e) {
    // Обработка исключения
} catch (...) {
    // Ловит любые исключения
}
```

==Пример==
```cpp
#include <iostream>
#include <stdexcept>

int divide(int a, int b) {
    if (b == 0) {
        throw std::runtime_error("Division by zero");
    }
    return a / b;
}

int main() {
    try {
        std::cout << divide(10, 2) << std::endl;
        std::cout << divide(10, 0) << std::endl;
    } catch (const std::exception& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
    return 0;
}
```

==Особенности==
- Используйте исключения для критических ошибок.
- Не рекомендуется бросать исключения в конструкторах или деструкторах.
