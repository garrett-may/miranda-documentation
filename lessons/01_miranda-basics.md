## Miranda Basics

Miranda is a functional language; this means that it works on taking 'some of this data' and producing 'some of that data'. The language places focus on _implementation_, rather than _efficiency_, as, much like other functional languages, it believes that the efficiency of the program can be improved after one has created the functionality (or at least understood how it should work).

Miranda scripts have the `.m` file extension, and, when compiled, will produce a `.x` compiled file. Compiling a Miranda script is automatically done after running the command:

`mira <filename>.m`

This attempts to compile the file and, if successful, will open the Miranda interpreter (so that you can test your code). If the compilation fails and errors occur, Miranda will open the Miranda interpreter and display the errors, _to the best of its ability_. Note that the errors outputted may bizarrely appear to not refer to the actual problem; this is likely to how the Miranda compiler is built.

### Comments

Comments are written in Miranda using two pipes/lines:

`|| This is a single-line Miranda comment`

Miranda only supports single line comments; it has no option for multi-line comments.

### "Hello, World!" program

The simple way of writing the "Hello, World!" program in Miranda is simply by creating a single value assigned with the string:

```
hello_world :: [char]
hello_world = "Hello, World!"
```

Then, in the Miranda interpreter:

```
Miranda> hello_world
Hello, World!
```

The program can be simplified to one line, since Miranda can calculate the type:

```
hello_world = "Hello, World!"
```

Or even simpler, by inputting it directly into the interpreter:

```
Miranda> "Hello, World!"
Hello, World!
```
