# A few examples of how I've been using Jevko

**Jevko tables to replace CSV** (although larger). Column names are at the top level, with alignment/formatting information in the []. The data is all wrapped in it's own []. Spaces between the fields are ignored and allow for simple alignment while reading as ASCII.

```
foo[<]bar[>]baz[>]
[a]   [1.0] [2.0]
[b]   [3.0] [4.0]
```

New lines are ignored, so this is also a valid encoding of the above table.

```
foo[<]bar[>]baz[>][a][1.0][2.0][b][3.0][4.0]
```

The current implementation also does not require that all the headers come before all the fields. So the following is also valid.

```
foo[<][a]bar[>][1.0]baz[>][2.0]
      [d]      [3.0]      [4.0]
```

Or:

```
foo[<]bar[>]baz[>]
[a]   [1.0] [2.0]
[b]   [3.0] [4.0]
                  bam[>]
[c]   [5.0] [6.0]  [7.0]
[d]   [8.0] [9.0] [10.0]
```

Limiting where headers can occur is probably a good idea. But the implementation was simpler without it. You read each text1 [ text2 ], check if text1 is all whitespace, if it's not whitespace append a header with text2 as the format, if it is whitespace, append the field text2. If the number of fields in the buffer is equal to the number of headers, then emit a row.

Generation is trivial as you're just writing out headers, and rows where you quote each field and wrap it in [].

**Mental models**

```
Some example of something [
    corollary [blah blah blah]
    corollary [ho ho ho]
    example [foo]
    example [bar]
    => [https://example.com]
    => [https://wikipedia.com/blah-blah]
]

Another point []

Yet another point []
```

**Generated data in docs**

```
foo
foo
foo

Write out a bunch of markdown like stuff.

bar bar

[title[Some task that has to be done]owner[Person A]by[2023-03-15]
  state[GREEN]
  update[2023-03-01][It's going well. On track to finish.]
  update[2023-03-04][Still good.]
  state[YELLOW]
  update[2023-03-05][We have some problems. Problem x.]

  [task[Some subtask that has to be done]by[2023-03-09]]
  [task[Another subtask]by[2023-03-09]]
]
[title[Some other tasks]owner[Person A]by[2023-03-07]
  state[RED]
  update[2023-03-01][We have a big problem! Oh no!]
  update[2023-03-04][Still a big problem!]
  state[GREEN]
  update[2023-03-05][We're good now. This is more markdown here, so I can use various formatting. Here's a simple ASCII table:
    ``````
           col1  col2  col3
    foo    bar   bar   bar
    foo    bar   bar   bar
    foo    bar   bar   bar
    foo    bar   bar   bar
    ``````
  ]
]

More stuff here using regular markdown.

[title[More tasks sprinkled throughout the doc]…]
```

Take something like this in as the source. Convert it into a clean markdown file. Then use other tools to convert the markdown into docx for printing or email-safe html for mailing out.

**Transcripts**

```
[Alice] blah blah
[Alice] more stuff
[Bob] I agree.
[Alice] No, you're wrong! [Bob] Oh. :-(
[Alice] We should change the topic.

[Carol] I have another topic.
[Bob] What is it?
[Carol] Something awesome. [My thoughts: it was really dumb]
[Bob] That is awesome. [Oh, here we go again.] We should totally do that! [Phew, sarcasm.]
```
