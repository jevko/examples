# Abstract tree

A possible Jevko encoding of an abstract tree structure:

```
Prefix 1 [Suffix 1] 
Prefix 2 [
  Prefix 2.1 [Suffix 2.1] 
  Prefix 2.2 [Suffix 2.2] 
  Suffix 2
]
Prefix 3 [Suffix 3]
Suffix
```

example part which matches the `Subjevko` rule:

```
Prefix 1 [Suffix 1] 
```

example part which matches the `Prefix` (`Text`) rule:

```

  Prefix 2.1 
```

Note: all whitespace characters are matched by the rule.

example part which matches the `Suffix` (`Text`) rule:

```
Suffix 3
```

The tree may be visualized like this:

```

         Prefix 1
    +----------------(Suffix 1)
    | 
    |
    |                     Prefix 2.1
    |                +------------------(Suffix 2.1) 
    |                |
    |                |
    |    Prefix 2    |    Prefix 2.2
----+----------------+------------------(Suffix 2.2) 
    |                |
    |                |
    |                |
    |                +----(Suffix 2)
    |
    |
    |    Prefix 3
    +----------------(Suffix 3)
    |
    |
    |
    +----(Suffix)
    
```

or like this:

```

               Prefix 1
      +--------------------(Suffix 1)
      | 
      |
      |                             Prefix 2.1
      |                        +------------------(Suffix 2.1) 
      |                        |
      |                        |
      |        Prefix 2        |
---(Suffix)----------------(Suffix 2)
      |                        |
      |                        |
      |                        |    Prefix 2.2
      |                        +------------------(Suffix 2.2) 
      |
      |
      |        Prefix 3
      +--------------------(Suffix 3)
    
```

