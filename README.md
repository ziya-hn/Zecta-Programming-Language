# ZECTA PROGRAMMING LANGUAGE DOCUMENTATION

Powerful as C++🔥, fast as C👨‍💻, Basic as Zig🎯


# Introduction

- Zecta is a Modern mid-level compiled langauge with high performance and flexibility
- Zecta tries to be give easier low-level and memory access with memory-safety and without garbage-collector
- Zecta provides neither verbose nor bloat syntax, but packs enough features
- Zecta will be perfect for Game Development and performance-critical tasks with better readablity

```
# program main

func main() void{
    print.format("Hello, Zecta");
}

```

- Every condition containers called conditions
- Semicolons are strictly required after actions
- Zecta has advanced feature controlabilty

# Primitive types



int - 32-bit integer.

float - 64-bit floating-point number.

char - 1 byte ASCII character.

string - shrinkable ASCII text.

bool - true/false stored in 1 byte.

void - represents void(nothing).

# Other types

func - function

array - array

vector - 1D vector

matrix - 2D matrix

tensor - 3D+ tensor, needs import

class - class

map - map

set - set

unit - unit

module - module

enum - enum

stipule - stipules, needs import

obj - object, needs import


# Sub-types

### Sub-ints:
    int8, int16, int64, int128 ...   >> integer types with different size 
    uint, uint8, uint32, uint64 ...  >> unsigned integer types
    int_min, int_max, int_mid ...    >> compiler picks size according to performance 

### Sub-floats:
    f8, f16, f32, f128 ...                  >> float types with different size 
    Ufloat, Ufloat8, Ufloat16, Ufloat32...  >> unsigned float types
    f_min, f_max, f_mid ...                 >> compiler picks size according to performance 

### Sub- Char & Strings:
    unichar, ustring                  >> unicode encoded char/strings
    str8, str64, str256, str1024 ...  >> limited-size and faster strings



# Variables

Declaration & definition:

`type_name variable_name = value;`

`type_name variable_name { value }`

Placeholder for empty value:

`_null`

Variables can't change type, but can change value:
```
int x = 10;
float y = 15.750;
string txt = "this is a string";
bool a = true;
x = y; // value of x changed to value of y
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

automatic type detection

`autoT x = 5; // sets type to int`

import needed type-declaretion utilities:
```
import 'dynamic\hybrid'

dynamic b = 20; // can change to any type
dynamic int z = 10; // can change type, originally int
dynamic<int, float> int a = 10; // only switch between int, float
hybrid y = "it stores all types"; // stores all types simultaneously
hybrid<int, bool> c = true; // holds both types at once
```

# Input / Output

Outputting with ascii
```
print.format("text here");` // raw text
print.format<int>("text here $var_name_here");`  // variable interpolated text
print.direct("text here $variable_name_here");`  // variable interpolated with implicit type detection
print.split("text here", var_name, "text here");`  // variables and text splited as arguments

```
Inputing with ascii
```
prompt.get(&x);
prompt.get<int>(&x);
prompt.read(&x);
prompt.read<string>(&x);
prompt.ask("set the value of x: ", &x);

```

For Unicode outputting, use
`U_print`  and  `U_prompt`


### Arithmetic Operators

-  '+' => Addition

-  '-' => Subtraction

-  '*' => Multiplication

-  '/' => Division

-  '%' => Modulus

-  '^' => Exponent

### Assignment Operators

+=, -=, *=, /=, %=, ^=

### Comparison and Boolean Operators

&&, and → AND

||, or → OR

!, not → NOT

==, is → Equal

!= → Not equal

<, >, <=, >=  -> smaller, greater

### other operators

- ""  -> string
- ''  -> library/file name etc.
- [] -> usually index operator or map key
- &   -> reference operator


# Type conversions and typeof()
```
float x = 5.255;

// typeof function returns type object
typeof(x) y = 10.25;  // creates a variable with same type of x variable
// for returning type with string
print.format(typename(x));  // string output: float

print.format(typecast<int>(x));             // casts x safely, not all types to cast supported
print.format(dynamic_typecast<string>(x));  // casts x less safely, more types supported than "typecast"

string z = stringfy(x);  // this excepts everything and stringizes everything lol
// So lines below gives same result
print.format(stringify(typeof(x)));
print.format(typename(x));
```

So many type conversions are available as methods which will discussed after;



# Conditionals
if/else:
```
int x, y = 5, 10;
if [x < y] {  // Zecta using braces for conditions to not mixing expressional paranthesis with conditional paranthesis
    print.format("y is greater");
} elif [x > y] {
    print.format("x is greater");
} else {
    print.format("they are equal");
}
```

