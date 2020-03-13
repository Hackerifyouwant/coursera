# Object-Oriented Data Structures in C++
###### tags: `C++` `Data structures` `Object-Oriented program` `

**If you want to get this class,following the link!!**
https://www.coursera.org/learn/cs-fundamentals-1

## Week 1
### C++ Intorduction
https://www.coursera.org/learn/cs-fundamentals-1/lecture/IOYcm/1-1-c-introduction
* C++ is a **strongly typed** programming language where every variable has a type,name,value,and location in memory.
#### 1. C++ Types
* The **type** of a variable defines the contents og the variable.Every **type** is either:
    * Primitive
    * User-defined  
#### 2. Primitive Types
* There are just six common primitive types in C++:
    * **int**,store intergers
    * **char**,stores single characters/single byte
    * **bool**,stores a Boolean(true or false)
    * **float**,stores a floating point number
    * **double**,stores a double-precision floating point number   
    * **void**,denotes the absence of a value
#### 3. User-Defined Types
* An unbounded number of user-defined types can exist - we'll create many of our own.
* Two very common user-defined types:
    * **std:string**, a string(sequence of characters)
    * **std::vector**, a dynamically-growing array
### C++ class
https://www.coursera.org/learn/cs-fundamentals-1/lecture/q5Vpx/1-2-c-classes
* **C++ classes** encapsulate data and associated functionality into an **object:**
![](https://i.imgur.com/KvzMJLa.png)
#### 1. Encapsulation
* **Encapsulation** encloses data and functionality into a single unit(called a **class
![](https://i.imgur.com/huSPSM4.png)
#### 2. Encapsulation(public and private)
* In C++,data and functionality are seperated into two seperate protections:**public** and **private**.
![](https://i.imgur.com/xZ4868j.png)
#### 3. Public vs. Private
* The protection level determines the access that **client code** has to the member data of functionality:
    * Public members can be accessed by client code.
    * Private members cannot be accessed by client code(only used within the class itself)
#### 4. C++ Header File(.h)
* A header file(.h) defines the interface to the class,which includes:
    * Declaration of **all** member variables
    * Declaration of **all** member functions 
* cpp-class/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

// All header (.h) files start with "#pragma once":
#pragma once

// A class is defined with the `class` keyword, the name
// of the class, curly braces, and a required semicolon
// at the end:
class Cube {
  public:  // Public members:
    double getVolume();
    double getSurfaceArea();
    void setLength(double length);

  private: // Private members:
    double length_;
};

```
* cpp-class/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"

double Cube::getVolume() {
  return length_ * length_ * length_;
}

double Cube::getSurfaceArea() {
  return 6 * length_ * length_;
}

void Cube::setLength(double length) {
  length_ = length;
}
```
* cpp-class/main.cpp
```C++=
/**
 * C++ code for creating a Cube of length 2.4 units.
 * - See ../cpp-std/main.cpp for a similar program with print statements.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>
#include "Cube.h"

int main() {
  Cube c;

  c.setLength(3.48);
  double volume = c.getVolume();
  std::cout << "Volume: " << volume << std::endl;

  return 0;
}

```
* Output
```
Volume: 42.1442
```
### C++ standard library
https://www.coursera.org/learn/cs-fundamentals-1/lecture/hmEtj/1-3-c-s-standard-library-std
* The C++ standard library(std)provides a set of commonly used functionally and data structures to build upon.
#### 1. Standard Library Organization
* The C++ standard library is organized into many seperate sub-libraried that can be **#include** in any C++ program.
#### 2. iostream
* The iostream header includes operations for reading/writing to files and the console itself,including **std::cout**.
* cpp-std/cout.cpp
```C++=
/**
 * C++ program for a simple "Hello, world!"
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

int main() {
  std::cout << "Hello, world!" << std::endl;
  return 0;
}
```
* Output
```
Hello, world!
```
* All functionality used from the standard library will be part of the **std namespace**
    * Namspaces allow us to avoid name conflicts fot commonly used names.
* If a feature from a namespace is used often,it can be imported into the global space with **using**:
```C++=
using std::cout;
```  
```C++=
/**
 * C++ program for a simple "Hello, world!" with `using`.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

using std::cout;
using std::endl;

int main() {
  cout << "Hello, world!" << endl;
  return 0;
}
```
* Output
```
Hello, world!
```
```C++=
/**
 * Simple C++ making use of std::cout and a `Cube` class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>
#include "Cube.h"

int main() {
  uiuc::Cube c;
  c.setLength(2.4);
  std::cout << "Volume: " << c.getVolume() << std::endl;

  double surfaceArea = c.getSurfaceArea();
  std::cout << "Surface Area: " << surfaceArea << std::endl;

  return 0;
}
```
* Output
```
Volume: 13.824
Surface Area: 34.56
```
#### 3. Using the uiuc Namespace
* A **cube** is rather generic - hundreds of cube-based data structures exist.
* We will be specific about our **Cube** and specify that our **Cube** is within the **uiuc** namespace.
* cpp-std/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

namespace uiuc {
  class Cube {
    public:
      double getVolume();
      double getSurfaceArea();
      void setLength(double length);

    private:
      double length_;
  };
}
```
## Week 2
### Stack Memory and Pointers
https://www.coursera.org/learn/cs-fundamentals-1/lecture/Iccq3/2-1-stack-memory-and-pointers
* In C++,the programmer has control over the memory and lifecycle of every variable! By default,variables live in **stack memory**.
![](https://i.imgur.com/DJ02P0N.png)

#### 1. A Variable
* A name
* A type
* A value
* A location in memory(**memory address**)
#### 2. A Varible's Memory Address
* In C++,the **&** operator returns the **memory address** of a varible.
* cpp-memory/addressOf.cpp
```C++=
/**
 * C++ program using the & operator to find the address of a variable in memory.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

int main() {
  int num = 7;

  std::cout << "Value: "   <<  num << std::endl;
  std::cout << "Address: " << &num << std::endl;

  return 0;
}
```
* Output
```
Value: 7
Address: 0x7ffee23b2818
```
#### 3. Stack memory
* By default, every varible in C++ is placed in **stack memory**.
* Stack memory is associated with the current function and the memory's **lifecycle** is tied to the function.
    * When the funtion returns or ends,the stack memory of that function is released.
* Stack memory always starts **from high address and gorws down**
![](https://i.imgur.com/QvgXroJ.png)
```C++=
/**
 * C++ program printing memory addresses of variables across two functions.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

void foo() {
  int x = 42;
  std::cout << " x in foo(): " <<  x << std::endl;
  std::cout << "&x in foo(): " << &x << std::endl;
}

int main() {
  int num = 7;
  std::cout << " num in main(): "   <<  num << std::endl;
  std::cout << "&num in main(): " << &num << std::endl;

  foo();

  return 0;
}
```
* Output
```
num in main(): 7
&num in main(): 0x7ffee9f96828
x in foo(): 42
&x in foo(): 0x7ffee9f967fc
```
#### 4. Pointer
* A pointer is a variable that stores the memory address of the data.
    * Pointers are a level of indirection from the data.
* In C++,a pointer is defined by adding an * to the type of the variable.
    -Integer pointer:
    ```C++=
    int *p = &num;
    ```
#### 5. Dereference Operator
* Given a pointer, a level of indirection can be removed with the deference operator *.
```C++=
int num = 7;
int *p = &num;
int value_in_num = *p;
*p = 42;
```
* cpp-memory/main.cpp
```C++=
/**
 * C++ program printing various memory values with references and pointers.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

int main() {
  int num = 7;
  std::cout << " num: " <<  num << std::endl;
  std::cout << "&num: " << &num << std::endl;

  int *p = &num;
  std::cout << " p: " <<  p << std::endl;
  std::cout << "&p: " << &p << std::endl;
  std::cout << "*p: " << *p << std::endl;

  *p = 42;
  std::cout << "*p changed to 42" << std::endl; 
  std::cout << " num: " <<  num << std::endl;

  return 0;
}
```
* Output
```
 num: 7
&num: 0x7ffeeb230868
 p: 0x7ffeeb230868
&p: 0x7ffeeb230860
*p: 7
*p changed to 42
 num: 42
```
### Heap Memory
https://www.coursera.org/learn/cs-fundamentals-1/lecture/TQFvT/2-2-heap-memory
* If memory memory needs to exist for longer than. the lifecycle of the function,we must use **heap memory**.
    * The only way to create heap memory in C++ is with the **new** operator.
* The **new** operator returns a pointer to the memory storing the data - **not an instance of the data itself**.

#### 1. C++'s New Operator
* The **new** operator in C++ will always do three things: 
    * Allocate memory on the heap for the data structure.
    * Initialize the data structure.
    * Return a pointer to the start of the data structure.
* The memory is only ever reclaimed by the system when the pointer is passed to the **delete** operator.
#### 2. Heap Memory
* The code below allocates two chunks of memory:
    * Memory to store an **interger pointer** on the **stack**
    * Memory to store an **interger** on the **heap** 
```C++=
int * numptr = new int;
```
* cpp-heapMemory/main.cpp
```C++=
/**
 * C++ program printing various memory values using heap-allocated memory.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>

int main() {
  int *numPtr = new int;

  std::cout << "*numPtr: " << *numPtr << std::endl;
  std::cout << " numPtr: " <<  numPtr << std::endl;
  std::cout << "&numPtr: " << &numPtr << std::endl;

  *numPtr = 42;
  std::cout << "*numPtr assigned 42." << std::endl;

  std::cout << "*numPtr: " << *numPtr << std::endl;
  std::cout << " numPtr: " <<  numPtr << std::endl;
  std::cout << "&numPtr: " << &numPtr << std::endl;

  return 0;
}
```
* Output
```
*numPtr: 0
 numPtr: 0x7f8b8b500000
&numPtr: 0x7ffeebafc810
*numPtr assigned 42.
*numPtr: 42
 numPtr: 0x7f8b8b500000
&numPtr: 0x7ffeebafc810
```
* cpp-heapMemory/heap1.cpp
```C++=
/**
 * C++ program allocating and free'ing heap memory.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include<iostream>
using uiuc::Cube;

int main() {
  int *p = new int;
  Cube *c = new Cube;

  *p = 42;
  (*c).setLength(4);

  delete c;  c = nullptr;
  delete p;  p = nullptr;
  return 0;
}
```
* Stack memory always starts **from low address and gorws up**
![](https://i.imgur.com/d8lEg8t.png)
```C++=
/**
 * C++ program allocating and double-freeing (!!) memory.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
using uiuc::Cube;

int main() {
  Cube *c1 = new Cube;
  Cube *c2 = c1;

  c2->setLength( 10 );

  delete c2;
  delete c1;  // !!

  return 0;
}
```

#### 3. Lifecycle
https://www.yumpu.com/en/document/read/27082657/c-programming-life-cycle-ipn
* Time during which memory is allocated to the object or,the time between the object and destuction of the object.

    * Automatic: the object is created with its declaration and is destoryed when it is out of scope, that is, when you leave a block of code where it was declared.
    * Dynamic:the object is created and destroyed at any time on the instruction of the programmer
    * Static: the object is created once and is destroyed only when the program ends

#### 4. nullptr

* The C++ keyword **nullptr** is a pointer that points to the memory address 0x0.

    * nullptr represents a pointer to nowhere
    * Address 0x0 is reserved and nerver used by the system
    * Address 0x0 will always generate an **segemention fault** when accessed
    * Calls to **delete** 0x0 is ignored.

#### 5. Arrow Operator(->)
* When an object is stored via s pointer,access can be made to member functions using the -> operator:

```c++=
c->getVolume();

...identical to...

(*c).getVolume();
```
### Heap Memory Puzzles
Following link to see it that this class mainly describe code.
https://www.coursera.org/learn/cs-fundamentals-1/lecture/9jE9R/2-3-heap-memory-puzzles
## Week 3
### Class Constructor
https://www.coursera.org/learn/cs-fundamentals-1/lecture/lYErY/3-1-class-constructors
* When an instance of a class is created, the **class constructor** sets up the initial state of the object.
![](https://i.imgur.com/NDRDFQv.png)

#### 1. Automatic Default Constructor

* If we do not provide any costom constructors,the C++ compiler provides an **automatic default constructor** for our class for free. 

* The automatic default constructor will only initialize all member variables to their default values.

#### 2. Custom Default Constructor

* The simplest constructor we can provide is a custom **default constructor** that specifies the state of the object when the object is constructed.We define one by creating:

* A member funtion with the same name of the class
* The function takes zero parameters.
* The funtion does not have a return type.
```c++=
Cube::Cube() // custom default constructor
```
* cpp-ctor/ex1/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube (with a custom constructor).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

namespace uiuc {
  class Cube {
    public:
      Cube();  // Custom default constructor

      double getVolume();
      double getSurfaceArea();
      void setLength(double length);

    private:
      double length_;
  };
}
```
* cpp-ctor/ex1/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with a custom constructor).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"

namespace uiuc {
  Cube::Cube() {
    length_ = 1;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-ctor/ex1/main.cpp
```C++=
/**
 * C++ program using the Cube's custom default constructor.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

int main() {
  uiuc::Cube c;
  std::cout << "Volume: " << c.getVolume() << std::endl;
  return 0;
}
```
* Output
```
Volume: 1
```
#### 3. Custom Constructors
* We can also specify custom,non-default constructors that require client code to supply arguments:
```c++=
Cube ::Cube(double length)
    //one-argument ctor specifying initial length
```
* cpp-ctor/ex2/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

namespace uiuc {
  class Cube {
    public:
      Cube();  // Custom default constructor
      Cube(double length);  // One argument constructor

      double getVolume();
      double getSurfaceArea();
      void setLength(double length);

    private:
      double length_;
  };
}
```
* cpp-ctor/ex2/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"

namespace uiuc {
  Cube::Cube() {
    length_ = 1;
  }

  Cube::Cube(double length) {
    length_ = length;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-ctor/ex2/main.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"

namespace uiuc {
  Cube::Cube() {
    length_ = 1;
  }

  Cube::Cube(double length) {
    length_ = length;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* Output
```
Volume: 8
```
#### 4. Automatic Dafault Constructor
* If **any** custom constructor is defined ,an automatic default constructor is **not** defined.
* cpp-ctor/ex3/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube (custom constructor, no default).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

namespace uiuc {
  class Cube {
    public:
      // No default constructor
      Cube(double length);  // One argument constructor

      double getVolume();
      double getSurfaceArea();
      void setLength(double length);

    private:
      double length_;
  };
}
```
* cpp-ctor/ex3/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (custom constructor, no default).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"

namespace uiuc {
  Cube::Cube(double length) {
    length_ = length;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-ctor/ex3/main.cpp
```C++=
/**
 * C++ program using the Cube's one arugment constructor.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

int main() {
  uiuc::Cube c;  // !!!
  std::cout << "Volume: " << c.getVolume() << std::endl;
  return 0;
}
```
* Output
```
main.cpp:12:14: fatal error: no matching constructor for initialization of 'uiuc::Cube'
  uiuc::Cube c;  // !!!
             ^
./Cube.h:14:7: note: candidate constructor not viable: requires single argument 'length', but no arguments were provided
      Cube(double length);  // One argument constructor
      ^
./Cube.h:11:9: note: candidate constructor (the implicit copy constructor) not viable: requires 1 argument, but 0 were provided
  class Cube {
        ^
./Cube.h:11:9: note: candidate constructor (the implicit move constructor) not viable: requires 1 argument, but 0 were provided
1 error generated.
make: *** [.objs/main.o] Error 1
```
### Copy constructor
https://www.coursera.org/learn/cs-fundamentals-1/lecture/qJHqB/3-2-copy-constructors
* A **copy constructor** is a special constructor that exists to make a copy of an existing object.
![](https://i.imgur.com/b2lqgtD.png)
#### 1. Automatic Copy Constructor
* If we do not provide a custom copy constructor, the C++ compiler provides an automatic copy constructor for our class for free.
* The automatic copy constructor will copy contents of all member varibles.
#### 2. Custom Copy Constructor
* A custom copy constructor is:
    * A class constructor
    * Has exactly one argument
        -The argument must be const reference of the same type as the class.
```c++=
Cube::Cube(const Cube & obj)
```
* cpp-cctor/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

namespace uiuc {
  Cube::Cube() {
    length_ = 1;
    std::cout << "Default constructor invoked!" << std::endl;
  }

  Cube::Cube(const Cube & obj) {
    length_ = obj.length_;
    std::cout << "Copy constructor invoked!" << std::endl;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
#### 3. Copy Constructor Invocation
* Often ,copy constructors are invoked automatically:
    * Passing on object as a parameter(by value)
    * Reutrning an object from a function(by value)
    * Initializing a new object
* cpp-cctor/ex1/main.cpp
```C++=
/**
 * C++ program copying a Cube class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

void foo(Cube cube) {
  // Nothing :)
}

int main() {
  Cube c;    //Default constructor
  foo(c);    //copy consturctor

  return 0;
}
```
* Output
```
Default constructor invoked!
Copy constructor invoked!
```
* cpp-cctor/ex2/main.cpp
```C++=
/**
 * C++ program copying a Cube class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

Cube foo() {
  Cube c;      //Default consturctor
  return c;    //Copy consturctor
}

int main() {
  Cube c2 = foo();//Copy consturctor
  return 0;
}
```
* Output
```
Default constructor invoked!
Copy constructor invoked!
Copy constructor invoked!
```
* cpp-cctor/ex3/main.cpp
```C++=
/**
 * C++ program copying a Cube class. 
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

int main() {
  Cube c;            //Default constructor
  Cube myCube = c;   //Copy constructor

  return 0;
}
```
* Output
```
Default constructor invoked!
Copy constructor invoked!
```
* cpp-cctor/ex4/main.cpp
```C++=
/**
 * C++ program copying a Cube class. 
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

int main() {
  Cube c;        //Default constructor
  Cube myCube;   //Default constructor

  myCube = c;

  return 0;
}

```
* Output
```
Default constructor invoked!
Default constructor invoked!
```
### Copy assignment operator
https://www.coursera.org/learn/cs-fundamentals-1/lecture/2s2yi/3-3-copy-assignment-operator
* A **copy assignment operator** defines the behavior when an object is copied defines the behavior when an object is copied using the assignment operator **=**
![](https://i.imgur.com/KKpCip3.png)

#### 1. Copy Constructor vs. Assignment
* A copy constructor **creates a new object**(constructor) 
* An assignment operator assigns a **value to an existing object.**
    * An assignment operator is always called on an object that has already been constructed. 
#### 2. Automatic Assignment Operator
* If an assignment operator is not provided,the C++ compiler provides an automatic assignment operator.
* The automatic assignment operator will copy the contents of all member variables.

#### 3. Custom Assignment Operator
* A custom assignment operator is:
    * Is a public member function of the class.
    * Has the function name **operator=**
    * Has a return value of a reference of the class type.
    * Has exactly one argument
    -The argument must be const reference of the class type. 
    ```c++=
    Cube & Cube::operator=(const Cube & obj)
    ```
* cpp-assignmentOp/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

namespace uiuc {
  Cube::Cube() {
    length_ = 1;
    std::cout << "Default constructor invoked!" << std::endl;
  }

  Cube::Cube(const Cube & obj) {
    length_ = obj.length_;
    std::cout << "Copy constructor invoked!" << std::endl;
  }

  Cube & Cube::operator=(const Cube & obj) {
    length_ = obj.length_;
    std::cout << "Assignment operator invoked!" << std::endl;    
    return *this;
  }

  double Cube::getVolume() {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-assignmentOp/main.cpp
```C++=
/**
 * C++ program invoking Cube's assignment operator.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
using uiuc::Cube;

int main() {
  Cube c;        //Default consctructor
  Cube myCube;   //Default constructor

  myCube = c;    //Assignment operation

  return 0;
}
```
* Output
```
Default constructor invoked!
Default constructor invoked!
Assignment operator invoked!
```
### Variable Storage
https://www.coursera.org/learn/cs-fundamentals-1/lecture/ekyDt/3-4-variable-storage
* In C++, an instance of a varible can be stored directly in memory, accessed by pointer, **or** accessed by reference.
![](https://i.imgur.com/abepdTw.png)
#### 1. Direct Storage
* By default, varibles are stored directly in memory.
    * The **type** of a varible has no modifiers(ex: * or &).
    * The objects takes up exactly its size in memory.
```c++=
Cube c;            //Stores a Cube in memory
int i;             //Stores an interger in memory
uiuc::HSLAPixel p; //Stores a pixel in memory
```
#### 2. Storage by Pointer
* The **type** of a variable is modified with an asterisk(*)
* A pointer takes a "memory address width" of memory(ex:64 bits on a 64-bit system). 
* The pointer "points" to the allocated space of the object.
```c++=
Cube *c;             //Pointer to a Cube in memory
int *i;              //Pointer to an interger in memory
uiuc::HSLAPixel *p;  //Pointer to a pixel in memory
```
#### 3. Storage by Reference
* A reference is an **alias** to existing memory and is denoted in the type with an ampersand(**&**).
* A reference **does not store memory** itself, it is only an alias to another varible.
* The alias must be assigned when. the variable is initialized.
```c++=
var s = "c++";
Cube &c = cube;     //Alias to the varible 'cube'
int &i = count;     //Alias to the varible 'i'
uiuc::HSLAPixel &p; //Illegal!! Must alias something  when varible is initialized.
```
#### 4. Example:Cube Currency
* Suppose our cubes have a value to them, based on their volume:
![](https://i.imgur.com/4ffiYyr.png)
* When we receive money, we want the cube itself - not a copy of the cube.
![](https://i.imgur.com/uw8aLhg.png)
* cpp-memory2/Cube.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

namespace uiuc {  
  Cube::Cube(double length) {
    length_ = length;
    std::cout << "Created $" << getVolume() << std::endl;
  }

  Cube::Cube(const Cube & obj) {
    length_ = obj.length_;
    std::cout << "Created $" << getVolume() << " via copy" << std::endl;
  }

  Cube & Cube::operator=(const Cube & obj) {
    std::cout << "Transformed $" << getVolume() << "-> $" << obj.getVolume() << std::endl;
    length_ = obj.length_;
    return *this;
  }

  double Cube::getVolume() const {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() const {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-memory2/ex1/byValue.cpp
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include <iostream>

namespace uiuc {  
  Cube::Cube(double length) {
    length_ = length;
    std::cout << "Created $" << getVolume() << std::endl;
  }

  Cube::Cube(const Cube & obj) {
    length_ = obj.length_;
    std::cout << "Created $" << getVolume() << " via copy" << std::endl;
  }

  Cube & Cube::operator=(const Cube & obj) {
    std::cout << "Transformed $" << getVolume() << "-> $" << obj.getVolume() << std::endl;
    length_ = obj.length_;
    return *this;
  }

  double Cube::getVolume() const {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() const {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* Output
```
Created $1000
Created $1000 via copy
```
* cpp-memory2/ex1/byRef.cpp
```C++=
/**
 * C++ program aliasing a Cube class by reference.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

int main() {
  // Create a 1,000-valued cube
  Cube c(10);

  // Transfer the cube
  Cube & myCube = c;

  return 0;
}
```
* Output
```
Created $1000
```
* cpp-memory2/ex1/byValue.cpp
```C++=
/**
 * C++ program copying a Cube currency pointer.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

int main() {
  // Create a 1,000-valued cube
  Cube c(10);

  // Transfer the cube
  Cube * myCube = &c;

  return 0;
}
```
* Output
```
Created $1000
```
#### 5. Pass by
* Identical to storage, arguments can be passed to functions in three different ways:
    * Pass by **value** (default)
    * Pass by **pointer** (modified with * )
    * pass by **reference** (modified with &, acts as an alias)
* cpp-memory2/ex2/byValue.cpp
```C++=
/**
 * C++ program sending a Cube by value.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
using uiuc::Cube;

bool sendCube(Cube c) {    
  // ... logic to send a Cube somewhere ...
  return true;
}

int main() {
  // Create a 1,000-valued cube
  Cube c(10);

  // Send the cube to someone
  sendCube(c);

  return 0;
}
```
* Output
```
Created $1000
Created $1000 via copy
```
```C++=
/**
 * C++ program sending a Cube by reference.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
#include <iostream>

using uiuc::Cube;

bool sendCube(Cube & c) {    
  // ... logic to send a Cube somewhere ...
  return true;
}

int main() {
  // Create a 1,000-valued cube
  Cube c(10);

  // Send the cube to someone
  sendCube(c);

  return 0;
}
```
* Output
```
Created $1000
```
* cpp-memory/ex2/byPointer.cpp
```C++=
/**
 * C++ program sending a Cube by pointer.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "../Cube.h"
#include <iostream>

using uiuc::Cube;

bool sendCube(Cube * c) {    
  // ... logic to send a Cube somewhere ...
  return true;
}

int main() {
  // Create a 1,000-valued cube
  Cube c(10);

  // Send the cube to someone
  sendCube(&c);

  return 0;
}
```
* Output
```
Created $1000
```
#### 6. Returned by
* Similarly, values can be returned all three ways as well:
    * Return by **value**(default)
    * Return by **pointer**(modified with * )
    * Return by **reference**(modified with &, acts as an alias)
    **-Never return a refernce to a stack varible created on the stack of your current function!**
### Class destructor
https://www.coursera.org/learn/cs-fundamentals-1/lecture/yP7YJ/3-5-class-destructor
* When. an instance of a class is cleaned up, the **class destructor** is the last call in a class's lifestyle.
![](https://i.imgur.com/WHWbGMy.png)
#### 1. Automatic Default Destructor
* An **automatic default destructor** is added to your class if no other destructor is defined.
* The only action of the automatic default destructor is to call the default destructor of all member objects.
* An destructor should **never** be called directly. Instead, it is automatically called when the object's memory is being reclaimed by the system:
    * If the object is on the **stack**, when the function returns
    * If the object is on the **heap**, when **delete** is used
#### 2. Custom Destructor
* To add custom behavior to the end-of-life of the function, a custom destructor can be defined as:
    * A custom destructor is a member function.
    * The function's destructor is the name of the class, preceded by a tlide **~** .
    * All destructors have zero arguments and no return type.
```c++=
Cube::~Cube();    //Custom destructor 
```
* cpp-dtor/Cube.cpp
```c++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */
#include "Cube.h"
#include <iostream>

using std::cout;
using std::endl;

namespace uiuc {  
  Cube::Cube() {
    length_ = 1;
    cout << "Created $1 (default)" << endl;
  }

  Cube::Cube(double length) {
    length_ = length;
    cout << "Created $" << getVolume() << endl;
  }

  Cube::Cube(const Cube & obj) {
    length_ = obj.length_;
    cout << "Created $" << getVolume() << " via copy" << endl;
  }

  Cube::~Cube() {
    cout << "Destroyed $" << getVolume() << endl;
  }

  Cube & Cube::operator=(const Cube & obj) {
    cout << "Transformed $" << getVolume() << "-> $" << obj.getVolume() << endl;
    length_ = obj.length_;
    return *this;
  }



  double Cube::getVolume() const {
    return length_ * length_ * length_;
  }

  double Cube::getSurfaceArea() const {
    return 6 * length_ * length_;
  }

  void Cube::setLength(double length) {
    length_ = length;
  }
}
```
* cpp-dtor/main.cpp
```c++=
/**
 * C++ program invoking Cube's destructor several times.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
using uiuc::Cube;

double cube_on_stack() {
  Cube c(3);
  return c.getVolume();
}

void cube_on_heap() {
  Cube * c1 = new Cube(10);
  Cube * c2 = new Cube;
  delete c1;
}

int main() {
  cube_on_stack();
  cube_on_heap();
  cube_on_stack();
  return 0;
}
```
Output
```
Created $27
Destroyed $27
Created $1000
Created $1 (default)
Destroyed $1000
Created $27
Destroyed $27
```
* A custom destructor is essential when an object allocates an external resource that must be closed or freed when the object is destroyed.Examples:
    * Heap memory
    * Open files
    * Shared memory 
## Week 4
### Template Types
https://www.coursera.org/learn/cs-fundamentals-1/lecture/41GZS/4-1-template-types
* A ** template type** is a special type that can take on different types whem the type is initialized.**std::vector** uses a template type:
![](https://i.imgur.com/RoNQdcQ.png)
1. std::vector
* **std::vector** standard library class that provides the functionality
* of a dynamically groming array with a **templated** type.Key ideas:
```c++=
Defined in:               #include <vector>;
Initalization:            #std::vector<T> v;
Add to (back) of array:   ::push_back(T);
Access specific element:  ::operator[](unsigned pos);
Number of elements:       ::size();
```
2. Template Type
* When initializing a "templated" type,the template type goes inside of **< >** at the end of the type name:
```C++
std::vector<char> v1;
std::vector<int> v2;
std::vector<uiuc::Cube> v3;
```
* cpp-vector/ex1/main.cpp
```C++=
/**
 * C++ program using the std::vector class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <vector>
#include <iostream>

int main() {
  std::vector<int> v;
  v.push_back( 2 );
  v.push_back( 3 );
  v.push_back( 5 );

  std::cout << v[0] << std::endl;
  std::cout << v[1] << std::endl;
  std::cout << v[2] << std::endl;

  return 0;
}
```
* Output
```
2
3
5
```
* cpp-vector/ex2/main.cpp
```C++=
/**
 * C++ program using the std::vector class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <vector>
#include <iostream>

int main() {
  std::vector<int> v;
  for (int i = 0; i < 100; i++) {
    v.push_back( i * i );
  }

  std::cout << v[12] << std::endl;

  return 0;
}
```
* Output
```
144
```
### Tower of Hanoi 
https://www.coursera.org/learn/cs-fundamentals-1/lecture/aLUTd/4-2-tower-of-hanoi-introduction
* Consider the Tower of Hanoi problem,where multiple cubes must be transferred to a new location in such a way that a large cube cannot be placed on top of a smaller cube:  
![](https://i.imgur.com/nA8hVyg.png)
1. Programmatic Structure
* The Tower of Hanoi problem involves three district entitles that must be represented in code:
![](https://i.imgur.com/EUElCA4.png)
2. Extending the Cube
* The cube class needs a color:
    * In last week's assignment, we built **uiuc::HSLAPixel**
* cpp-tower/uiuc/Cube.h
```C++=
/**
 * Simple C++ class for representing a Cube (with constructors).
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

#include "HSLAPixel.h"

namespace uiuc {
  class Cube {
    public:
      Cube(double length, HSLAPixel color);

      double getLength() const;
      void setLength(double length);

      double getVolume() const;
      double getSurfaceArea() const;

    private:
      double length_;
      HSLAPixel color_;
  };
}
```
3. Building the Tower of Hanoi Game
* A new class must be created to represent each of the stacks in the Tower of Hanoi game:
![](https://i.imgur.com/cV0arD4.png)
4. Building the Stack Class
* A single stack must contain:
    * An vector of cubes
    * Operation to interact with the top of the stack 
* cpp-tower/Stack.h
```C++=
/**
 * C++ class for a "stack" of cubes in a Tower of Hanoi puzzle.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

#include <vector>
#include "uiuc/Cube.h"
using uiuc::Cube;

class Stack {
  public:
    void push_back(const Cube & cube);
    Cube removeTop();
    Cube & peekTop();
    unsigned size() const;

    // An overloaded operator<<, allowing us to print the stack via `cout<<`:
    friend std::ostream& operator<<(std::ostream & os, const Stack & stack);

  private:
    std::vector<Cube> cubes_;
};
```
5. Building the Tower of Hanoi Game
* Finally, the game is built from the components we have already built:
    * An array of three stacks
    * The initial state has four cubed in the first stack
* cpp-tower/Game.h
```C++=
/**
 * C++ class for a game of the Tower of Hanoi puzzle.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

#include "Stack.h"
#include <vector>

class Game {
  public:
    Game();
    void solve();

    // An overloaded operator<<, allowing us to print the stack via `cout<<`:
    friend std::ostream& operator<<(std::ostream & os, const Game & game);

  private:
    std::vector<Stack> stacks_;
};
```
* cpp-tower/Game.cpp
```C++=
/**
 * C++ class for a game of the Tower of Hanoi puzzle.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Game.h"
#include "Stack.h"
#include "uiuc/Cube.h"
#include "uiuc/HSLAPixel.h"

#include <iostream>
using std::cout;
using std::endl;

// Solves the Tower of Hanoi puzzle.
// (Feel free to call "helper functions" to help you solve the puzzle.)
void Game::solve() {
  // Prints out the state of the game:
  cout << *this << endl;

  // @TODO -- Finish solving the game!
}

// Default constructor to create the initial state:
Game::Game() {
  // Create the three empty stacks:
  for (int i = 0; i < 3; i++) {
    Stack stackOfCubes;
    stacks_.push_back( stackOfCubes );
  }

  // Create the four cubes, placing each on the [0]th stack:
  Cube blue(4, uiuc::HSLAPixel::BLUE);
  stacks_[0].push_back(blue);

  Cube orange(3, uiuc::HSLAPixel::ORANGE);
  stacks_[0].push_back(orange);

  Cube purple(2, uiuc::HSLAPixel::PURPLE);
  stacks_[0].push_back(purple);

  Cube yellow(1, uiuc::HSLAPixel::YELLOW);
  stacks_[0].push_back(yellow);
}

std::ostream& operator<<(std::ostream & os, const Game & game) {
  for (unsigned i = 0; i < game.stacks_.size(); i++) {
    os << "Stack[" << i << "]: " << game.stacks_[i];
  }
  return os;
}
```
* cpp-tower/main.cpp
```C++=
/**
 * Simple main to create and solve a game of the Tower of Hanoi puzzle.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Game.h"
#include <iostream>

int main() {
  Game g;

  std::cout << "Initial game state: " << std::endl;
  std::cout << g << std::endl;

  g.solve();

  std::cout << "Final game state: " << std::endl;
  std::cout << g << std::endl;

  return 0;
}
```
* Output
```
Initial game state: 
Stack[0]: 4 3 2 1 
Stack[1]: 
Stack[2]: 

Stack[0]: 4 3 2 1 
Stack[1]: 
Stack[2]: 

Final game state: 
Stack[0]: 4 3 2 1 
Stack[1]: 
Stack[2]: 
```
### Tower of Hanoi - Solution 1
https://www.coursera.org/learn/cs-fundamentals-1/lecture/LpU49/4-3-tower-of-hanoi-solution-1
![](https://i.imgur.com/Pye3SSQ.png)
* cpp-tower-solution/Game.cpp
```C++=
#include "Game.h"
#include "Stack.h"
#include "uiuc/Cube.h"
#include "uiuc/HSLAPixel.h"

#include <iostream>
using std::cout;
using std::endl;

// Game default constructor
Game::Game() {
  // The initial default game state has three stacks four cubes.
  
  // Create the three empty stacks:
  for (int i = 0; i < 3; i++) {
    Stack stackOfCubes;
    stacks_.push_back( stackOfCubes );
  }

  // Create the four cubes, placing each on the [0]th stack:
  // - A blue cube of length=4, on the bottom
  // - A orange cube of length=3, on top of the blue cube
  // - A purple cube of length=2, on top of the orange cube
  // - A yellow cube of length=1 at the very top
  Cube blue(4, uiuc::HSLAPixel::BLUE);
  stacks_[0].push_back(blue);

  Cube orange(3, uiuc::HSLAPixel::ORANGE);
  stacks_[0].push_back(orange);

  Cube purple(2, uiuc::HSLAPixel::PURPLE);
  stacks_[0].push_back(purple);

  Cube yellow(1, uiuc::HSLAPixel::YELLOW);
  stacks_[0].push_back(yellow);
}

void Game::_move(unsigned index1, unsigned index2) {
  Cube cube = stacks_[index1].removeTop();
  stacks_[index2].push_back(cube);
}

void Game::_legalMove(unsigned index1, unsigned index2) {
  if (stacks_[index1].size() == 0 && stacks_[index2].size() > 0) {
    _move(index2, index1);
  } else if (stacks_[index1].size() > 0 && stacks_[index2].size() == 0) {
    _move(index1, index2);
  } else if (stacks_[index1].size() > 0 && stacks_[index2].size() > 0) {
    if (stacks_[index1].peekTop().getLength() < stacks_[index2].peekTop().getLength() ) {
      _move(index1, index2);
    } else {
      _move(index2, index1);
    }
  }
  
  cout << *this << endl;
}

void Game::solve() {
  while (stacks_[2].size() != 4) {
    _legalMove(0, 1);
    _legalMove(0, 2);
    _legalMove(1, 2);
  }
}

std::ostream& operator<<(std::ostream & os, const Game & game) {
  for (unsigned i = 0; i < game.stacks_.size(); i++) {
    os << "Stack[" << i << "]: " << game.stacks_[i];
  }
  return os;
}
```
```
nitial game state: 
Stack[0]: 4 3 2 1 
Stack[1]: 
Stack[2]: 

Stack[0]: 4 3 2 
Stack[1]: 1 
Stack[2]: 

Stack[0]: 4 3 
Stack[1]: 1 
Stack[2]: 2 

Stack[0]: 4 3 
Stack[1]: 
Stack[2]: 2 1 

Stack[0]: 4 
Stack[1]: 3 
Stack[2]: 2 1 

Stack[0]: 4 1 
Stack[1]: 3 
Stack[2]: 2 

Stack[0]: 4 1 
Stack[1]: 3 2 
Stack[2]: 

Stack[0]: 4 
Stack[1]: 3 2 1 
Stack[2]: 

Stack[0]: 
Stack[1]: 3 2 1 
Stack[2]: 4 

Stack[0]: 
Stack[1]: 3 2 
Stack[2]: 4 1 

Stack[0]: 2 
Stack[1]: 3 
Stack[2]: 4 1 

Stack[0]: 2 1 
Stack[1]: 3 
Stack[2]: 4 

Stack[0]: 2 1 
Stack[1]: 
Stack[2]: 4 3 

Stack[0]: 2 
Stack[1]: 1 
Stack[2]: 4 3 

Stack[0]: 
Stack[1]: 1 
Stack[2]: 4 3 2 

Stack[0]: 
Stack[1]: 
Stack[2]: 4 3 2 1 

Final game state: 
Stack[0]: 
Stack[1]: 
Stack[2]: 4 3 2 1 
```
### Tower of Hanoi - Solution 2
https://www.coursera.org/learn/cs-fundamentals-1/lecture/0Y1zE/4-4-tower-of-hanoi-solution-2
![](https://i.imgur.com/LgYVrvq.png)
![](https://i.imgur.com/JLbz4wR.png)
![](https://i.imgur.com/4Ym7lYS.png)
![](https://i.imgur.com/VUbmkI9.png)
![](https://i.imgur.com/723lNk6.png)
* cpp-tower-solution2/Game.cpp
```C++=
#include "Game.h"
#include "Stack.h"
#include "uiuc/Cube.h"
#include "uiuc/HSLAPixel.h"

#include <iostream>
using std::cout;
using std::endl;

// Game default constructor
Game::Game() {
  // The initial default game state has three stacks four cubes.
  
  // Create the three empty stacks:
  for (int i = 0; i < 3; i++) {
    Stack stackOfCubes;
    stacks_.push_back( stackOfCubes );
  }

  // Create the four cubes, placing each on the [0]th stack:
  // - A blue cube of length=4, on the bottom
  // - A orange cube of length=3, on top of the blue cube
  // - A purple cube of length=2, on top of the orange cube
  // - A yellow cube of length=1 at the very top
  Cube blue(4, uiuc::HSLAPixel::BLUE);
  stacks_[0].push_back(blue);

  Cube orange(3, uiuc::HSLAPixel::ORANGE);
  stacks_[0].push_back(orange);

  Cube purple(2, uiuc::HSLAPixel::PURPLE);
  stacks_[0].push_back(purple);

  Cube yellow(1, uiuc::HSLAPixel::YELLOW);
  stacks_[0].push_back(yellow);
}

// Move a Cube from Stack `s1` to Stack `s2`:
void Game::_moveCube(Stack & s1, Stack & s2) {
  Cube cube = s1.removeTop();
  s2.push_back(cube);
}

// Move the cubes in the range [start...end] from `source` to `target`, using spare as a spare spot:
void Game::_move(
  unsigned start, unsigned end,
  Stack & source, Stack & target, Stack & spare,
  unsigned depth
) {
  cout << "Planning (depth=" << depth++ << "): Move [" << start << ".." << end << "] from Stack@" << &source << " -> Stack@" << &target << ", Spare@" << &spare << "]" << endl;

  // Check if we are only moving one cube:
  if (start == end) {
    // If so, move it directly:
    _moveCube( source, target );
    cout << *this << endl;
  } else {
    // Otherwise, use our move strategy:
    _move(start + 1, end  , source, spare , target, depth);
    _move(start    , start, source, target, spare , depth);
    _move(start + 1, end  , spare , target, source, depth);
  }
}

void Game::solve() {
  _move(
    0, stacks_[0].size() - 1,  //< Move the entire set of cubes, [0 .. size-1]
    stacks_[0], //< Source stack is [0]
    stacks_[2], //< Target stack is [2]
    stacks_[1], //< Spare stack is [1]
    0   //< Initial depth (for printouts only) is 0
  );
}

std::ostream& operator<<(std::ostream & os, const Game & game) {
  for (unsigned i = 0; i < game.stacks_.size(); i++) {
    os << "Stack[" << i << ", " << &game.stacks_[i] << "]: " << game.stacks_[i] << endl;
  }
  return os;
}
```
```
Initial game state: 
Stack[0, 0x7ff1fdc018b0]: 4 3 2 1
Stack[1, 0x7ff1fdc018c8]: 
Stack[2, 0x7ff1fdc018e0]: 

Planning (depth=0): Move [0..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Planning (depth=1): Move [1..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018e0]
Planning (depth=2): Move [2..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018e0]
Stack[0, 0x7ff1fdc018b0]: 4 3 2
Stack[1, 0x7ff1fdc018c8]: 1
Stack[2, 0x7ff1fdc018e0]: 

Planning (depth=3): Move [2..2] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Stack[0, 0x7ff1fdc018b0]: 4 3
Stack[1, 0x7ff1fdc018c8]: 1
Stack[2, 0x7ff1fdc018e0]: 2

Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018b0]
Stack[0, 0x7ff1fdc018b0]: 4 3
Stack[1, 0x7ff1fdc018c8]: 
Stack[2, 0x7ff1fdc018e0]: 2 1

Planning (depth=2): Move [1..1] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018e0]
Stack[0, 0x7ff1fdc018b0]: 4
Stack[1, 0x7ff1fdc018c8]: 3
Stack[2, 0x7ff1fdc018e0]: 2 1

Planning (depth=2): Move [2..3] from Stack@0x7ff1fdc018e0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018b0]
Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018e0 -> Stack@0x7ff1fdc018b0, Spare@0x7ff1fdc018c8]
Stack[0, 0x7ff1fdc018b0]: 4 1
Stack[1, 0x7ff1fdc018c8]: 3
Stack[2, 0x7ff1fdc018e0]: 2

Planning (depth=3): Move [2..2] from Stack@0x7ff1fdc018e0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018b0]
Stack[0, 0x7ff1fdc018b0]: 4 1
Stack[1, 0x7ff1fdc018c8]: 3 2
Stack[2, 0x7ff1fdc018e0]: 

Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018e0]
Stack[0, 0x7ff1fdc018b0]: 4
Stack[1, 0x7ff1fdc018c8]: 3 2 1
Stack[2, 0x7ff1fdc018e0]: 

Planning (depth=1): Move [0..0] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Stack[0, 0x7ff1fdc018b0]: 
Stack[1, 0x7ff1fdc018c8]: 3 2 1
Stack[2, 0x7ff1fdc018e0]: 4

Planning (depth=1): Move [1..3] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018b0]
Planning (depth=2): Move [2..3] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018b0, Spare@0x7ff1fdc018e0]
Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018b0]
Stack[0, 0x7ff1fdc018b0]: 
Stack[1, 0x7ff1fdc018c8]: 3 2
Stack[2, 0x7ff1fdc018e0]: 4 1

Planning (depth=3): Move [2..2] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018b0, Spare@0x7ff1fdc018e0]
Stack[0, 0x7ff1fdc018b0]: 2
Stack[1, 0x7ff1fdc018c8]: 3
Stack[2, 0x7ff1fdc018e0]: 4 1

Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018e0 -> Stack@0x7ff1fdc018b0, Spare@0x7ff1fdc018c8]
Stack[0, 0x7ff1fdc018b0]: 2 1
Stack[1, 0x7ff1fdc018c8]: 3
Stack[2, 0x7ff1fdc018e0]: 4

Planning (depth=2): Move [1..1] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018b0]
Stack[0, 0x7ff1fdc018b0]: 2 1
Stack[1, 0x7ff1fdc018c8]: 
Stack[2, 0x7ff1fdc018e0]: 4 3

Planning (depth=2): Move [2..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018c8, Spare@0x7ff1fdc018e0]
Stack[0, 0x7ff1fdc018b0]: 2
Stack[1, 0x7ff1fdc018c8]: 1
Stack[2, 0x7ff1fdc018e0]: 4 3

Planning (depth=3): Move [2..2] from Stack@0x7ff1fdc018b0 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018c8]
Stack[0, 0x7ff1fdc018b0]: 
Stack[1, 0x7ff1fdc018c8]: 1
Stack[2, 0x7ff1fdc018e0]: 4 3 2

Planning (depth=3): Move [3..3] from Stack@0x7ff1fdc018c8 -> Stack@0x7ff1fdc018e0, Spare@0x7ff1fdc018b0]
Stack[0, 0x7ff1fdc018b0]: 
Stack[1, 0x7ff1fdc018c8]: 
Stack[2, 0x7ff1fdc018e0]: 4 3 2 1

Final game state: 
Stack[0, 0x7ff1fdc018b0]: 
Stack[1, 0x7ff1fdc018c8]: 
Stack[2, 0x7ff1fdc018e0]: 4 3 2 1
```
### Templates and Classes
https://www.coursera.org/learn/cs-fundamentals-1/lecture/ztTcK/4-5-templates-and-classes
* C++ allows for us to use the power of templates in building our own classes.
1. Templated Functions
* A template variable is defined by declaring it before the beginning of a class or function: 
```C++=
template <typename T>
class List{
    ...
    private:
        T data_;
}

template <typename T>
int max(T a,T b){
    if(a>b){
    return a;
    }
    return b;
}
```
2. Compile-Time Binding
* Templated variables are checked at compile time, which allows for errors to be caught before running the program:
```C++=
templated <typename T>
T max(T a,T b){
    if(a>b){
    return a;
    }
    return b;
}

max (4,7);               //OK
max(Cube(3),Cube(6));    //!!Error
```
* cpp-templates/main.cpp
```C++=
/**
 * Simple use of C++ templates.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include <iostream>
using std::cout;
using std::endl;

#include "Cube.h"
using uiuc::Cube;

template <typename T>
T max(T a, T b) {
  if (a > b) { return a; }
  return b;
}

int main() {
  cout << "max(3, 5): " << max(3, 5) << endl;
  cout << "max('a', 'd'): " << max('a', 'd') << endl;
  cout << "max(\"Hello\", \"World\"): " << max("Hello", "World") << endl;
  cout << "max( Cube(3), Cube(6) ): " << max( Cube(3), Cube(6) ) << endl;

  return 0;
}
```
* Output
```
main.cpp:17:9: fatal error: invalid operands to binary expression ('uiuc::Cube' and 'uiuc::Cube')
  if (a > b) { return a; }
      ~ ^ ~
main.cpp:25:42: note: in instantiation of function template specialization 'max<uiuc::Cube>' requested here
  cout << "max( Cube(3), Cube(6) ): " << max( Cube(3), Cube(6) ) << endl;
                                         ^
1 error generated.
make: *** [.objs/main.o] Error 1
```
### Inheritance
* **Inhertance** allows for a class to inherit all member functions and data from a **base class** into a **derived class.*
1. Generic to Specialized
* A **base class** is a genric from of a specialized, **derived class.** 
![](https://i.imgur.com/RD3kv3U.png)
* cpp-inheritance/Shape.h
```C++=
/**
 * Generic `Shape` class.
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

class Shape {
  public:
    Shape();
    Shape(double width);
    double getWidth() const;

  private:
    double width_;
};
```
* cpp-inheritance/Cube.h
```C+= 
/**
 * A `Cube` class inheriting from a `Shape`
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#pragma once

#include "Shape.h"
#include "HSLAPixel.h"

namespace uiuc {
  class Cube : public Shape {
    public:
      Cube(double width, uiuc::HSLAPixel color);
      double getVolume() const;

    private:
      uiuc::HSLAPixel color_;
  };
}
```
2. Initialization
* When a derived class is initialized, the derived class **must** construct the base class:
    * **Cube** must construct **Shape**
    * By default, uses default constructor
    * Custom constructor can be used with an **initialization list**
* cpp-inheritance/Cube.cpp
```C++=
/**
 * A `Cube` class inheriting from a `Shape`
 * 
 * @author
 *   Wade Fagen-Ulmschneider <waf@illinois.edu>
 */

#include "Cube.h"
#include "Shape.h"

namespace uiuc {
  Cube::Cube(double width, uiuc::HSLAPixel color) : Shape(width) {
    color_ = color;
  }

  double Cube::getVolume() const {
    // Cannot access Shape::width_ due to it being `private`
    // ...instead we use the public Shape::getWidth(), a public function

    return getWidth() * getWidth() * getWidth();
  }
}
```
3. Access Control
* When a base class is ingerited, the derived class:
    * Can access all **public** members of the base class
    * Can **not** access **private** of the base class
4. Initializer List 
* The syntax to initialize the bese class is called the initializer list and can be used for several purposed:
    * Initialize a base class
    * Initialize the current class using another constructor
    * Initialize the default values of mamber variables 
* cpp-inheritance/Shape.cpp
```C++=
#include "Shape.h"

Shape::Shape() : Shape(1) {
  // Nothing.
}

Shape::Shape(double width) : width_(width) {
  // Nothing.
}

double Shape::getWidth() const {
  return width_;
}
```
* cpp-inheritance/main.cpp
```C++=
#include <iostream>

#include "Cube.h"
#include "HSLAPixel.h"

int main() {
  uiuc::Cube c(4, uiuc::HSLAPixel::PURPLE);
  std::cout << "Created a Purple cube!" << std::endl;
  return 0;
}
```
* Output
```
Created a Purple cube!
```