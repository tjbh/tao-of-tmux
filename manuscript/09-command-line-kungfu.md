# Command Line Kung fu {#cli-kung-fu}

The command line in tmux is one of those areas often uncharted.

## Shorthands

tmux commands and arguments may all be accessed via [`fnmatch(3)`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/fnmatch.html)
patterns.

For instance, you don't need to type `$ tmux attach` every time. `$ tmux attac`,
`$ tmux att`, `$ tmux at`, `$ tmux a` work just as well.

Every tmux command has short-hands, let's try this for `$ tmux new-session`:

{language=shell, line-numbers=off}
    $ tmux new-session

    $ tmux new-sessio

    # ...

    $ tmux new-s

and so on, until:

{language=shell, line-numbers=off}
    $ tmux new-
    ambiguous command: new-, could be: new-session, new-window

## Targets {#targets}

If a command allow target specification, it's usually done through `-t`.

Think of targets as tmux's way of specifying a [unique key](https://en.wikipedia.org/wiki/Unique_key)
in a relational database.

| Entity    | Prefix | Example                               |
|-----------|--------|---------------------------------------|
| server    | n/a    | n/a, uses socket-name and socket-path |
| session   | $      | $13                                   |
| window    | @      | @2313                                 |
| pane      | %      | %5432                                 |


## Formats {#formats}

tmux provides a minimal template language and set of variables you can use to
access information about your tmux environment.

Formats are often specified via `-F` flag.

You know how template engines such as
[mustache](https://mustache.github.io/), [handlebars](http://handlebarsjs.com/)
[ERB](http://ruby-doc.org/stdlib-2.3.3/libdoc/erb/rdoc/ERB.html) in ruby,
[jinja2](http://jinja.pocoo.org/docs/dev/) in python,
[twig](http://twig.sensiolabs.org/) in PHP and
[JSP](https://en.wikipedia.org/wiki/JavaServer_Pages) in Java allow template
variables? Formats are a similar concept.

The amount of `FORMATS` (variables) made available by tmux has expanded greatly
since version 1.8. 