Switch-case:
```
switch[x] {
    case 1  :>  print.format("x is 1"); break;
    case 2  :>  print.format("x is 2"); pass;
    case 0  :>  print.format("x is 0");
    default :>  print.format("x is unknown");
}
```

Match-when:
```
match[x]
    when [x > 10] {
        print.format("x is greater than 10");
    } break;
    when [x > 5] {
        print.format("x is greater than 5");
    }
    when [x > 0] {
        print.format("x is greater than 0");
    }
    otherwise {
        print.format("x is unknown");
    }
end   // Yes matches end with end keyword for clarity beetwen curly braces
```

Alternative ternary:
".." for else if logic, "..." for else logic

`opt (x > y) x .. (x < y) y ... x + y end`


# Loops

while loops

```
while [x != 1] {
    print.format("x");
    x++;
}
```


until loops
```
until [x == 10] {
    print.format<int>("$x");
    x++;
}
```

do-while loops
First do statement inside scope then check the condition

```
doWhile [x <= 10] {
    print.format<int>("$x");
    x++;
}
```


in for loops, the type of index variable is int by default and can be typed to another by just writing it

```
for[i = 0; i <= 100; i++] {
    print.format<int>("$i");
}
```


for-each loops

```
foreach [int i : array] {
    print.format<int>("$i");
}
```


# Functions

`  'func' + func_name + (type + parameter_name) + return_type + {}  `

Declaration:

`func sum(float x, float y);`
or
`func sum(float x, float y) float;`

Definition:
```
func sum(float x, y) float {  // no need to write float twice
    return: x + y;
}

func sample(int|float x);  // argument can be either type int or float

```

Return types and main exit code:

return type of a function comes after parameters paranthesis and before scope begins:
`func sample() void{ print.format("sample function") }`
main return types are: void, int, float, string, bool. we will also discuss return definers (const, override etc.)

When program finishes, it returns a integer value to the operating system. it is 0 by default but we can handle it by ourselves:
```
func main() void{
    system.exit(0);  // says "there is not problems in program" to OS
}
```
Usual meanings of exit codes
0 => Success
1 => General error
2 => Misuse of shell commands
... => Depends on OS/program

Variadic functions:
Variadic function arguments are stored in the type "func_arr" which is similar to an array and programmer can not access
```
func multiply(int x, float a...) int {
    int result = x;
    for(i = 0; i < a.count(); i++) {
        result *= a.index(i);
    }
    return: result;
}
```

Generic functions:

These functions gave us an opportinity to choose the type and/or handle types better in function definition.

```
func sample<T>() void{
    if[typeof(T) == typeobj::int] print.format("generic type is integer")
}

func main() void{
    sample<int>();  // output: generic type is integer
}
```


# Stipules (import needed)

`  'stipule' + stipule_name + '?' + (type + parameter_name) + {}  `

stipule examples:
```
stipule isEven? (int|float x) {
   if [x % 2] == 0 {
       return true;
   }
   return false;

func main() void{
    int x;
    prompt.get(&x);  // set x to user input
    isEven?(x): { print.format("x is even"); } // outputs if x is even
}
```

# Arrays
an example of 2 dimensional array:
```
array<int> arr { { 3, 10, 15, 20, 30 }, { 4, 9, 12, 27, 38 } };
arr[0][1] = 13;
print.format<int>("$arr[0][1]");  // 13
arr[1][0] = _null;  // will empty this chunk
print.format<int>("$arr[1][0]")  // empty output
arr.empty?() { print.format("array is empty"); }  // would output if 'arr' array was really empty

```


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
unit to child unit => "."
unit to unitvar or method => "."
unit to static unitvar or static method => ":"

`parent_unit::child_unit.unitvar`

Unit examples:
```
unit subject {
    unit Physics;
    unit Chemisty;
    unit Biology;

    int GPA;

    setGPA(f8 GPA) void{
        this.GPA = GPA
        if[GPA > 5] GPA = 5
        if[GPA < 0] GPA = 0;
    }
    getGPA() f8{
        return this.GPA;  // this is not optional even if it refers to unitvar
    }
}

func main() void{
    print.format<int>("$subject.Physics.getGPA()");
}
```

for modifying all unitvars at the same time, make this unitvar static so parent unit can modify all child units at the same time
```
unit Parent{
    unit child1
    unit child2

    static int x;
}

func main() void{
    child1.x = 5
    child2.x = 15
    Parent:x = 10
    print.format<int>("$Parent:x");  // 10
    print.format<int>("$Parent::child1.x");  // 10
    print.format<int>("$Parent::child1.x");  // 10
}
```

