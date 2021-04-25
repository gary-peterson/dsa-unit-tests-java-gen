

# Running Unit Tests

Time constraints may prevent us from writing test code.

This git includes generalized test code for Java projects. It is generalized using interfaces and a simple factory approach.

First [verify (and install if needed)](https://objectcoding.com/Books/XdocRoot/Intro/I/103InstallingJava/103InstallingJava.html?20112813203) a Java JDK.

## Hash Table -- Running From Script (for Windows) - MAC and Unix are below

1. Download archive (DSA-Hash-Table.zip)
2. Extract to local machine
3. Copy your implementation files to the "src/hash" directory
4. Note: the "hashpub" package should be okay as-is (no action needed)
5. Run the compile script
6. NOTE -- Windows safeguards archive files, so you will likely get "windows security error". You can safely click "More Info" and then "Run Anyway".
7. Run the "unit-tests" script
8. The "Unit Test Window" opens
9. See "Using Unit Tests UI" below

Or run the "unit-tests-headless" script for headless (console) output

## Running From Script (for MAC or unix)

1. In the test root, replace the three "BAT" fils with the three SH files (located in "MAC-UNIX" subdir)
2. Follow the same steps as listed above for Windows

## To Run Tests In IDE project

	-Add/Import/Reference the following in your IDE PROJECT:

		-/src
		-/test
		-scorerbase.jar
		-support.jar
		
	-Run Either of These:	
	
		-_UnitTestLauncher (it is headfull)
		-_UnitTestManager (it is headless -- i.e. console only)	

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
