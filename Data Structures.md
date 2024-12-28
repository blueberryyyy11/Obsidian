
## 1. C++ Basics: References, Pointers, Memory Segments, and Operators

### References and Pointers
	
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
### Сегменты памяти: Stack и Heap

- **Стековая память (Stack)**: Автоматически выделяется и освобождается. Используется для локальных переменных и вызовов функций.
- **Куча (Heap)**: Память выделяется динамически с помощью `new` и освобождается с помощью `delete`.
    ```cpp
	int* p = new int(10); // Память выделяется в куче
	delete p;             // Память освобождается

    ```

### Function Overloading and Default Parameters

#### **Function Overloading**

==когда несколько функций имеют одинаковое имя, но различное число или тип аргументов==

##### **Example:**

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

##### ВАЖНО:
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

#### **Параметры по умолчанию**

Параметры по умолчанию задаются при объявлении функции. Если аргумент не указан, используется значение по умолчанию.

##### **Пример:**
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
##### **Example of Conflict:**

```
void print(int x, int y = 10); // Function with default parameter
void print(int x);            // Overloaded function

int main() {
    print(5); // Error: Ambiguity, compiler cannot decide which version to call
    return 0;
}
```


###  l-value vs r-value

- **l-value**: это то выражение, которое ХОТЬ ОДНАЖДЫ может оказаться слева от знака =.
- **r-value**: это то выражение, которое ЛИШЬ может оказаться справа от знака =.
    ```cpp
    int x = 10;   // x is an l-value, 10 is an r-value 
    int&& r = 20; // r binds to r-value 20
    ```


---
**достаточное но не необходимое условие, чтобы быть l-value**:  
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


##  **2. Object-Oriented Programming (OOP) in C++**

OOP is a programming paradigm that uses objects and classes to model real-world problems. It includes the following core principles:

### 1. **Core Concepts**

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
### 2. Structs in C++
- A `struct` is a user-defined type in C++ that groups data together.
- Unlike in C, in C++ a `struct` can have **member functions**, **access specifiers**, and **constructors**.

### 3. Default Access Modifier

- The default access in a `struct` is `public`.
- Example:
    
    cpp
    
    Copy code
    
    `struct Point {     int x, y;      void display() {         std::cout << "x: " << x << ", y: " << y << std::endl;     } };`
    

### **Difference Between Class and Struct**

|**Struct**|**Class**|
|---|---|
|Default access is `public`.|Default access is `private`.|
|Typically used for simpler data structures.|Used for more complex, OOP-based designs.|
|Less overhead conceptually.|Fully OOP-focused.|

---
### 4. Member Variables and Member Functions
### **Member Variables**

- Variables declared inside a class/struct.
- Represent the state of the object.

### **Member Functions**

- Functions defined in the class/struct.
- Represent the behavior of the object.

### **Access Specifiers**

- `public`: Accessible from anywhere.
- `private`: Accessible only within the class/struct.
- `protected`: Accessible within the class and its derived classes.

### Example:
```cpp
struct Circle {     
	double radius; // Member variable      
	double area() { // Member function         
		return 3.14 * radius * radius;     
	} 
};
```
---
### Constructors
Constructors are special member functions called automatically when an object is created.

### **Default Constructor**

- A constructor with no parameters.
- If no constructor is defined, C++ provides a default constructor.
- Example:
```cpp
    class Box {     
	    public:         
	    Box() { std::cout << "Default Constructor called"; } 
	};`
```

### **Constructor with Parameters**

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

### **Constructor Overloading**

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
### Operator Overloading
- Operators in C++ can be redefined for user-defined types.
- Example: Overloading the `+` operator for adding two objects.

### Syntax
```cpp
ReturnType operatorSymbol(Arguments) { /* Implementation */ }`
```

### Rules

1. You cannot overload `sizeof`, `::`, `.*`, `.` (direct member selection), or `typeid`.
2. At least one operand must be a user-defined type.
3. Overloading does not change operator precedence.

### Example: Overloading `+` Operator
```cpp
class Complex {     
int real, imag;  

public:         
	Complex(int r, int i) : real(r), imag(i) {}          
	Complex operator+(const Complex& c) {             
		return Complex(real + c.real, imag + c.imag);         
	}          
	void display() {             
		std::cout << real << " + " << imag << "i" << std::endl;         
	} 
};
```

### Example: Overloading `==` Operator
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
### Key Notes

- **Struct and Class Differences**:
    - Remember default access levels and typical use cases.
- **Constructors**:
    - Understand default constructors, parameterized constructors, and constructor overloading.
- **Operator Overloading**:
    - Focus on how to overload arithmetic and comparison operators.
    - Know the rules of operator overloading (e.g., at least one operand must be user-defined).OP
