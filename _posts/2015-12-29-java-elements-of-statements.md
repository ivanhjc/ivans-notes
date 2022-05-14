---
title: "Java: Elements of Statements"
last_modified_at: 2020-10-14
categories:
  - Java
tags:
  - Programming
classes: narrow
toc: true
---

Literals, identifiers, symbols, values, types
---------------------------------------------

A value is a number, a character, a string of characters, or a boolean,
etc.

Literals make the names of values. A literal could be a digit, a
character, or a "symbol". For example, 100 contains the literals "1",
"0", "0" and represents the value of one hundred.

A type is a set of values. Java is a statically-typed language which
means every value has a designated type, or in other words, there's no
values that don't have a type. Java types can be divided into two
categories, **primitive types** and **reference types** (or **object
types**).

### Identifiers

An identifier is an unlimited-length sequence of Unicode letters and
digits used as the names of variables, methods and classes. An
indentifier can start with a letter, an underscore `_`, or a dollar sign
`$`, but it's good practice to always begin with a letter. It cannot
start with any other kind of characters including digits, whitespace,
hyphen, asterisk, equal sign, etc, and it cannot contain whitespaces. In
Java identifiers are case sensitive, for example, `foo` and `Foo` are
different identifiers.

Identifiers cannot be reserved words such as `class`, `public`,
`static`, `if`, `else`, `while`, etc.

It's a good practice to always use meaningful names for variables
instead of abbreviations. If the name consists of only one word, spell
it in all lowercase letters, and if it consists of more than one word,
capitalize the first letter of each subsequent word, such as
`firstTime`. This is called **camel casing**. If the variable contains a
constant value, capitalize every letter and separate subsequent words
with underscores, such as `DEFAULT_VALUE`.

By convention class names should begin with upper case letters, and
variable and method names should begin with lower case letters.

Periods are used to indicate different levels of containment in compound
names (also called **qualified names**), e.g. `System.out.println()`.

### Symbols

* `{ }` Used to group things together. If there are no curly braces in above structures only the first line of the statements will be performed. 
* `//` In-line comment 
* `/*…*/` Block comment 
* `/**…*/` Javadoc comment `Spaces` They do not affect the program, but are useful for organizing code.

### Types of types

Java is a strictly-typed language. Every value and every variable has
their own type, and each variable can only store a value of the same
type. There are two types of Java types: primitive types and reference
types.

1.  Primitive types

    Primitive types of values are represented using only a certain
    finite number of bits (a bit is a 0 or 1 and 8 bits is one byte).

    Names of primitive types begin with lower-case letters.

    When you declare a primitive variable you get a storage space for a
    primitive value.

    You can not create new primitive types in Java.

    There are 8 primitive types in Java: `byte`, `short`, `int`, `long`,
    `float`, `double`, `char`, `boolean`.

2.  Reference types

    Reference types (also called **object types**) usually represent
    more complicated data.

    Names of object types should begin with upper-case letters.

    When you declare an object variable you get a storage space for a
    reference to the object. To get space for the object itself you
    should use `new`.

    You can create new object types.

    Java is an object-oriented programming language and most Java types
    are object types, such as `String`, `Point`, `Rectangle`, etc.
    Arrays are also object types. `null` is a special value that means
    "no objects" and can be assign to any object type variable.

### Numbers

-   Numerical literals can include underscores as separators of digit
    groups, e.g. 1<sub>000000</sub>, 2<sub>000</sub>.000<sub>001</sub>
-   Numbers can be represented using scientific notation, e.g. 1.3e10,
    3.5E200, 10e10.

