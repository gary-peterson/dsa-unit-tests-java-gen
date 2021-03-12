

# Running Unit Tests

Time constraints may prevent us from writing test code.

This git includes generalized test code for Java projects. It is generalized using interfaces and a simple factory approach.

We will use "linked list" **for example purposes**.

## Running From Script

1. Download archive and extract all directories (e.g. "DSA-Linked-List.zip")
2. See "MAC-UNIX" directory (if applicable)
3. Copy your package(s) into "src" directory
4. Copy your factory into approprite package directory (e.g. "linearpub")
5. Run "compile.bat"
6. Run "unit-tests-UI.bat"
7. Unit Test window opens
8. See "Using Unit Tests UI" below

Or run "unit-tests-z-console.bat" for headless (console) output

## Running In IDE

Note: example here is Eclipse -- other IDE's should be similar

1. Download archive and extract all directories (e.g. "DSA-Linked-List-Source.zip")
2. Import two extracted projects
  - File - Open Projects from File System
    - Choose full path to "Scorer" directory
  - File - Open Projects from File System
    - Choose full path to "Linked-List" directory
3. Find new project in IDE
4. Copy your package(s) into "src" directory
5. Copy your factory into "linearpub" package/directory
6. Find class "_UnitTestLauncher.java"
7. Run it
8. See "Using Unit Tests UI" below

Note: You should be using **JavaSE-11 or later**

## Using Unit Tests UI

The window has three panes:

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
  	"subList -- FAILED"
  the test method would be "test_subList"

