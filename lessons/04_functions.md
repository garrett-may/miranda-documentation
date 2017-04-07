## Functions

Functions in Miranda are a way of manipulating data. Much like values, they do not require their type, but writing it is often helpful.

To declare a function, the name of the function is written along with `::` before the type signature of the function is declared.

The definitions of the function are then written below it.

```
secondsInAMinute = 60
minutesInAnHour = 60
hoursInADay = 24
secondsInADay = secondsInAMinute * minutesInAnHour * hoursInADay

|| Function to convert seconds to days
convertSecondsToDays :: num->num
convertSecondsToDays seconds = seconds / secondsInADay
```

You'll notice that the type signature for the function is `num->num`. This function takes one `num` as a paramter and outputs one `num`.

To declare multiple paramters, more arrows are used:

```
|| Function to add two numbers together
plus :: num->num->num
plus a b = a + b
```

The type signature here is `num->num->num`, and has two `num` paramters, and returns a `num`. This works due to a concept called _currying_, which we will look at later.

You'll also notice that, unlike in some other language, the type signature only contains the types, and not the names of the parameters. The names appear in the next line, as `seconds`, or `a` and `b`. Their type is not required, as Miranda will infer the type of each parameter by using the type signature, and the order of the types and parameters.

```
|| Function to add two numbers together
plus :: num->num->num
plus a b = a + b    || Miranda knows that a is of type num, and b is of type num
```

To call the function, simply write the name of the function and then each parameter:

```
Miranda> plus 2 3
5
```
