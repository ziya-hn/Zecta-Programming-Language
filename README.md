# ZECTA PROGRAMMING LANGUAGE

Powerful as C++🔥, fast as C👨‍💻, Basic as Zig🎯

# Introduction

- Zecta is a Modern mid-level compiled langauge with high performance and flexibility
- Zecta tries to be give easier low-level and memory access with memory-safety and without garbage-collector
- Zecta provides neither verbose nor bloat syntax, but packs enough features
- Zecta will be perfect for Game Development and performance critical tasks with better readablity
```
# program main

func main() void{
    print.format("Hello, Zecta");
}
```
- Every line of command statement called actions
- Every condition containers called conditions
- Semicolons are optional after actions, unless there is more than one action
- Zecta has improved feature controlabilty

# Primitive types

int - 32-bit integer. Others: int8, int16, int64, int128

float - 64-bit floating-point number. Others: f16, f32, f128, f256

string - ASCII text, shrinkable. Fixed-size: string8, string16, ..., string512

U_string - Unicode text, shrinkable. Fixed-size: U_string8, ..., U_string512

bool - true/false in 1 byte. Can also use 1/0, True/False

autoT - exclusive type holder, stores only one type at a time

void - represents void(nothing)

# Other types

func - function

stipule - stipules, needs import

class - class

unit - unit

module - module

array - array

vector - 1D vector

matrix - 2D matrix

tensor - 3D+ tensor, needs import

map - map

set - set

obj - object, needs import


# Variables

Declaration & definition:

type_name variable_name = value

type_name variable_name { value }

Placeholder for empty value:

_null

Variables can't change type, but can change value:
```
int x = 10;
float y = 15.750;
string txt = "this is a string";
bool a = true;
x = y; // x becomes y (type check enforced)
```
Grouped declaration:

`int x, y = 10, 15;`

# Constants

Constants can not change neither type nor value 
```
const PI = 3.141592653;
PI = 4; // Error
```

# More about types

`autoT x = 5; // sets type to int`
// import needed:
`dynamic<> b = 20; // can change to any type`
`dynamic<> int z = 10; // can change type, originally int`
`dynamic<int, float> int a = 10; // only switch between int, float`
`hybrid<> y = "it stores all types"; // stores all types simultaneously`
`hybrid<int, bool> c = true; // holds both types at once`


# Input / Output

`print.format("text here");` // raw text
`print.format<int>("text here $var_name_here");`  // variable interpolated text
`print.direct("text here $variable_name_here");`  // variable interpolated with implicit type detection
`print.split("text here", var_name, "text here");`  // variables and text splited as arguments

`prompt.get(&x);`
`prompt.get<int>(&x);`
`prompt.read(&x);`
`prompt.read<string>(&x);`
`prompt.ask("set the value of x: ", &x);`


# Arithmetic Operators

+ Addition

- Subtraction

* Multiplication

/ Division

% Modulus

^ Exponent

# Assignment Operators

+=, -=, *=, /=, %=

# Comparison and Boolean Operators

&&, and → AND

||, or → OR

!, not → NOT

==, is → Equal

!= → Not equal

<, >, <=, >=

# other operators

""  -> string
''  -> library/file name etc.
[] -> usually index operator
&   -> reference operator


# Conditionals
if/else:
`int x, y = 5, 10;`
`if [x < y] {`  // condition can be written without braces
`    print.format("y is greater");`
`} elif [x > y] {`
`    print.format("x is greater");`
`} else {`
`    print.format("they are equal");`
`}`

Switch-case:

`switch(x) {`
`    case 1: print.format("x is 1"); break;`
`    case 2: print.format("x is 2"); pass;`
`    case 0: print.format("x is 0");`
`    default: print.format("x is unknown");`
`}`

Match-when:

`match(x)`
`    when [x > 10] {`
`        print.format("x is greater than 10");`
`    } break;`
`    when [x > 5] {`
`        print.format("x is greater than 5");`
`    }`
`    when [x > 0] {`
`        print.format("x is greater than 0");`
`    }`
`    otherwise {`
`        print.format("x is unknown");`
`    }`
`end`

Alternative ternary:

`opt (x > y) x , (x < y) y .. x + y`

# Loops
while loops
`while [x != 1] {`
`    print.format("x");`
`    x++;`
`}`

until loops
`until [x == 10] {`
`   print.d`
`}`

in for loops, if the type of index variable is int no need to write int, it's typed to int by default
`for[i = 0; i <= 100; i++] {`
`    print.format<int>("$i");`
`}`

foreach loops
`foreach[int i : array] {`
`    print.format<int>("$i");`
`}`

# Functions

'func' + func_name + (type + parameter_name) + return_type + {}

Declaration:

`func sum(float x, float y);`

Definition:

`func sum(float x, float y) float {`
`    return: x + y;`
`}`

`func sample(x, int y) void {}` // x can be any type

`func foo(int|float x);`  // argument can be either type int or float

Variadic example:

