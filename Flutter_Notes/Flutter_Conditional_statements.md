### Using "if" Statements In Lists

The `if` statement is a crucial feature of the Dart language - actually, it's a core feature of pretty much all programming languages.

In addition to what you learned in the previous lecture, in Dart, you may also use `if` inside of lists to conditionally add items to lists:

1. final myList = [
2.   1,
3.   2,
4.   if (condition)
5.     3
6. ];

In this example, the number `3` will only be added to `myList` if `condition` was met (`condition` can be `true` or `false` or a check that yields `true` or `false` - e.g., `day == 'Sunday'`).

Please note that there are **NO curly braces** around the `if` statement body. The `if` statement body also only comprises the next line of code (i.e., you can't have multiple lines of code inside the `if` statement).

You can also specify an `else` case - an alternative value that may be inserted into the list if `condition` is not met:

1. final myList = [
2.   1,
3.   2,
4.   if (condition)
5.     3
6.   else
7.     4
8. ];

Using this feature is optional. Alternatively, you could, for example, also work with a ternary expression:

1. final myList = [
2.   1,
3.   2,
4.   condition ? 3 : 4
5. ];

Especially when inserting more complex values (e.g., a widget with multiple parameters being set) into a more complex list (e.g., a list of widgets passed to a `Column()` or `Row()`), this feature can lead to more readable code.

---
### if Statements & Comparison Operators

When using `**if**` **statements** - no matter if inside or outside of functions - as well as when using **ternary expressions**, you ultimately must provide a boolean value (`true` / `false`):

1. if (true) {
2.   // do something ...
3. }
4. // or
5. true ? 'this' : 'that'

Of course, hardcoding `true` or `false` into the code makes no sense though - you wouldn't need an `if` statement or ternary expression if a value would always be `true` or always be `false`.

Instead, `true` or `false` is typically derived by comparing values - e.g, comparing a number to an expected value:

1. if (randomNumber == 5) {
2.   // do something
3. }

The `==` operator checks for **value equality** (i.e., the values on the left and right side of the operator must be equal). It **must not be mistaken** with the **assignment operator** (which uses a single equal sign: `=`).

The assignment operator is used to assign values to variables:

1. var userName = 'Max'; // assignment operator used
2. if (userName == 'Max') { ... } // comparison operator used

Besides the equality operator (`==`) Dart also supports many other key comparison operators:

- `!=` to check for **inequality** (`randomNumber != 5` expects `randomNumber` to NOT be `5`, i.e., to be any other value)
    
- `>` to check for the value on the left to be **greater than** the value on the right (`randomNumber > 5` yields `true` if `randomNumber` is greater than `5`)
    
- `>=` to check for the value on the left to be **greater than or equal to** the value on the right (`randomNumber >= 5` yields `true` if `randomNumber` is greater than `5` or equals `5`)
    
- `<` to check for the value on the left to be **smaller than** the value on the right (`randomNumber < 5` yields `true` if `randomNumber` is smaller than `5`)
    
- `<=` to check for the value on the left to be **smaller than or equal to** the value on the right (`randomNumber <= 5` yields `true` if `randomNumber` is smaller than `5` or equals `5`)