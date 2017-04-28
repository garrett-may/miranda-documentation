# The Miranda Standard Environment

## Values

`pi :: num`
> The ratio of the circumference to its diameter

`e :: num`
> Transcendental number, the base of natural logarithms.

`tinynum :: num`
> The smallest positive fractional number that can  be distinguished from zero in this implementation (should be around 1e-324 for IEEE standard 64 bit floating point)

`hugenum :: num`
> The largest  fractional  number  that  can  exist  in  this implementation (should be around 1e308 for IEEE standard 64 bit floating
point, will be around 1e38 for the VAX)

`undef :: *`
> Representation of the completely undefined value

## Basic functions

`hd :: [*]->*`
> Returns the first element of a list

> Argument must not be an empty list

`tl :: [*]->[*]`
> Returns the list without the first element

> e.g. `tl "snow"` is `"now"`

`last :: [*]->*`
> Returns the last element of a list

> Argument must not be an empty list

`init :: [*]->[*]`
> Returns the list without its last element

> e.g. `init [1,2,3,4]` is `[1,2,3]`

`member :: [*]->*->bool`
> Checks whether an element is in a list

`neg :: num->num`
> Applies `-` operator onto an element

`subtract :: num->num->num`
> Subtract function representing infix `-`

`or :: [bool]->bool`
> Logical disjunction of a list of bools

`and :: [bool]->bool`
> Logical conjunction of a list of bools

`max :: [*]->*`
> Returns the maximum value out of a list

> e.g. `max [1,2,12,-6,5]` is `12`
> e.g. `max "hippopotamus"` is `'u'`

`min :: [*]->*`
> Returns the minimum value out of a list

`max2 :: *->*->*`
> Returns the maximum value out of the two arguments

`min2 :: *->*->*`
> Returns the minimum value out of the two arguments

`fst :: (*,**)->*`
> Returns the first component of a pair

`snd :: (*->**)->**`
> Returns the second component of a pair

`postfix :: *->[*]->[*]`
> Appends an element to a list

### Extra functions

`reverse :: [*]->[*]`
> Reverses a list

> Argument must be finite

`merge :: [*]->[*]->[*]`
> Merges two sorted list

> Returns a sorted list

`sort :: [*]->[*]`
> Sorts a list into ascending order

> Uses mergesort for sorting

> e.g. `sort "hippopotamus"` is `"ahimoopppstu"`

`take :: num->[*]->[*]`
> Takes the first x elements from a list, and returns the taken list

> Returns the original list if the original list has length less than x

> e.g. `take 2 [1,2,3,4] = [1,2]`

`drop :: num->[*]->[*]`
> Drops the first x element from a list, and returns the rest of the list

> Returns the empty list if the original list has length less than x

> e.g. `drop 2 [1,2,3,4]` is `[3,4]`

`rep :: num->*->[*]`
> Replicates an element x times

> Returns a list

> e.g. `rep 6 'o'` is `"oooooo"`

`repeat :: *->[*]`
> Repeats an element an infinite number

> Returns an infinite list

`mkset :: [*]->[*]`
> Strips a list of duplicate values (thus, it makes a set from it)

`limit :: [*]->*`
> Returns the first value in a list which is the same as its successor

> Useful in testing for convergence

> e.g. the following Miranda expression computes the square root of 2 by the Newton-Raphson method `limit [x | x<-1, 0.5*(x + 2/x).. ]`

`index :: [*]->[num]`
> Returns the list of subscript values of a list

> e.g. `index "hippopotamus"` is `[0,1,2,3,4,5,6,7,8,9,10,11]`

`concat :: [[*]]->[*]`
> Concatenates the elements of a list of lists into one single list

> e.g. `concat [[1,2],[],[3,4]]` is `[1,2,3,4]`

`zip2 :: [*]->[**]->[(*,**)]`
> Zips two lists together, by tupling the elements with the same index

> Produces a list of 2-tuples

> If different-length lists are used, `zip2` will only tuple upto the shortest length

> e.g. `zip2 [0..3] "type"` is `[(0,'t'),(1,'y'),(2,'p'),(3,'e')]`

`zip3 :: [*]->[**]->[***]->[(*,**,***)]`
> Zips three lists; produces a list of 3-tuples

`zip4 :: [*]->[**]->[***]->[****]->[(*,**,***,****)]`
> Zips four lists; produces a list of 4-tuples

`zip5 :: [*]->[**]->[***]->[****]->[*****]->[(*,**,***,****,*****)]`
> Zips 5 lists; produces a list of 5-tuples

`zip6 :: [*]->[**]->[***]->[****]->[*****]->[******]->[(*,**,***,****,*****,******)]`
> Zips 6 lists; produces a list of 6-tuples

`transpose :: [[*]]->[[*]]`
> Transposes a matrix represented as a list of lists

## Higher Order functions

`map :: (*->**)->[*]->[**]`
> Applies a function to each element in a list

> Returns a list of each mapped element

`map2 :: (*->**->***)->[*]->[**]->[***]`
> Applies a function to each element of the first list and the second list

> Returns a list of each mapped element

`filter :: (*->bool)->[*]->[*]`
> Returns a list of elements where each element satisfies the predicate

> e.g. `filter (>5) [3,7,2,8,1,17]` is `[7,8,17]`

`takewhile :: (*->bool)->[*]->[*]`
> Takes elements from a list whilst the predicate is satisfied, and returns the taken list

> e.g. `takewhile digit "123gone"` is `"123"`

`dropwhile :: (*->bool)->[*]->[*]`
> Drops elements from a list whilst the predicate is satisfied, and returns the rest of the list

> e.g. `dropwhile digit "123gone"` is `"gone"`

