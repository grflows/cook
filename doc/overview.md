# Overview

kiwi is a tiny lua-like language that transpiles into js.

## basic Syntax

### Hello world

it's simple, create a file ```hello.kw``` containing:

```lua
print("hello world") --this is a comment :)
```

run `kiwi hello.kw` and you'll get a ```hello.js``` file.

### variables

to define a variable just do:

```js
var x = 1;
var name = "Bond";
var list = [];
```

to reassign a variable:

```js
set x = 10
set name = "James Bond"
set list\[0] = 43
```

for consts use ```const```:

```js
const place = "Paris";
```

### functions

to define a function use the ```fn``` keyword

```lua
fn foo()
  -- do something
end

fn foo()
  -- do something
  return bar
end
```

#### tiny function notation
to make a one-liner function, aka a lambda function, use this syntax: \
```fn foo(bar) -> <statment>```
```rust
fn x(y) -> y + 42
fn foo(n) -> bar(n) + 4
fn t(flag) -> (flag)? j() else n()
```

### loops

we only have for and while

```lua
while x < 0
  -- do something
end

for i in list
   -- do something
end
```

you can use the ```@max<iteration>``` guard to prevent a forever loop.

```lua
while x < y @max<10>
  -- do something
end

for i in db @max<39>
  -- do something
end
```

#### break and next

```break``` exits the current loop
```next``` skips the current iteration and starts the next one.

```lua
while true
  -- do something
  if flag
    break -- or use "next" to skip this iteration
  end
end
```

### conditional statements

the same ol' if-else syntax

```lua
if (x == y)
  -- do something
end

if (flag)
  -- do something
else
  -- do something else
end

if (name == "James")
  -- do something
else if (name == "Bond")
  -- do something
else if (name == "specter")
  -- do something
else
  -- do something
end
```

#### conditional assignment

for a simple op; (condition)? foo else bar

```js
var x (flag)? 4 else 2
```

### defer
defers a single-line statement's execution to the end of the current scope. There can only be one ```defer``` per scope.

```odin
  defer print('3')
  print('1')
  print('2')
```


### directives, guards, and annotations

#### directives

stuff the complier takes to change the code

`#single-use` // used to prevent double use of a variable, nullifies the var and compiler error

#### guards

these are value checks, but with extra steps.
to run with guards on, use the -g or --guards flag.\\


```@(condition)``` is a primitive guard, throws if the condition is true. \
```@type<arg, Type>``` asserts the type of arg, throws if the type is different \
```@max<iteration>``` limit a loop's iteration, throws if the limit is exceeded


#### annotations

these are for debugging and expermenting, they need a -a or --annotations flag to run.

?var // prints the value(s) of the variable(s) in the current line
?read // prints every time the variable is accessed
?set // prints every time the variable is re-assigned
?call // prints the function call every time the function is called
?trace // traces the last function's call
?type // prints the type(s) of the variable(s) in the current line
