[back to homepage](index.md)

# Lab Report 4

<br />

## Analyzing Snippets of Code Using Different Implementations

<br />

The link to my group's repository: https://github.com/sallada1/markdown-parse

The link to the repository that my group reviewed: https://github.com/pvijay03/markdown-parse 

<br />

Here are the snippets of code that we are analyzing:

## Snippet 1
```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

## Snippet 2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

## Snippet 3
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```

<br />

## Snippet 1 Expected Output:

```
[`google.com, google.com, ucsd.edu]
```

<br />

## Snippet 2 Expected Output:

```
[b.com, a.com(()), example.com]
```

## Snippet 3 Expected Output:

```
[https://ucsd-cse15l-w22.github.io/]
```


