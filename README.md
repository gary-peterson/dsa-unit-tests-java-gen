

# Running Unit Tests

Time constraints may prevent us from writing test code.

This git includes generalized test code for Java projects. It is generalized using interfaces and a simple factory approach.

## Running From Script (for Windows) - MAC and Unix are below

Note: First verify (and install if needed) a Java JDK. [Here are steps...](https://objectcoding.com/Books/XdocRoot/Intro/I/103InstallingJava/103InstallingJava.html?20112813203)

1. Download archive (e.g. DSA-Linked-List.zip or DSA-Dynamic-Array.zip, etc)
2. Extract to local machine
3. Copy your implementation package(s) to the "src" directory
    - for linked list, you would copy your "linkedlist" package (dir) into "src"
    - for dynamic array, you would copy your "dynarray" package (dir) into "src" 
    - and similar for others
4. Copy your factory JAVA file into public package directory (e.g. "linearpub")
5. Run "compile.bat" (e.g., double click to run)
6. NOTE -- windows safeguards archive files, so you will likely get "windows security error". You can safely click "More Info" and then "Run Anyway".
7. Run "unit-tests-UI.bat" (double click to run)
8. The "Unit Test Window" opens
9. See "Using Unit Tests UI" below

Or run "unit-tests-z-console.bat" for headless (console) output

## Running From Script (for MAC or unix)

Note: First verify (and install if needed) a Java JDK. [Here are steps...](https://objectcoding.com/Books/XdocRoot/Intro/I/103InstallingJava/103InstallingJava.html?20112813203)

1. Download archive (e.g. DSA-Linked-List.zip or DSA-Dynamic-Array.zip, etc)
2. Extract to local machine
3. We will call the extracted root directory "root" in these steps
4. In root, **delete** the three BAT (.bat) files.
5. Copy the three SH (.sh) files from the MAC-UNIX directory into the root (e.g., we are replacing the BAT files with the SH files)
6. Copy your implementation package(s) to the "src" directory
    - for linked list, you would copy your "linkedlist" package (dir) into "src"
    - for dynamic array, you would copy your "dynarray" package (dir) into "src" 
    - and similar for others
7. Copy your factory JAVA file into public package directory (e.g. "linearpub")
8. Open the MAC terminal window or unix console
9. Navigate to the root directory (in the terminal)
10. Type and run the command **sh compile.sh**
11. Type and run the command **sh unit-tests-UI.sh**
12. The "Unit Test Window" opens
13. See "Using Unit Tests UI" below

Or, to have headless output (console only - no UI), run **unit-tests-z-console.sh** after compiling.

## Running In IDE

Note: example here is Eclipse -- other IDE's should be similar

This applies to any archive with name ending in "-For-IDE".

1. Download archive and extract root directory
2. You will have probably two subdirectories
	in the root. Each of these is a separate project
    - File - Open Projects from File System
      - Choose full path to the first sub-directory
    - Repeat for the other subdirectory(s)
    - Note that you may have already loaded a project (like Scorer) with a previous archive in which case you can ignore or update
3. Find new project in IDE
4. Copy your package(s) into "src" directory
5. Copy your factory into "linearpub" package/directory
6. Find class "_UnitTestLauncher.java"
7. Run it
8. See "Using Unit Tests UI" below
9. You can also find and run "_UnitTestManager.java" for console output

Note: You should be using **JavaSE-11 or later**

## Using Unit Tests UI

The simple unit test window has three areas:

	-----------------------
	| Test Cases | Tests |
	-----------------------
	|        Output      |
	-----------------------

1. Select a test case(s) and optionally tests
2. And click "Run"
3. The trick is to isolate any tests that are failing (listed in output)
4. Simply selecting the failing test case and test and run again.
5. Browse the test code using the test case class and test name which identifies a test method.
  e.g. for:
      "test_isEmpty -- FAILED"
  the test method would be "test_isEmpty" (in the identified test case class)
  
## Coding - Factory

We need to tell the unit test framework how to construct an instance of our subject class.

We do that in a factory.

For our example, let us say we have a LinkedListFactory. All we would need to do is insert our class name in the method shown below.

~~~
	public static <T> DynamicList<T> newList() {
		//return new empty LinkedList
		return new **LinkedList**<>();
	}
~~~

## Coding - Interface

We need to comply to a protocol that the unit tests understand.

We do that with Java interface(s).

For our example, let us say we have a DynamicList interface. For our linked list example, we would implement the interface in the usual way:

~~~
	public class LinkedList<E> implements DynamicList<E>
~~~

## What if My Protocol Is Different?

This is easy to solve with Java interfaces.

Using our linked list example, let us say that the interface declares a method "first", but your class implements "firstElement".

We would simply add an "alias method":

~~~
public E first() {
	return this.firstElement();
}
~~~

The idea is simply to **comply** with the interface.

Once the interface is done, the unit tests, have their needed protocol in place, and we are off and running with unit testing.
