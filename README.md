# ZECTA PROGRAMMING LANGUAGE DOCUMENTATION

Powerful as C++🔥, fast as C👨‍💻, Basic as Zig🎯




# Introduction

- Zecta is a Modern mid-level compiled langauge with high performance and flexibility
- Zecta tries to be give easier low-level and memory access with memory-safety and without garbage-collector
- Zecta provides neither verbose nor bloat syntax, but packs enough features
- Zecta will be perfect for Game Development and performance-critical tasks with better readablity


```zig
# program main

func main() void{
    console.print("Hello, Zecta! \n");
}

```






# Types in Zecta

There are 4 types of types in Zecta

```java
1 -  Data types

        1.1 -  Core types (int, float)
                1.1.1 -  Sub-types (int64, f128)

        1.2 -  Class types
                1.2.1 -  Built-in Class types (math::real)
                1.2.2 -  User defined Class types (custom types)


2 -  Composite types (var, func, class)

3. Meta-Types (auto, hybrid)
```




# Core Types

int - 32-bit integer

float - 64-bit floating-point number.

char - 1 byte ASCII character.

string - shrinkable ASCII text.

bool - stores either true or false in 1 byte.

void - represents void(nothing).





# Composite Types

func - function with flexible & safe structure

array - array that holds value, multi-dimension supported

class - strcutures for objects with members, classvars and methods for each one

map - holds a key and a value for each instance

set - non-queued arrays

unit - class-like OOP structures

module - namespaces that usually used for libraries and files

enum - type that holds a name and a integer value for it

stipule - stipules for bool value checking





# Sub-types

### Sub-ints:
    int8, int16, int64, int128 ...   >> integer types with different size 
    uint, uint8, uint32, uint64 ...  >> unsigned integer types
    int_min, int_max, int_mid ...    >> compiler picks size according to performance 


### Sub-floats:
    f8, f16, f32, f128 ...                  >> float types with different sizes
    ufloat, ufloat8, ufloat16, ufloat32...  >> unsigned float types
    f_min, f_max, f_mid ...                 >> compiler picks size according to performance 


### Sub- Char & Strings:
    uchar, ustring                  >> unicode encoded char/strings
    str8, str64, str256, str1024 ...  >> static-sized and faster strings
    strdecl      >> this string sub-type sets size once when declared only
    strinit     >> string sub-type that sets size once, when initialized 
    strdef      >> this sub-type sets size once, when defined


We will discuss other types later;





# Comments
There are 5 type of comments in zecta


1. Basic Comments

```zig
    // single line comments
    /* this is multi line comment */
```


2. Documentation Comments

```zig
    /// doc comment
    /** multi line doc comment **/
```


3. Helper Comments

```zig
//! TODO:	Marks pending work.	//! TODO: Optimize this fn.

//? DEBUG:	Debugging hints.	//? DEBUG: Check bounds here.
```


4. Regions

- can nest all type of comments
- Regions start and end with triple backticks (```)

example of region comments:
```zig
```region1
optional region name

/* nested comments */
 
ending of region1```
```


6. Shebang Support

```--[ /usr/bin/env zecta ]--```

Zecta provides very rare but clean shebang





# Variables

Variables have types and a value.

Declaration & definition:

```zig
var type variable_name = value;

var type variable_name { value };
```


Placeholder variable for discarded value:
`_`


Variables can't change type, but can change value:

```zig
var int x = 10;
var float y = 15.750;
var string txt = "this is a string";
var bool a = true;
x = y; // value of x changed to value of y
```

Grouped declaration:

`var int x, y = 10, 15;`




# Constants

Constants can not change neither type nor value

```zig
const int64 PI = 3.14159265358;
PI = 4; // Error
```

They provide faster execution because variables resolved at compile time and guaranteed that can not change





# Meta-Types

automatic type detection

```zig
var auto x = 5;               // sets type to int automatically
var auto<int, float> y = 10;  // automatically chooses beetwen types faster
```

import needed type-declaretion utilities:


Dynamic Types
```zig
import 'MetaTypes_Dynamic'

dynamic b = 20; // can change to any type
dynamic int z = 10; // can change type, originally int
dynamic<int, float> int a = 10; // only switch between int, float
```

Hybrid Types
```zig
import 'MetaTypes_Hybrid'

hybrid y = "string value"; // stores all types simultaneously
hybrid<int, bool> c = true; // holds types at once
```




# Standart Input / Output

### Output

```zig
# program main

func main() void
{
    var string12b name = "Ziya";
    var int8 age = 15;

    console.print("My name is $name and my age is $age", { string12b, int8 });  // faster
    newl;  // adds new line
    console.out("my name is ", name, " and my age is ", age);  // slower
}
```

Both "print" and "out" function does not end line automatically. We should write "\n" as a
standart escape sequence for new line or "newl" at the end


### Input

```zig
# program main

func main() void{
    var string full_name;
    var int age;

    console.prompt<string>("Enter your full name: ", &full_name);
    // reads full line as a prompt, takes 2 arguments.

    console.get<int>("Enter yout age: ", &age);
    // Gets input until the first space character and as a variadic function, accepts a variable number of arguments.
}

```

These were main I/O structures in Zecta, but there are other methods for console object below;

### Console methods

```
# program main

func main() void{
    console.flush();
    console.clear();
    console.play(300, 2);  // play sound 300 hz sound from console for 2 seconds
    console.setCursor(10, 3);  // 10th columns, 3rd row
    console.getRow();
    console.getColumn();
    console.title("Window");  // set the title of the console window
}

```





# Type conversions and typeof()

```
var float x = 5.255;

// var int y = x; would throw an error
var int y = cast<int>(x);  // will cast x to int and define y's value to x safely
```


### Stringify function

This function can take so many things as an argument, and dynamically converts to the string
 
```zig
var float x = 15.001;
var string s = stringify(x).append("str");

console.print("$s", {string}); // output is 15.001str

```


typeof() function returns type object which is very flexible and rare
```
console.out("type of x is: ", stringify(typeof(x)), "and type of y is: ", stringify(typeof(y)));

var typeof(x) z = 25.75;  // will declare a variable with same type of x
```

typename() function
gets type object(like typeof() returns) or variable name as an argument and returns string 
```
console.out("type of x is: ", typename(x), "and type of y is: ", typename(y));
```























Other type conversions are available as methods which will be discussed after.
