## Good Practices
### Never Nesting
Invert conditionals and break before main logic.
### Extraction & Modularity
Move code to a new method with a name that explains what it does.
Methods should do one thing and do one thing well. [[Unix Philosophy]]
### Code Duplication
Avoid duplicating code and move it to new methods.
### Meaningful Variable Name
The variable name should describe or at least hint what it's used for.
### Unit Testing
Running test cases to verify code is often necessary.
Sometimes starting with the unit tests first, then the methods makes the tests act as documentation for how the methods should work.
### Regression Testing
Unit tests that check if old features are still working as changes are made.
