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

Let's examine it against the Jevko grammar given below (see [Jevko specifications](https://github.com/jevko/specifications) for a detailed Jevko grammar reference):

```abnf
; start symbol, main rule #1
Jevko = *Subjevko Suffix
; main rule #2, mutually recursive with #1
Subjevko = Prefix Opener Jevko Closer

; delimiters
Delimiter = Opener / Closer / Escaper

Opener  = %x5b ; left square bracket 
Closer  = %x5d ; right square bracket
Escaper = %x60 ; grave accent

; aliases
Suffix = Text
Prefix = Text

; text
Text = *Symbol
Symbol = Digraph / Character
Digraph = Escaper Delimiter
; Character is any code point which is not a Delimiter
Character = %x0-5a / %x5c / %x5e-5f / %x61-10ffff
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

