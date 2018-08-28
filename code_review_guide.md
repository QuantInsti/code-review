# Guide to Code Review

This is a guide/ checklist for generic code review. The guidelines are divided 
in to different sections for easy reference. These are guidelines, meaning 
exceptions are allowed, except otherwise mentioned.

### Functionality and implementation
+ code implements the logic and flow in a simple and readable manner
+ when required, the code includes **unit test** cases
+ try to cast your problem statement in to accepted design patterns
+ if the code is not a minor bug-fix or feature additions, the implementation
logic should be discussed with other team members before coding
+ all repeated code should be factored out in functions
+ There is no commented out code block
+ There is no dead code block (i.e. run time execution will never reach that
block)
+ data structures are precise, and whenever possible, use built-in types
+ no code blocks that can be replaced by common library functions
+ loops are replaced with **vectorized** operations if possible
+ block of codes inside loops are minimized or factored out in functions
+ all loops terminate with clearly identified conditions
+ check for race conditions **whenever accessing any resource** and resolve
such race conditions within the code itself
+ use proper exception handling **whenever accessing any resource**

### Variables and functions and classes
+ all variables should be in the **lowest possible scope**
+ minimize global variables, ensure all variables are **initialized** 
+ do not use logical comparison on unsupported types. Cast floating points to
int before equality checks
+ functions should be self-contained and [**without side-effects**](https://en.wikipedia.org/wiki/Side_effect_(computer_science)) as much as 
possible. For functions with side effects, they either should be common (like
a file I/O operation) or clearly identifiable
+ funtions should not return None or Null - exceptions allowed
+ no print statements in final code version
+ all types of collections are checked for bounds (i.e. out of bounds access).
Also all collections are initialized with lowest estimated size
+ anonymous functions are either one-liner, or used inside a closure which is
not global in scope
+ return **early** from functions/ method before implementing the logic for 
valid inputs, scenarios etc.
+ whenever possible use **composition** than inheritence to implement 
polymorphism
+ always stick to the [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter)
+ always follow Do not Repeat Yourself (DRY) principle for class design
+ always stick to the [S.O.L.I.D.](https://en.wikipedia.org/wiki/SOLID) principles for class design

### Documentations, debugging and logging
+ required logs are present
+ debug codes, if present, are clearly identified
+ do not catch all exceptions in a generic single line
+ catch expressions are fine-grained to capture specific exception
+ exceptions, once caught are re-raised, unless it is intended by design
+ all variable and function names should capture their purpose if possible
+ all significantly large functions should have proper in-line documentation
+ all public APIs, methods etc. are properly documented
+ edge cases found during code review, if any, are included in the doc until
a better version is implemented

### Resource handling
+ all file descriptors, sockets, database cursors are released and destroyed
when no longer needed
+ all file descriptors, sockets, database cursors are released and destroyed
when caught in exceptions
+ use context managers 
+ all non-local scope variables are destroyed when no longer needed
+ if the programming language does not support automatic garbage collection, 
make sure you are doing proper clean-up
+ use **context managers** whenever accessing any OS resource
+ separate functionalities that do computation from those who co-ordiantes 
(e.g. threading, queueing etc.)

### Security and performance
+ always do input validation **for all public APIs**
+ add **API rate limiting** for all public APIs
+ check for sand-boxing and ensure for sensetive codes, some code is 
responsible for checking which users can run this and in which capacity
+ for functions/ scripts using more than a threshold time/ resource, take a
profile and document future performance improvement scopes
+ always check for scalability. If this piece of code runs million instance in
parallel, will it break?
+ check stack trace generated in exceptions and if it contains sensitive 
information

### Coding styles
+ for python styles, refer [this](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)
+ for javascripts, refere [here](https://google.github.io/styleguide/jsguide.html)
+ for shell scripts, refer [here](https://google.github.io/styleguide/shell.xml)
+ for HTML/ CSS, refer [here](https://google.github.io/styleguide/htmlcssguide.html)
+ for R, refer [here](http://adv-r.had.co.nz/Style.html)
+ for python, try and use the future package to make the code version 
independent as much as possible