`foldr :: (*->**->**)->**->[*]->**`
> Folds a list using a binary operator, right associatively

> e.g. `foldr op r [a,b,c]` is `a $op (b $op (c $op r))`

`foldl :: (*->**->*)->*->[**]->*`
> Folds a list using a binary operator, left associatively

> e.g `foldl op r [a,b,c]` is `(((r $op a) $op b) $op c)`

`foldl1 :: (*->*->*)->[*]->*`
> Applies `foldl` over non-empty lists

> Argument must not be an empty list

`foldr1 :: (*->*->*)->[*]->*`
> Applies `foldr` over non-empty lists.

> Argument must not be an empty list

`scan :: (*->**->*)->*->[**]->[*]`
> Applies `foldl` to every segment of a list

> e.g. `scan (+) 0 [1,2,3,4,5]` is `[0,1,3,6,10,15]`

`iterate :: (*->*)->*->[*]`
> `iterate f x` returns the infinite list `[x, f x, f(f x), ... ]`

> e.g. `iterate (2*) 1` yields a list of the powers of 2

`until :: (*->bool)->(*->*)->*->*`
> Continues to apply a function to an element until the predicate has been satisfied

> e.g. `until (>1000) (2*) 1` is `1024`

## Mathematical functions

`numval :: [char]->num`
> Converts a number represented as a string into the actual number

`entier :: num->num`
> Floors a number

> e.g. `entier 1.0` is `1`

> e.g. `entier 3.5` is `3`

> e.g. `entier (-3.5)` is `-4`

> Note: the following rule holds: `a div b = entier (a/b)`

> Note: 'entier' is French for 'integer'

`integer :: num->bool`
> Checks to see if a number is an integer (specifically, not fractional)

> e.g. `integer 1` is `True`
> e.g. `integer 1.5` is `False`
> e.g. `integer 1.0` is `False`

`abs :: num->num`
> Absolute value of a number

> e.g. `abs (-3)` is `3`

`sqrt :: num->num`
> Computes the square root of a number

> Returns a fractional number

`exp :: num->num`
> The exponential function

`log :: num->num`
> Returns the natural logarithm of a number

`log10 :: num->num`
> Returns the logarithm in base 10 of a number

`sum :: [num]->num`
> Sums a list of numbers

`product :: [num]->num`
> Returns the product of a list of a numbers

### Trigonometric functions

`sin :: num->num`
> Returns the trigonometric sine of a number

> Argument in radians.

`cos :: num->num`
> Computes the cosine

> Argument in radians

`arctan :: num->num`
> Computes the inverse tangent

> Returns a result in the range `-pi/2` to `pi/2`

## String and Character functions

`letter :: char->bool`
> Checks if a character is a letter

`digit :: char->bool`
> Checks if the character is a digit

`code :: char->num`
> Returns the ASCII code of a character

`decode :: num->char`
> Returns the ASCII character represented by this number

> Argument between 0 and 255

`show :: *->[char]`
> Transforms a type into its string representation

`shownum :: num->[char]`
> Transforms a number into its string representation

`showfloat :: num->num->[char]`
> Transforms a number into its string representation, to x decimal places

> e.g. `showfloat 1 2` is `2.0`
> e.g. `showfloat 0 1.0` is 1

`showscaled :: num->num->[char]`
> Transforms a number into its string representation, in standard form

> e.g. `showscaled 1 20` is `2.0e+01`

`spaces :: num->[char]`
> Returns a list of x many spaces

`ljustify :: num->[char]->[char]`
> Left-justifies a string via a specified width

`rjustify :: num->[char]->[char]`
> Right-justifies a string via a specified width

`cjustify :: num->[char]->[char]`
> Centre-justifies a string via a specified width

`lay :: [[char]]->[char]`
> Concatenates a list of strings together, with each string appended with a newline character
> e.g. `lay ["hello","world"]` would produce
```
hello
world
```

`layn :: [[char]]->[char]`
> Concatenates a list of strings together, with each string prepended with a number and appended with a newline character

> e.g. `layn ["hello","world"]` would produce
```
   1) hello
   2) world
```

`lines :: [char]->[[char]]`
> Takes a string, and splits it by the newline character

> Returns a list of strings

> e.g. `lines "hello world\nit's me,\neric\n"` is `["hello world","it's me","eric"]`

## System functions

`read :: [char]->[char]`
> Returns the contents of a UNIX file

> Throws an error if the file does not exist, or lacks read permission

`filemode :: [char]->[char]`
> Returns the access permissions of the current process of a UNIX file

> Permissions are encoded as: "drwx"

> Any  permission  not  granted  is  replaced  by  a  '-' character

`system :: [char]->([char],[char],num)`
> Executes the string as a UNIX shell command

`getenv :: [char]->[char]`
> Looks up a string in the user's UNIX environment.

> e.g. `getenv  "HOME"` returns the pathname of your home directory

> Uses 'sh'

> Returns a 3-tuple of standard output, error output, and exit status

## Combinators

`id :: *->*`
> The identity function; returns the argument

`const :: *->**->*`
> A combinator for creating constant-valued functions
> e.g. `(const 3)` is the function that always returns `3`

`converse :: (*->**->***)->**->*->***`
> A combinator for inverting the order of arguments of a two-argument function

> e.g. `f a b` is `f b a`


## Miscellaneous functions

`error :: [char]->*`
> Creates an error value with the associated
string message

`force :: *->*`
> Forces a check that the element is defined

> e.g. `hd (force x)` returns the `hd x`, but fully evaluates `x` first (so `x` must be finite)

`seq :: *->**->**`
> Checks that the first value is not completely undefined, before returning the second value
