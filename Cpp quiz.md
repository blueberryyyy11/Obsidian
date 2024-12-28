
- Static functions 
   ```cpp
	 #include<iostream> 
	 int foo() { return 10; } 
	 struct foobar { 
		static int x; 
		static int foo() { return 11; } 
	}; 
		int foobar::x = foo(); 
		int main() { 
			std::cout << foobar::x;  // The compiler starts by searching for `foo()` in the immediate scope of the class `foobar`. In this case, it finds `foobar::foo()`, a static member function, so the search stops here. No further lookup is performed. If `foobar::foo()` didn't exist, the compiler would expand the search to the next enclosing scope, which is the global scope in this case. At the global scope, the `foo()` function is defined, so this would be chosen. So the output is 11.
	}
	```
- Copy constructor VS operator= 
  ```cpp
	#include <iostream> 
	struct C { 
		C() { std::cout << "1"; } 
		C(const C& other) { std::cout << "2"; } 
		C& operator=(const C& other) { std::cout << "3"; return *this;} 
	}; 
			
	int main() { 
		C c1; 
		C c2 = c1; // the output is 12
	}
	```
	*if we initialize the object (C c2 = c1) - the copy constructor is called*
	*if both objects already exist (c2 = c1) - the operator= is called.*
- Indeterminately sequenced
	```cpp
	#include <iostream>
	
	void print(int x, int y)
	{
	std::cout << x << y;
	}
	
	int main() {
	
		int i = 0;
		print(++i, ++i);
		return 0;
	
	}
	```
	![[Pasted image 20241228165231.png]]
	> Evaluations _A_ and _B_ are _indeterminately sequenced_ when either _A_ is sequenced before _B_ or _B_ is sequenced before _A_, but it is unspecified which.

	So from the two quotes above we see that they can happen in either order, and importantly that all side effects of the first evaluation (whichever that might be) are guaranteed to be completed before the second one gets evaluated.
	
	Let's say the implementation decides to go left to right. Then the first parameter `x` is initialized by the leftmost expression `++i`, which increments `i` and results in the updated `i` which is now `1`. Next, the second parameter `y` is initialized by the rightmost expression `++i`, which increments `i` and results in the updated `i` which is now `2`. Then, `print` prints `12`.

	Alternatively, the implementation could decide to go right to left, and `print` would print `21`.

	So this is unspecified (but not undefined) behavior, and a conforming implementation can either print `12` or `21`, but not for instance `22`. Interestingly, `22` is what GCC prints at the time of writing, and there's an [open bug](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=78734) for that.