1.  Integers

    Whole numbers. Integers are represented bitwise using [Two's
    Complement](https://www.cs.cornell.edu/~tomf/notes/cps104/twoscomp.html).
    See integer clock.

    A `byte` type integer takes up a single byte (a sequence of 8 bits)
    of memory, which makes this type of numbers range from -128
    (-2<sup>7</sup>) to 127 (2<sup>7</sup>-1), inclusive. See [Why is
    the range of bytes 128 to 127 in
    Java](http://stackoverflow.com/questions/3621067/why-is-the-range-of-bytes-128-to-127-in-java).

    A `short` type integer takes up 2 bytes (16 bits) and ranges from
    -2<sup>15</sup> to 2<sup>15</sup>-1.

    An `int` type integer takes up 4 bytes (32 bits) and ranges from
    -2<sup>31</sup> and 2<sup>31</sup>-1 \[&gt;\] (approx. four billion
    numbers). It's the default type for integers in Java. See
    [StackOverflow: The range of
    int](d:Stack Overflow - Java the range of int.pdf).

    A `long` type integer takes up 8 bytes (64 bits) and ranges from
    -2<sup>63</sup> to 2<sup>63</sup>-1. Integers of this type are
    represented by appending an "l" or "L' at the end of the number,
    e.g. 500L.

2.  Floating-point numbers

    Fractional numbers, real numbers.

    A `float` type number takes up 4 bytes and ranges up to
    10<sup>38</sup> with 7 significant digits at most. Numbers of this
    type end with an "f" or "F", e.g. 1.0F, 2f.

    A `double` type number takes up 8 bytes and ranges up to
    1.7x10<sup>308</sup> with 15 significant digits at most. It's the
    default type in Java for floating-point numbers.

3.  Radices

    Numbers can be in different radices:

    -   Binary: beginning with `0b` or `0B`, e.g. `0b101`
    -   Octal: beginning with with `0`, e.g. `077`
    -   Hexadecimal: beginning with `0x` or `0X`, e.g. `0x9a`

### Characters

Characters are of type `char` and a character takes up 2 bytes of
memory. A character is specified in the Unicode character set, which may
be a letter, a number, or a symbol, and should be enclosed in single
quotes when represented, such as 'a', '1', etc.

A character is stored as a 16-bits (short) integer which represents its
position in the Unicode set, called Unicode number. In Java the
character and its Unicode number is equivalent and can be used
interchangeably. For example, you can assign a number to a `char` type
variable or convert a number to a character with typecasting:

``` example
char character = 233;
int number = 'é';
System.out.println((char) 233); // output: é
```

A character can be represented with `\u` followed by four hexadecimal
digits. e.g. `'\u00E9'` -&gt; `'é'`. You can check a character's hex
number in the character map (Windows).

Not all characters can be represented with one letter or symbol either
because they are invisible functional characters such as a tab or a
linefeed, or the letters and symbols conflict with reserved literals.
These special characters could be represented as escaped characters by
using a backslash `\`. Some common escaped characters are:

-   `\t`: a tab
-   `\r`: a carriage return
-   `\n`: a linefeed
-   `\b`: a backspace
-   `\f`: a formfeed
-   `\'`: a single quote
-   `\"`: a double quote
-   `\\`: a back slash

### Boolean values

The results of logical propositions. A `boolean` value is either `true`
or `false` and has type `boolean`.

### Strings

A sequence of one or more characters enclosed in double quotes.

Operators
---------

-   For these operators the order of operations is based on the rules of
    precedence.
-   They only work with primitive types.

### Arithmetic

-   `+`: Add (numbers, characters), concatenating (strings)
-   `-`: Subtract
-   `*`: Multiply
-   `/`: Divide
-   `%`: Modulus operation, works on integers and yields the remainder of the first operand divided by the second. It also works on real numbers and yields the residue of the first operand subtracted as many copies as possible of the second.
-   `i++`: Increment the value of `i` by 1 for its next use. `i` can be
    of type int or char.
-   `i--`: Decrement the value of `i` by 1 for its next use. `i` can be
    of type int or char.
-   `++i`: Increment the value of `i` by 1 immediately. `i` can be of
    type int or char.
-   `--i`: Decrement the value of `i` by 1 immediately. `i` can be of
    type int or char.

NOTE:

-   For `+,-,*,/` if the operands are all integers, the result is also
    an integer or otherwise a floating-point number. For the division of
    two integers the result always rounds down to the nearest integer.
-   A char is converted into its Unicode code number when it is used
    with an arithmetic operator.

### Assignment

-   `=` Assign
-   `+=` Add a value to the current value of an int or double, e.g. x +=
    y ⇔ x = x + y
-   `-=` Subtract a value from the current value of an int or double,
    e.g. x -= y ⇔ x = x - y
-   `*=` x \*= y ⇔ x = x\*y
-   `/=` x /= y ⇔ x = x/y
-   `%=` x %= y ⇔ x = x % y
-   `&&=` p &&= q ⇔ p = p && q

### Comparison/Relational

-   `==` Equal to
-   `!=` Not equal to
-   `>` Greater than
-   `<` Less than
-   `>=` Greater than or equal to
-   `<=` Less than or equal to

NOTE:

-   The two sides of of a condition operator have to be the same type.
-   They can be used to compare values of type char according to their
    numeric Unicode values.

- `instanceof`: Compares an object to a specified type. You can use it to
test if an object is an instance of a class, an instance of a subclass,
or an instance of a class that implements a particular interface. null
is not an instance of anything.

### Logical/Conditional

-   `&&` Short-circuit and
-   `||` Short-circuit or
-   `!` Not
-   `? :` The ternary operator. `var = <exp1> ? <exp2> : <exp3>;` If
    exp1 is true, returns exp2, or else returns
    -   exp3

Precedence of logical operators:

- `!` High 
- `&&` Medium 
- `||` Low

### Bitwise

-   `&` Bitwise AND
-   `|` Bitwise inclusive OR
-   `^` Bitwise exclusive OR, XOR, e.g.
    0<sup>0</sup>=0，1<sup>0</sup>=1，0<sup>1</sup>=1，1<sup>1</sup>=0
-   `~` Unary bitwise complement, which inverts every bit of a value,
    e.g. if x = 1 is a byte, then \~x == -2, because \~00000001 == 11111110. A negative integer is
        represented by inverting its positive counterpart plus 1, e.g.
        -1 == \~1 + 1, which is called Two's Complement. If a is an
        integer, then \~a=−a−1. The first bit of negative integers is
        always 1.
-   `<<` Signed left shift
-   `>>` Signed right shift
-   `>>>` Unsigned right shift

Variables
---------

### Type conversion

Variables have types. A type is a set of values. A variable is either a
*primitive types* or a *reference type*. A variable can only hold a
value of same type, or type which is a subset of the variable type. For
example, an `int` variable can hold a `byte` or `short` value, but not a
`long` value, neither a `float` or `double` value. But you can convert
these values to `int`.

1.  Automatic conversion

    In some cases values are converted automatically.

    When an integer is assigned to a `double` variable it is
    automatically converted to `double`. When the right side of the
    assingment is an expression with all operands being integers, Java
    evaluates the expression before the conversion. Thus, the result of
    the statement `double q = 1/2;` is 0.0, not 0.5. To gain 0.5 just
    write either or both of the operands to float-point, i.e., 1.0/2.0.

    When assigning `char` values to `int` variables, or `int` values
    between 0 and 65545 to `char` variables, the values are
    automatically converted. This is because `char` is in fact
    equivalent to `int`.

    When evaluating an arithmetic expression if all operands are
    integers then the result is an integer, and if one of the operands
    is a float-point number the result is a float-point number.

    When use `+` to concatenate strings the result is a string. For
    example, `1 + "foo"` produces `"1foo"`.

2.  Typecast

    Typecast is to convert the type of a value to another type by using
    the typecasting operator `(<type>)` before the value or variable to
    convert. Not all types can be typecasted to one another. Typecast
    can happen between numeric types, between a numeric type and a
    `char` type, and between objects.

    Type conversion from a numeric type to a higher-bit numeric type is
    automatic, e.g. from `short` to `int`, but converting a numeric type
    to a lower-bit numeric type is forced by using the operator
    `(<type>)`, e.g. `short foo = (short) 100000`. The result of this
    type of conversion is

    ``` example
    (n - max) % range - 1 + min
    ```

    -   n: the integer to be converted
    -   max: the max value of the the type to be converted into
    -   range: the range of the values of the type from min to max
    -   min: the min value of the type

    Type conversion from a floating-point to an integer always rounds
    down. For example, `(int) 0.9` produces 0.

    Typecast takes precedence over arithmetic operations. For example,
    in

    ``` java
    double pi = 3.14; 
    int x = (int) pi * 20.0; 
    ```

    x gives 60 rather than 62.

    Between char and int: `(char) 233` -&gt; é, `(int) 'é'` -&gt; 233

    Between object types that have inheritance relationship.

3.  Using methods

    `int` to `String`:

    ``` java
    String s = String.valueOf(number); 
    String s = Integer.toString(int number); 
    String s = "" + number;
    ```

    `String` to `int`:

    ``` java
    int foo = Integer.parseInt("5");
    ```

    `String` to `double`:

    ``` java
    double dou = Double.parseDouble("3.14");
    ```

    `int` to `Double`:

    ``` java
    Double n = new Integer(i).doubleValue();
    Double n = Integer.valueOf(i).doubleValue();
    ```

### Declaration

-   It is the process of deciding the type of the variable before
    assigning the value.
-   It is marked by putting the value type before the variable name,
    e.g. String bob.
-   You can declare a list of variable names such as String bob, dylan,
    felix.

### Assignment

-   The left side of an assignment has to be a variable name for it
    indicates the storage location where the value will go.
-   Expressions do not represent storage locations, only values.
-   The type of the value and the variable in an assignment must be the
    same.

### Initializtion

The process of declaring a variable and assigning a value to it at the
same time. e.g. `String name = "Bob";`

You can initialize multiple variables with only one type declaration.
E.g. `String name1 = "Bob", name2 = "John", name3 = "Felix";`

Default values: Variables that are not initialized have default values
that depends on their types.

-   int variable defaults to 0
-   boolean variable defaults to false
-   object variable defaults to null

### Usages

-   Intermediate/Temporary variables: Variables that are used in
    computation but never printed

-   Flags: Variables that flag the presence or absence of some
    condition, e.g. evenFlag in

    ``` java
    boolean evenFlag = (n % 2 = 0); 
    if (evenFlag) { 
        System.out.println("n is even"); 
    }
    ```

-   Local variables:

    -   variables declared inside a method definition
    -   only exist inside the method

-   Member variables/Global variables:

    -   Variables that are declared outside any method
    -   Can be marked with modifiers such as static, public and private
        -   static member variables
        -   non-static member variables

-   Parameters

-   Class variables

-   Instance variables

-   Fields: refer to both class variables and instance variables.
    Variables refer to all of the above.

### Mutable and immutable variables

-   A variable is mutable if its orignal value can be modified by using
    some methods, and immutable if its original value can't be modified
    through invoking methods.
-   Primitive variables are immutable, while object (except string)
    variables are mutable.

Reserved words
--------------

-   `println` short for "print line", adds a special character called
    newline after each line, which moves the cursor to the next line of the display
-   `print` displays the output from multiple print statements all on
    one line. The inside of a print statement can be an expression.
-   `return`
-   `new`
-   `import`
