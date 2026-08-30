# Assignment 3: Integer Stack

## Description

In this assignment, you will design, implement, and thoroughly test an integer Stack in C++.

This is the first substantial programming assignment in the course. You are now expected to apply the development process introduced in Assignment 2 more independently. You will decide how to divide the work into meaningful development stages, when to test, and when a coherent change is ready to commit.

The Stack itself is intentionally simple. The larger purpose of the assignment is to begin developing software as a collection of well-defined components with clear interfaces, private state, separate implementation, systematic testing, and meaningful development history.

The primary concepts in this assignment are:

- Abstract Data Types (ADTs);
- classes and objects;
- object state;
- stack behavior and Last-In-First-Out (LIFO) ordering;
- interface versus implementation;
- header and source file organization;
- encapsulation;
- overflow and underflow;
- systematic testing;
- incremental software development with Git; and
- responsible use of generative AI.

## Learning Objectives

By completing this assignment, you should be able to:

- explain the behavior of a Stack ADT;
- implement `push`, `pop`, `peek`, and `isEmpty`;
- maintain the internal state of an object correctly;
- separate a class interface from its implementation;
- use public and private members appropriately;
- compile and link a multi-file C++ program;
- reason about overflow and underflow;
- test a stateful object systematically;
- use generative AI while independently understanding and verifying the resulting work;
- develop software incrementally using meaningful Git commits; and
- document a small software project professionally.

## Background

Before beginning this assignment, you should have:

