## Types

### Basic Types

Miranda has several pre-built types which makes up the basics of a type system:

 - `num`: This is the numeric type. It represents all numbers, including both integers and decimals (note: this is simply one object to hold any int, float, double, long, etc.).
   - Declared: Using digits; period symbol for decimal point
   - Examples:
    - `0`
    - `-2`
    - `3.14159`
 - `char`: This is the character type. It represents any single character.
   - Declared: Single character inside two single quotes
   - Examples:
    - `'a'`
    - `'>'`
    - `'!'`
 - `bool`: This is the boolean type, which is either true or false. This is most often used in conditions.
  - Declared: Using either the word 'True' for true, or the word 'False' for false, without single quotes
   - Examples:
    - `True`
    - `False`

### Lists

Miranda also provides a way of representing lists of elements:

 - `[num]`: A list of numbers
   - Declared: Square brackets surrounding comma-separated numbers
   - Examples:
    - `[0, 1, 2, 3, 4]`
    - `[3.14159, 3.2, 9]`
    - `[4000]`
 - `[char]`: A list of characters. Also known as a string (as it's a "string of characters").
   - Declared: Square brackets surrounding comma-separated characters. Also can be declared using characters inside two double-quotes
   - Examples:
    - `['a', 'b', 'd', 'f', 'x']`
    - `"Lorem Ipsum"`
    - `['g']`
    - `"g"`
 - `[bool]`: A list of booleans
   - Declared: Square brackets surrounding comma-separated booleans
   - Examples:
      - `[True]`
      - `[True, False]`
      - `[False, True]`
      - `[False, False, False, False, False, False, True]`

### "Hello, World!"

Going back to our "Hello, World!" program, we can see that the type of it was a list of char i.e. a string:

```
hello_world :: [char]
hello_world = "Hello, World!"
```
