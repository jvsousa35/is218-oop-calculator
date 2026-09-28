# OOP Calculator

## Project Overview

This project is a command-line calculator 
built with Python using object-oriented 
programming. The calculator supports addition 
and subtraction while also keeping a history 
of calculations during the current session. 
The project was built in stages so that new 
concepts could be added without having to 
completely redesign the program.

The main concepts used in this project 
include classes, inheritance, abstraction, 
encapsulation, testing, error handling, and 
continuous integration.

## Features

The calculator currently supports:

- Addition
- Subtraction
- Calculation history
- Removing calculations from history
- Help command
- Error handling for invalid inputs
- Testing with pytest
- 100% line and branch coverage
- Automated testing with GitHub Actions

## How to Run the Calculator

Clone the repository and enter the project 
folder.

```bash
git clone 
git@github.com:jvsousa35/is218-oop-calculator.git
cd is218-oop-calculator
```

Install the required dependencies.

```bash
python3 -m pip install -r requirements.txt
```

Run the calculator.

```bash
python3 -m calculator
```

Once the calculator starts, type `help` to 
see the available commands.

## Available Commands

- `add` - Add two numbers
- `subtract` - Subtract the second number 
from the first
- `history` - Show calculations from the 
current session
- `remove` - Remove a calculation from 
history
- `help` - Show the available commands
- `exit` - Exit the calculator

## Running the Tests

To run the complete test suite, use:

```bash
python3 -m pytest
```

The project currently contains 37 passing 
tests and has 100% line and branch coverage.

## Continuous Integration

GitHub Actions is used to automatically test 
the calculator whenever changes are pushed to 
the repository or included in a pull request. 
The workflow tests the project using Python 
3.11, 3.12, 3.13, and 3.14.

This is useful because the project is tested 
in fresh environments instead of only being 
tested on the computer where it was 
developed. It can help identify problems that 
may not appear locally.

## Design Reflection

### Adding Multiplication

If multiplication was added to the 
calculator, I would create a `Multiply` class 
that follows the same `Calculation` contract 
as `Add` and `Subtract`. The class would 
implement `get_result()` and return the 
result of multiplying the two numbers.

The new operation would also need to be 
registered in the operations dictionary in 
the CLI so that the `multiply` command 
creates a `Multiply` object. The help message 
would need to include the new command, and 
tests would need to be added to verify that 
multiplication produces the correct results 
and works through the command-line interface.

The `History` class would not need any 
multiplication-specific logic. History 
already works with objects that follow the 
`Calculation` abstraction. A `Multiply` 
object would still be a calculation, so 
History could store and remove it in the same 
way it handles addition and subtraction. This 
shows one advantage of using a shared 
abstraction instead of making History 
understand every individual operation.

### Email and Text Message Notifications

Email and text-message notification objects 
could share a common contract through a 
`send()` method. For example, both an 
`EmailNotification` and a `TextNotification` 
class could implement the same notification 
interface or abstract class.

The details of sending an email and sending a 
text message would be different, but another 
part of the program could simply call 
`send()` without needing to know how the 
notification is actually delivered. This is 
similar to how the calculator can work with 
different calculation types through a shared 
method such as `get_result()`.

### Transferring the Design to Another 
Language

Many of the design concepts from this project 
could transfer to another programming 
language. Concepts such as separating 
responsibilities, using classes to represent 
different behaviors, creating shared 
contracts, hiding internal data, and writing 
tests are not limited to Python.

However, learning the design concepts does 
not mean that the code would look exactly the 
same in another language. I would still need 
to learn that language's syntax and rules. 
For example, another language may handle 
interfaces, abstract classes, data types, 
exceptions, packages, and program execution 
differently. The overall design ideas can 
transfer, but the way they are implemented 
depends on the language.

## README Usability Review

I reviewed the README as if I were setting up 
the project again on a new computer. One 
instruction that could have been confusing 
was simply saying to run the calculator 
without explaining that the dependencies 
should be installed first.

To make the instructions clearer, the README 
now separates the process into cloning the 
repository, entering the project directory, 
installing the requirements, and then running 
the calculator. This makes the setup order 
easier to follow for someone who has not 
worked with the project before.

## Investigating a Coverage Failure

If the tests passed but the coverage check 
failed, I would first look at the coverage 
report instead of assuming that the 
application was broken. Passing tests mean 
that the existing test cases succeeded, but 
they do not necessarily mean that every 
required line or branch of the program was 
tested.

I would look at the `Missing` column in the 
coverage output to identify which lines were 
not executed. I would then review those parts 
of the program and determine what scenario is 
missing from the tests. After adding a 
meaningful test for that behavior, I would 
run `python3 -m pytest` again and confirm 
that both the tests and the coverage 
requirement pass.

## What I Learned

This project showed how object-oriented 
design can make a program easier to expand. 
Instead of putting all calculator behavior 
into one large function, different 
responsibilities were separated between 
calculations, history, and the command-line 
interface.

It also showed the importance of testing 
beyond checking whether a program works once. 
Unit tests, coverage, and GitHub Actions 
provide different ways to verify that changes 
do not break existing behavior. The biggest 
takeaway is that good program design is not 
only about making the current version work, 
but also making future changes easier to 
manage.







