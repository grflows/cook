# kiwi 🥝

a tiny lua-like langauge transpiled into javascript. The current version is written in python.

## philosphy

simple by default, complex when it needs to.

## overview

to check the syntax and learn the langauge [click here](http://localhost:33583/doc/overview.md)

## some quality of life features

### PHP kind of methodology

the most used things are turned into sensably named keywords, functions, or methods. Here's an example:

```js
const playBtn = document.getElementById("play");
```

simple use `map` to map a variable to a DOM object

```lua
map playBtn to objById('play')

-- or use it as a block
map
    volUp objById('volume-up')
    volDwn objById('volume-down')
    artWork objByClass('art-work')
end

-- and if you only use the same objBy(), just simplify it to
map to objById()
    nextBtn 'next'
    pauseBtn 'pause'
    muteBtn 'mute'
end
```

### guards and debugging annotations

these are compile and run-time checkers to prevent some simple but annoying bugs. Here're some of the most used guards.

-   `@(condition)` is a primitive guard, throws if the condition is false.
-   `@type<arg, Type>` asserts the type of arg, throws if the type is different.
-   `@max<iteration>` limits a loop's iteration, throws if the limit is exceeded.
-   `@impure<fn(err, ..)>` if a statement returns null or undefined, fn(err) is called.

The debugging annotations simply replaces the log() if you're a print debugger. Here're some of the common onces:

-   `?var` basically log(\_variable-name, \_variable\_value)
-   `?trace` prints the last function call of `foo() ?trace`
-   `?track` logs every call to the tracked function

### macros

you can like them, you can hate them, but you can't say they make writing code harder.
the simplest form of macro is`#replace "string $1..$n" -> <statement $1..$n>`

```lua
#replace ">> $1 $2" -> map $1 to objById('$2')

>> playerBtn player-buttn
-- turns into: map playBtn to objById('play')
```
