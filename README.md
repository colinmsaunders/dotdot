# dotdot -- dot dot, a line based markup language

## Principles:

1. universal -- everything can be generated
2. unambiguous -- intent should be obvious -- for both machine and man
3. extensible -- should support unknown use cases
4. friendly -- lastly, should be easy to read & write

dotdot is a utf-8 encoded, line based markup language. 
The first characters in a line denote it's meaning.

    .. dotdot 0.1           identifies version of dotdot
    ... comment             Three or more leading dots is a comment.
    .. foo bar		            Two is a pre-processor directive.
    .. DOT                  Two followed by ALL CAPS is a special char.
    .foo bar		        One sets the attribute foo to bar.

    Normal text.            If a line starts with A-Za-z0-9_, it is normal text.

    This line \ 
    continues.		        Wack newlines to continue.

                            Empty lines are ignored.

    *- Foo                    Otherwise, leading punctuation marks up the line.

    = Header                  One equals sign is an h1.
    == Sub Header		        Sub header. Note leading spaces are stripped.
    === Sub Sub Header        h3
    ==== Sub Sub Sub Header 	h4

    _underline
    /italicize 
    @bold
    `code

    * bulleted list
    ** indented bulleted list
    # numbered list
    ## outline format

    --- 		                Three or more hyphens is an hr.
    ___			            Three or more underscores is an input field.
    | 			            A leading bar indicates a text box.

    ) one		                single choice 
    ) two

    ] apples		            multiple choice
    ] bananas

    > Now is the time \       block quote 
    for all good men.

    ^http://www.foo.bar/      hyperlink

Specifically, for each line, take the longest leading punctuation
strip trailing whitespace, emit line.

Emit list of (punctuation, text, attributes) tuples.

