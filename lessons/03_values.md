## Values

A (global) value can be declared and assigned in Miranda with very simple syntax:

```
hello_world = "Hello, World!"
```

They do not require the type to be declared, as Miranda can infer the type. However, declaring the type is often a useful convenience:

```
hello_world :: [char]
hello_world = "Hello, World!"
```

Values are immutable, meaning that, once they have been assigned, they cannot be reassigned:

```
hello_world :: [char]
hello_world = "Hello, World!"
hello_world = "Bello, World!"     || Error: hello_world is immutable
```

Values are often used to as constants, in order to simplify the code:

```
secondsInAMinute = 60
minutesInAnHour = 60
hoursInADay = 24
secondsInADay = secondsInAMinute * minutesInAnHour * hoursInADay
```
