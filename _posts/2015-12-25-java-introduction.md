---
title: "Java: Introduction"
last_modified_at: 2020-10-14
categories:
  - Java
tags:
  - Programming
---

Java is a high-level programming language. A high-level programming
language is easy to write and read for humans, and it's portable, which
means it can run on different computers and systems. Java, Python, C++,
C, and Perl etc. are all high-level languages. In contrast, a low-level
language such as machine language and assembly language, is hard to
write or read for humans. They can run directly by a computer, while
high-level languages need to be translated to low-level language before
running. A low-level language isn't portable, which means it can only
run on one kind of computer.

There are two ways of translating high-level language to low-level
language: **interpreting** and **compiling**. Interpreting is to
translate a program line by line, alternatively reading lines and
carrying out commands in an interpreter. Compiling is to translate a
program all at once before running any of the commands in a compiler. In
compiling, the high-level language is called the **source code** and the
low-level language is called the **object code** or **executable**. Java
is both interpreted and compiled. Java's compiler generates **byte
code**, a kind of machine language, for Java Virtual Machine (JVM),
which is easy to interpret and portable.

    +-------------+    +----------+    +--------------+    +-------------+    +------------------+
    | source code |--> | compiler |--> | byte code    |--> | interpreter |--> | result on screen |
    | x.java {io} |    +----------+    | x.class {io} |    +-------------+    | {io}             |
    +-------------+                    +--------------+                       +------------------+

The process of analyzing the structure of a sentence is called
**parsing**.

Basic operations in a program for all languages:

-   Input
-   Output
-   Math
-   Testing
-   Repetition

The hierarchy of Java the programming language:

``` example
Library: a collection of method and class definitions
└── Package: a collection of classes, e.g. java.lang, java.awt 
    └── Class: a collection of related methods; a set of objects 
        └── Object: a collection of related data with a set of methods operating on it 
            └── Method: a named collection of statements 
                └── Statement
```

Java is also a development platform which aims at "Write once, run
everywhere", i.e. the same program written in Java can run on various
platforms. Java has different editions:

-   Java Standard Edition (Java SE)
    -   Java Development Kit (JDK)
    -   Java Runtime Environment (JRE)
-   Java Enterprise Edition (Java EE)
-   Java Mobile Edition (Java ME)

Installation
------------

For Windows:

1.  [Download](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
    the package and install it as instructed.

2.  Create the `JAVA_HOME` environment variable: In CMD type:

    ``` example
    setx /m java_home C:\Program Files\Java\jdk1.8.0_101
    ```

3.  Add `%JAVA_HOME%\bin` to your execution path (classpath). See [path
    and class
    path](http://docs.oracle.com/javase/tutorial/essential/environment/paths.html).

4.  Check the JDK version installed on your OS using `javac -version`.

For RHEL-like linux distros (Centos, Fedora), the packages are named as
below:

-   bin: `java-1.8.0-openjdk-devel`
-   bin: `java-11-openjdk-devel.x86_64`
-   src: `java-11-openjdk-src.x86_64`
-   doc: `java-11-openjdk-javadoc.x86_64`

You can install them with `yum` or `dnf`:

``` bash
sudo dnf install java-devel
sudo dnf install java-src
java -version
```

See more at [openjdk](https://openjdk.java.net/install/) and [Fedora
docs](https://docs.fedoraproject.org/en-US/quick-docs/installing-java/).

Quick start
-----------

Your first "Hello World!" program.

Open a text editor and put the following code in it, and save as
"HelloWorld.java":

``` java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

Open the shell on your system, e.g. bash on Linux and CMD on Windows,
run these commands in the directory where the file is saved:

``` example
javac HelloWorld.java
java HelloWorld
```

You should see the output `Hello World!`.

If you bump into this error:

``` example
Exception in thread "main" java.lang.UnsupportedClassVersionError: HelloWorld has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0.
```

See [How to Fix
java.lang.UnsupportedClassVersionError](references/baeldung.org::*How%20to%20Fix%20java.lang.UnsupportedClassVersionError).

As you see in the directory there are two files, `HelloWorld.java` and
`HelloWorld.class`. Files with `.java` suffix are Java source code files
and `.class` are bytecode files compiled from the `.java` files. There's
another file format the jar files which have the suffix `.jar`. These
are Java archive files, where the standard classes are stored. Most of
the standard Java classes are stored in `rt.jar` in your `JAVA_HOME`.

-   Regular jar files:
    -   In Eclipse:
        1.  In package explorer right click the project and select
            "Export";
        2.  Select "JAR File" and click "Next";
        3.  In the box labeled "JAR file" enter a name for the jar file.
            The name should end with ".jar". Click "Finish".
    -   Commands:
        1.  Compile the source code files;
        2.  Execute `jar cf <name>.jar *.class`. This works only if all
            the classes are in the default package; .class means every
            class in the package is included in the jar file. You can
            specify the class names individually and separate them with
            spaces to include only certain classes.
-   Executable jar files:
    -   In Eclipse:
        1.  In the 3rd step of creating a regular jar file, instead of
            clicking "Finish", click "Next" twice to get to the "Jar
            Manifest Specification" screen;
        2.  In the box labeled "Main class" enter the name of the class
            that will be run when the jar file is executed. Click
            "Finish".
    -   Commands:
        1.  Compile the source code files;

        2.  Create a manifest file (a plain-text file without an
            extension) that contains the line

            ``` example
            Main-Class: <class name> 
            ```

            where class name is the name of the class that contains the
            `main()` method. This line must end with a new line. Then
            put the manifest file in the same directory where you will
            issue the `jar` command;

        3.  Create the jar file by executing:

            ``` example
            jar cmf <manifest file> JarFileName.jar *.class
            ```

        4.  Run the jar file:

            ``` example
            java -jar JarFileName.jar
            ```

Developing tools
----------------

Java programs are normally developed with an IDE, i.e., Integrated
Developing Environment. Here are the most commonly used IDEs:

-   Intellij IDEA
-   Eclipse
-   NetBeans

You can also use plain text editors such as Emacs or Vim. After all,
codes are just plain texts!
