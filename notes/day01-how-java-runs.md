Day 1 — How Java runs

## In one line
Java compiles to bytecode; the JVM runs it and JIT-compiles hot code.

## Key ideas (in my own words)
The three commands

1. javac compiles source code into bytecode

javac -d out src/main/java/day1/Day1.java
Flag	What it does
-d out	Puts the .class files in out/, creating folders for each package (out/day1/Day1.class)
-cp <path>	Where to find other classes or libraries your code uses
-g	Keeps debug info such as local variable names
-parameters	Keeps method parameter names, which Spring uses
--release 21	Compiles for a specific Java version

2. java starts a JVM and runs a class

java -cp out day1.Day1
Part	What it does
-cp out	The classpath: the folder (or .jar files) where the JVM looks for classes
day1.Day1	The fully qualified class name (package + class), not a file path
-jar app.jar	Runs a packaged jar. This is how Spring Boot apps run in production
-Xms512m -Xmx2g	Starting and maximum heap size. You'll use these in the JVM week
java Day1.java	Shortcut (Java 11+): compiles and runs a single file in one step, which is handy for quick experiments

3. javap disassembles a .class file so you can inspect it

javap -c -cp out day1.Day1
Flag	What it shows
(none)	Just the method signatures
-c	The bytecode instructions in each method
-v	Everything: constant pool, stack size, Java version (major version 65 = Java 21)
-p	Private members too
Try it now (5 min)

Open IntelliJ's terminal in the Backend folder and run:

javac -d out src/main/java/day1/Day1.java
java -cp out day1.Day1
javap -c -cp out day1.Day1
## Mistakes I made
- Ran `java src/main/java/day1/Day1` → needs class name + classpath: `java -cp out day1.Day1`

## Interview questions + my answers
- JDK vs JRE vs JVM: ...