`func multiply(int x, float a...) int {`
`    int result = x;`
`    for(i = 0; i < a.argscount(); i++) {`
`        result *= a.index(i);`
`    }`
`    return: result;`
`}`


# Stipules (import needed)

'stipule' + stipule_name + '?' + (type + parameter_name) + {}

stipule examples:
`stipule isEven? (int|float x) {`
`   if [x % 2] == 0 {`
`       return true;`
`   }`
`   return false;`

`func main() void{`
`    int x;`
`    prompt.get(&x);`  // set x to user input
`    isEven?(x): { print.format("x is even"); }` // outputs if x is even
`}`


# Arrays
an example of 2 dimensional array:
`array<int> arr { { 3, 10, 15, 20, 30 }, { 4, 9, 12, 27, 38 } };`
`arr[0][1] = 13;`
`print.format<int>("$arr[0][1]");`  // 13
`arr[1][0] = _null;`  // will empty this chunk
`print.format<int>("$arr[1][0]")`  // empty output
`arr.empty?() { print.format("array is empty"); }`  // would output if 'arr' array was really empty

# Class/OOP in Zecta
Classes contain members, classvars, methods, static methods

notaitons:
Class to child Class => "::"
Class to static methods => ":"
Class to classvar or method => "."


# Units
Units are specific type in zecta, can be used as simplified and easily inherited OOP structure
They are classified objects. they can inherit like a class(parent/child). They have variables called unitvars and functions called

notaitons:
unit to child unit => "::"
unit to unitvar or method => "."
unit to static unitvar or static method => ":"

`parent_unit::child_unit.unitvar`

Unit examples:

`unit subject {`
`    unit Physics;`
`    unit Chemisty;`
`    unit Biology;`

`    int GPA;`

`    setGPA(f8 GPA) void{`
`        this.GPA = GPA`
`        if[GPA > 5] GPA = 5`
`        if[GPA < 0] GPA = `
`    }`
`    getGPA`
`}`

`func main() void{`
`print.format<int>()`
`}`

for modifying all unitvars at the same time, make this unitvar static so parent unit can modify all child units at the same time
`unit Parent{`
`    unit child1`
`    unit child2`

`    static int x;`
`}`

`func main() void{`
`    child1.x = 5`
`    child2.x = 15`
`    Parent:x = 10`
`    print.format<int>("$Parent:x");  // 10`
`    print.format<int>("$Parent::child1.x");  // 10`
`    print.format<int>("$Parent::child1.x");  // 10`
`}`


# Modules
Modules can contain variables, functions, classes, units and library imported in
Modules used in core Zecta for creating same-named libraries

notations:
module to variable => ':'
module to function => ':'
module to class => '::'
module to unit => '::'


`# program main`

`module myModule{`
`    func printf(string text) { print.format<string>("${text}"); }`
`}`

`func main() void{`
`    myModule:printf("sample");`
`}`


# importing libraries/files
`import 'math' ` import math library
`import 'random' as rand ` imports random library as rand
`import_file 'myfile' ` imports user defined file

all libraries accessed via their name
`func main() void{`
`    print.format<int64>(math::PI);`
`}`


# File headers
all files in project should contain file headers, but secondary file headers are optional
`# program main`  // compiler runs this file first, accesible by other files via 'import_file'
`# program myProgram`  // 'myProgram' file's header 

secondary file headers
`# public program main`  // visible by other files without any import
`# private program main`  // neither visible nor importable
`# import_guard`  // prevents multi-import


# variable function/method/stipules
sizeof(var)  // returns size of variable in bytes
typeof(var)  // returns type name of variable
cast<>(var)  // staticly casts a type of variable
const?(var)  // checks if variable is constant
immut?(var)  // checks if the variable has fixed type

# Number types
there are some methods for variables that is int, float or their extensions.
shared functions
sqrt(x)
gcd(x, y...)
lcm(x, y...)

shared methods:
var.abs()  // returns absolute value
var.tostring()  // makes string
var.wholeDigits()  // returns count of digits before decimal point
var.floatingDigits()  // returns count of digits after decimal point

int-special methods:
var.factorial()  // returns factorial
var.prime?()  // checks if the integer is prime number

float-special functions:
round(var), round(var, index)  // rounds number
floor(var), floor(var, index)  // floor of a number
ceil(var), ceil(var, index)  // ceiling of number
clamp(var, low, high)  // clamps number to bounds

# String
strvar.insert("inserted text", 5)
strvar += "appended text"
strvar.find(substring)  // returns beginning index of finded substring
strvar.findend(substring)  // returns ending index of finded substring
strvar.search(substring)  // returns count of substrings inside string

# Useful Libraries
`math`, `time`, `memory`, `dynamic\hybrid`, `custom`, `enable\disable`, `tensor`,
`stipule`, `obj`, `Zgame`, `SDL2`

Math library:
math variables/constants -> math::PI, 
math classes/types       -> math::real, math::degree, math::radian
math functions/methods   -> 


