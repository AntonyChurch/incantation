# Incantation
Incantation is a programming language to make the programmer feel like a wizard again. Conjure spells, write books for others to consume. Take over the world.

## Language Definition
`spell` is an application/program

`book` is a library/module (a way to share code)

`chapter` can be used to break a book into smaller pieces

`share` is a list that defines which steps can be used by external programs

`step {step name} {comma seporated parameters}:` is a function or method often defined in books, all steps return a value, steps can contain multiple lines separated with a comma and ending with either a semi colon `;` (if other matches are potential) or a full stop `.` (to return that value)

`#` is used for comments

`say` prints the parameter to the console

`Value = 1` Variables are matched and immutable like in Erlang and start with capitol letters

`_` Can be used to match variables you don't currently care about

Creating a spell
```
spell fibonaci #Spell is called fibonaci

book sequences #Use book sequences

step cast: #cast is the first point of contact for a spell
    say sequences.fib.at(10). #fib_at is a step defined in the sequences book which will print the 10th number in the fibonaci sequence

# Output:
    > 89
```

Creating a book
```
book sequences

chapter fib

share [at/1]

step at X:
    fib X - 1, [1, 1].

step fib 0, Squence:
    [Head | _ ] = Sequence,
    Head;

step fib Count, Sequence:
    [Head | Tail] = Sequence,
    [Head2 | _ ] = Tail
    Value = Head + Head2,
    NewSequence = [Value] ++ Sequence,
    fib(Count - 1, NewSequence).
```
Book in Erlang (for comparisson)
```
-module(fib).

-export([at/1]).

at(X) ->
    fib(X - 1, [1, 1]).

fib(0, Sequence) ->
    [Head | _ ] = Sequence,
    Head;

fib(Count, Sequence) ->
    [Head | Tail] = Sequence,
    [Head2 | _ ] = Tail,
    Value = Head + Head2,
    NewSeq = [Value] ++ Sequence,
    fib(Count - 1, NewSeq).
```

## TODO
1. Start the language
2. Make list functions a lot nicer
3. Make a better example
4. Testing
5. Website?
6. ...
7. Profit?


## Ideas
- MyLibrary could be used like Cargo in rust or rebar in Erlang
- Library could be used like Crates in Rust or the Elixir equivelant that I can't remember
