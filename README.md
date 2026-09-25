# Mint

a tiny untyped lua-like langauge that 'compiles' to javascript. The current version is written in python.

## philosphy

a personal language for your personal projects. It's simple by default, and grows the way you need it to.

## language overview

the syntax is ~~stolen~~ inspired by lua, so you can learn the langauge over a cup of coffee.

### Hello world

it's simple, create a file `hello.mnt` containing:

```lua
log("hello world") ---this is a comment :)
```

run `mint hello.mnt` and you'll get a `hello.js` file.

### variables

this is an untyped language, to define a variable just use `var`:

```js
var x = 1
var name = "Bond"
var list = []
```

to reassign a variable:

```js
x = 10
name = "James Bond"
list[0] = 43
```

for consts use `const`:

```js
const place = "Paris";
```

### functions

to define a function use the `fn` keyword

```lua
fn foo()
  --- do something
end

fn foo()
  --- do something
  return bar
end
```

#### tiny function notation

to make a one-liner function, aka a lambda function, use this syntax: `fn foo(bar) => <statment>`

```rust
fn x(y) => y + 42
fn foo(n) => bar(n) + 4
fn dispatcher(flag) => if (flag) foo() else bar()
```

### loops

we only have for and while

```lua
while (x < 0) --- while's condition must be wrapped in ()
  --- do something
end

for i in list
   --- do something
end
```

#### break and next

`break` exits the current loop `next` skips the current iteration and starts the next one.

```lua
while (i++ < 10)
  --- do something
  if flag
    break --- or use "next" to skip this iteration
  end
end
```

### conditional statements

a condition must be wrapped in `()` to be evaluated.

```lua
if (x == y)
  --- do something
end

if (flag)
  --- do something
else
  --- do something else
end

if (name == "James")
  --- do something
else if (name == "Bond")
  --- do something
else if (name == "specter")
  --- do something
else
  --- do something
end
```

#### tiny conditional notation

you can write a conditional statement in a single line like: `if (condition) foo() else bar()` the return is ignored by default, unless the statement was preceeded by assignment, then it acts like a ternary op.

```lua
--- call the function and igonre the return
if (highDangerLevel) avengers() else callJBond()
--- assign the returned value to x
x = if (flag) 4 else randInt()
```

### importing

mint takes the headers approach to importing. It uses a .seam file that can act as the face of multiple files. to use a .seam file, use the `use` keyword.

```rust
use <engine.seam>
```

a `.seam` file has a slightly different structure and rules than a normal mint language:

-   to help with the documentation, whatever is inside the brackets `(){}` stays in them. It could be types, arguments and their explantions, whatever. As long as you use `foo(whatever you write here gets ignored)`   to denote functions, and `{same here}` to denote the consts types or returns types.
-   The `from`, `import`, `append` keywords only work inside .seam file. And they accept only one file or lib at a time:
    -   `from` selects something from files and libs.
    -   `import` dedcated to js libs. It can import `as` a namespace.
    -    `append` this just appends mint files, or appends js files to the compilation output.

-   you can assign *functions*, *consts* and *js libs* different names to avoid collisions using the `as` keyword. You however can not us `as` for file names.

```lua
--- engine.seam
from 'engine.mnt' --- mint file
  Scene {struct} --- const
  Camera {struct}
  Object3D {struct}
  render(scene: scene) {int} --- functions
  rendererInit(window: window, bool: gpuFlag) {int | err}
  shaderApply(shader: shader, int: amount) {struct}
end

from 'Math' as math --- js lib must be used as something
  floor(int: number) {void}
end

from 'customlarp.js' --- js file
  larp(int: current, int: min, int: max) {int: final}
  hashr(str: secret) {hash} as encrypt
end

append 'gamelevel.mint' --- appends this to the main mint file
append 'shaders.js' --- appends js to the final compilation
import 'isEven' as even --- for modules / libs
```