# Modules
Modules can contain variables, functions, classes, units and libraries imported in
Modules used in core Zecta for creating same-named libraries

notations:
module to variable => '.'
module to function => ':'
module to class => '::'
module to unit => '::'

```
# program main

module myModule{
    func printf(string text) { print.format<string>("${text}"); }
}

func main() void{
    myModule:printf("sample");
}
```


# importing libraries/files
```
import 'math' // imports math library
import 'random' as rand  // imports random library as rand
import_file 'myfile' // imports user defined file
import_next 'myheader'  // import the next matching header in the path order
```

most of the libraries accessed via their name
```
func main() void{
    print.format<int64>(math:PI);
}
```

# File headers

all files in project should contain file headers, but secondary file headers are optional
```
# program main  // compiler runs this file first
# program myProgram  // 'myProgram' file's header, accesible by other files via 'import_file'
``` 

secondary file headers
```
# public program main  // visible by other files without any import
# private program main  // neither visible nor importable
# import_guard  // prevents multi-import
```

# variable function/stipules

sizeof(var)      returns size of variable in bytes
typeof(var)      returns type name of variable
typecast<>(var)  staticly casts a type of variable
const?(var)      checks if variable is constant
immut?(var)      checks if the variable has fixed type


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

`math`, `time`, `memory`, `dynamic\hybrid`, `custom`, `tensor`,
`stipule`, `obj`, `Zgame`, `SDL2`

Math library:
variables/constants -> math:PI, math:Euler, math:TAU
classes/types       -> math::real, math::degree, math::radian, math::vec2, math::vec3
functions/methods   -> math::root(), math::sin(), math::cos(), math::tan(), math::atan(),
                       math::min(), math::max(), math::lerp()

Time library:
variables/constants -> time:zecta_time
classes/types       -> time::sec, time::ms, time::timer, time::clock
functions/methods   -> time:wait(), time::clock.now(), time::timer timer.start(), timer.stop()

Memory library:
variables/constants -> memory:NULL, memory:PAGE_SIZE
classes/types       -> memory::raw, memory::ptr, memory::alloc
functions/methods   -> memory::size(), memory::bitsize(), memory::alloc.bytes(),
                       memory::free(), memory::trace()


dynamic\hybrid library
variables/constants -> dynamic:NULL, hybrid:NULL
classes/types       -> dynamic<>, hybrid<>, hybrid
functions/methods   -> dynamic::typeid(), hybrid::cast(), hybrid::reset(), hybrid::view()


Custom lib utilities:
```
// safe macros
@custom('macro') dowhile <=> until
@custom('type') number <=> math::real
@custom('func') print(string arg) <=> print.format(arg)

// Zecta Feature Control
@enable 'Uppercase-Global'
@enable 'Uppercase-Classname'

@disable 'Conditional-Bracket'
@enable 'Conditional-paranthesis'
```


# Standart IO library

```
# program main

import 'stdio'

func main() void
{
    int x;

    stdio.call_console();
    stdio.out("ascii output");  // stdio.wout() for unicode output
    stdio.in(&x);    // stdio.win() for unicode input
    stdio.err("output error message");  // stdio.werr() for unicode output
    stdio.exit_console();
```


# File writing/reading

```txt
    
    file.create('firstfile.txt');  // create non-existing .txt file
    file.open('firstfile.txt');   // open existing .txt file
    file.close('firstfile.txt')  // close file
    file.open('firstfile.txt', 'file1')  // open file as 'file1'
      //

    file1.open?() {  // stipule that checkes if file is open
        file2.write("writing first line of file2"); newl;
        string8 s = file2.readchars(0, 1);  // read and store 1st character of file2 in s variable
        file2.close()
    }


    // file Cursor
    file.open('file1.txt', file1);
    file1.cursor.get_row();  // get count of rows above the the cursor
    file1.cursor.get_column();  // get count of columns behind cursor
    file1.cursor.set_row();  // set count of rows above the the cursor
    file1.cursor.set_column();  // set count of columns behind cursor
    file1.cursor.setposition(2, 4);  // set row and columns location of cursor
    file1.cursor.move(3, 6);  // add values of arguments to current position

    // Read function
    string1024 txt;
    txt = file1.read()  // read text in row of cursor and columns which comes after cursor
    txt = file1.read_row(0)  // read first row
    txt = file1.read_column(0)  // read first column
    txt = file1.read(1, 5)  // read first row and fifth column
    txt = file1.read_area(1, 10, 5, 12);  // read row 1 to ro 5 and column 10 to 12
    txt = file1.read_range(1, 10, 5, 12);  // read row 1 to ro 10 and column 5 to 12
    
}

```





































