- completed **Assignment 2: First Code**;
- completed the material on intermediate programming, ADTs, and OOP;
- completed the material on interface versus implementation, header files, and loose coupling;
- completed the material on stacks;
- completed the testing lecture and reviewed the [Testing Guidelines](https://katrompas.accprofessors.com/testing);
- watched **[Using AI Effectively](https://youtu.be/CHhfy3fAMaA)**;
- a working Ubuntu development environment;
- Git and GitHub configured and working; and
- completed the Classroom 50 workflow used in Assignment 2.

If your C++ OOP background is weak or rusty, optional OOP review material is available in the Notes folder, and videos are available in Panopto.

Assignment 2 demonstrated the development and submission workflow in detail. **This assignment will not repeat those instructions step by step.** You are responsible for applying that process independently.

## Starter Repository

Your repository initially contains:

```text
ASSIGNMENT.md
ESSAY.md
.gitignore
main.cpp
main.h
stack.cpp
stack.h
```

A `README.md` is intentionally **not** included. **You must [create one](https://katrompas.accprofessors.com/readme-guidelines) as part of the assignment.**

Do not replace the supplied project structure.

The Stack class has already been started for you. Its internal representation is fixed:

```cpp
#define SIZE 10

class Stack {

public:

    Stack();

    // required public Stack methods belong here

private:

    int stack[SIZE];
    int top;

};
```

The supplied attributes are the only attributes allowed.

Do not:

- change the value of `SIZE`;
- change the supplied attributes;
- remove either attribute; or
- add additional attributes.

Part of the assignment is determining how the required Stack operations belong in the public interface and implementing those operations in `stack.cpp`.

## Stack Requirements

Implement a fixed-size Stack that stores integers.

The Stack must follow Last-In-First-Out (**LIFO**) behavior.

The public interface must provide the following operations:

```cpp
Stack();
bool push(int);
bool pop(int&);
bool peek(int&);
bool isEmpty();
```

Use these method names, return types, and parameter types exactly.

Do not add parameter names to function declarations in the header file.

### Constructor

The constructor must initialize a newly created Stack to the empty state.

For the supplied representation, an empty Stack is represented by:

```text
top = -1;
```

### `push`

`push` attempts to place an integer on top of the Stack.

If space is available:

- add the value to the top of the Stack;
- update the Stack state correctly; and
- return `true`.

If the Stack is full:

- do not modify the Stack; and
- return `false`.

Attempting to push onto a full Stack is **overflow**.

### `pop`

`pop` attempts to remove the value currently on top of the Stack.

If the Stack is not empty:

- provide the removed integer through the reference parameter;
- update the Stack state correctly; and
- return `true`.

If the Stack is empty:

- do not modify the Stack; and
- return `false`.

Attempting to pop from an empty Stack is **underflow**.

### `peek`

`peek` examines the value currently on top of the Stack without removing it.

If the Stack is not empty:

- provide the top integer through the reference parameter;
- leave the Stack unchanged; and
- return `true`.

If the Stack is empty:

- do not modify the Stack; and
- return `false`.

### `isEmpty`

`isEmpty` returns:

- `true` when the Stack contains no items; and
- `false` otherwise.

**Remember:** The algorithms may conceptually return `true` or `false` at different points, but your implementation must contain **one and only one `return` statement**. All functions and methods in this course use [single-entry, single-exit structure](https://katrompas.accprofessors.com/best-practice-procedural-programming).

## File and Module Requirements

This course uses a deliberately strict interface/implementation convention.

Professional C++ development may make more nuanced decisions about which dependencies belong in a header and which belong only in an implementation file. In this course, the convention is intentionally stricter so that the separation between modules and their interfaces remains explicit and consistent.

For this course:

- every `.cpp` file has a corresponding `.h` file;
- declarations belong in header files;
- definitions belong in source files;
- directives, constants, and includes used by a module belong in its header file;
- a `.cpp` file includes its own header file; and
- each module must explicitly include what it requires rather than depending on another file to include something indirectly.

Follow this convention throughout the course unless an assignment explicitly states otherwise.

For this project:

```text
stack.h      Stack interface and object-state declarations
stack.cpp    Stack method implementations
main.h       directives required by main.cpp
main.cpp     testing
```

Do not place the Stack method implementations in `stack.h`.

Do not place the Stack class declaration in `main.cpp` or `main.h`.

## Programming Constraints

Keep the implementation simple and within the scope of the course material.

Do not use:

- `std::stack`;
- `std::vector`;
- another container as the Stack implementation;
- dynamic memory;
- exception handling;
- additional classes; or
- additional Stack attributes.

The supplied integer array and `top` attribute are the Stack implementation for this assignment.

All functions and methods that return a value must use a single-entry, single-exit structure and contain **one and only one `return` statement**. See the [section on modularity](https://katrompas.accprofessors.com/best-practice-procedural-programming) for additional explanation.

Generative AI may suggest techniques that are more advanced or more complicated than necessary. **Do not use a technique simply because AI generated it.**

You are responsible for understanding every part of the submitted program.

## Testing

Testing is a major part of this assignment.

Use the [testing lecture](https://www.youtube.com/watch?v=qk6drZiiXiA) and the course [Testing Guidelines](https://katrompas.accprofessors.com/testing) as your guide.

Your testing must thoroughly exercise the Stack rather than merely demonstrate that a few convenient calls work.

Think about:

- the important states a Stack can occupy;
- transitions between those states;
- normal operations;
- boundary conditions;
- overflow;
- underflow;
- whether LIFO behavior is preserved;
- whether `peek` changes the Stack;
- sequences of operations rather than isolated method calls; and
- how you can gain confidence that the object continues to behave correctly over many operations.

Use systematic testing and randomized testing where appropriate.

For this assignment, **do not modularize the testing code**.

All testing should be written as **one continuous test script** inside `main()`.

This is deliberate. The immediate objective is to learn how to test an object thoroughly. The organization and modularization of test code will be addressed in a later assignment.

**There is no behavioral autograding for this assignment.** Designing and performing sufficient testing is part of the assignment. You are responsible for establishing that your Stack behaves correctly.

## Development Process

Develop the project incrementally.

Do **not** write the complete Stack and complete test script first and then commit the finished assignment.

Your Git history is part of the submitted work and should show the program developing through meaningful stages.

Your repository must contain **at least ten meaningful student-created program-development commits**.

You are responsible for:

- deciding how to decompose the work;
- determining appropriate commit boundaries;
- writing descriptive commit messages;
- compiling and testing before committing;
- pushing your work regularly.

A meaningful commit represents a coherent change in the development of the software.

Arbitrary partial changes made only to increase the number of commits are not meaningful.

Changes made only to:

- `README.md`;
- `ESSAY.md`; or
- `.gitignore`

do **not** count toward the minimum number of program-development commits.

Use the course [Commit Guidelines](https://katrompas.accprofessors.com/committing).

## Generative AI

Use of generative AI is required as part of the development process.

You may give your AI assistant this complete assignment and use it as a:

- tutor;
- programming partner;
- critic;
- debugging assistant;
- testing assistant; or
- source of explanations.

AI may help you write code, but producing code is not the primary objective. Use AI to help you reason about the software you are building.

Useful activities include:

- asking AI to explain Stack behavior;
- asking questions about an unfamiliar C++ construct;
- discussing interface decisions;
- asking AI to identify possible boundary cases;
- developing a testing strategy;
- asking AI to inspect code for assumptions or defects;
- comparing possible solutions;
- interpreting compiler errors; and
- challenging an AI explanation or recommendation.

You remain responsible for:

- understanding all submitted code;
- understanding how the Stack maintains its state;
- knowing why each public method behaves as it does;
- testing AI-generated or AI-suggested code;
- verifying that the implementation follows the assignment requirements;
- rejecting unnecessary or out-of-scope techniques; and
- making the final engineering decisions.

AI output is not authoritative. A suggestion that compiles or appears plausible may still be incorrect, unnecessarily complicated, or inconsistent with the assignment.

Your use, evaluation, and verification of AI are documented in `ESSAY.md`.

## `ESSAY.md`

Complete the supplied `ESSAY.md`.

The questions ask you to discuss:

- how you used generative AI;
- something AI helped you understand;
- the integer-stack underflow problem;
- how you tested and verified your Stack; and
- a situation in which you questioned, tested, compared, corrected, or otherwise evaluated an AI suggestion.

This is not a formal essay.

Concise answers are appropriate, but they must be specific and substantive enough to demonstrate your understanding and your actual development process.

Do not merely list prompts or say that AI "helped with the code."

Your responses should demonstrate that you remained intellectually involved in the work: understanding, questioning, testing, verifying, and making decisions.

Answer every question in your own words.

## Code Documentation

All source and header files must follow the course [Commenting Guidelines](https://katrompas.accprofessors.com/commenting).

Complete the required:

- file header comments;
- function and method documentation; and
- header-file documentation.

Follow the supplied course examples and formatting requirements.

Before submission, remove:

- instructional placeholder comments;
- debugging statements;
- commented-out code;
- temporary code; and
- unnecessary comments.

## `README.md`

A `README.md` is intentionally not supplied.

Create one in the root of your repository and complete it according to the course [README Guidelines](https://katrompas.accprofessors.com/readme-guidelines).

The README should document the software you actually submitted.

All Markdown files must be properly formatted and professional. Spelling, grammar, and writing quality count.

## `.gitignore`

Complete the supplied `.gitignore` according to the instructions in the file and [the course guidelines](https://katrompas.accprofessors.com/gitignore-guidelines).

Use generative AI as appropriate to help identify generated files and other artifacts that should not be committed to a C++ project.

Your compiled executable must not be committed to the repository.

## Building and Running

Compile the complete project from the terminal:

```bash
g++ main.cpp stack.cpp -o stack
```

Run it with:

```bash
./stack
```

You are responsible for resolving compiler errors and verifying that the complete project builds successfully.

## Final Review and Submission

Before submitting the assignment, verify the complete repository.

### 1. Build the program

Compile the complete project:

```bash
g++ main.cpp stack.cpp -o stack
```

The project must compile successfully.

### 2. Run your complete test script

```bash
./stack
```

Review the results and make sure your testing demonstrates correct Stack behavior.

### 3. Check repository status

Run:

```bash
git status
```

Your working tree should be clean.

### 4. Review development history

Run:

```bash
git log --oneline
```

Verify that the repository contains at least **ten** meaningful program-development commits and that the history demonstrates incremental development.

### 5. Review GitHub

Open the repository on GitHub and confirm that:

- the final source and header files are present;
- `README.md` has been created and completed;
- `ESSAY.md` has been completed;
- `.gitignore` has been completed;
- no compiled executable or other unwanted generated files are tracked; and
- all final changes have been pushed.

### 6. Submit through Blackboard

Copy the normal HTTPS URL for your GitHub repository and submit that URL in the Blackboard assignment.