# Overview

## Basic Syntax

### Hello world
it's simple, create a file hello.kw containing:

print("hello world") // this is a comment :)

run kiwi hello.kw
you'll get a hello.js

### variables
to define a var just do:

var x = 1
var name = "Bond"

to reassign a var:

let x = 10
let name = "James Bond"

#### variables modifications
mods changes the behaviour of variables:

const // make it constant
temp // make it single use
secret // encrypted in memory, only decrypted when read
pub // make it global
local // for the current module use only
owned .. <foo(), bar()> // only allowed to be read by pre-defined functions
shared // safe to share between threads and async calls
opt // can return value, null, or err

### functions
do define a function use fn

fn foo()
  // do something
end

#### lambda functions
use to make a lambda function, use fn foo(bar) -> // something 
fn x(y) -> y + 42
lambda functions strictly do arithmetics evaluations.
They either return a value, null, or an err.


### loops
we only have for and while

while x < 0
  // do something
end

for i in list
  // do something
end

you can use the #limit directive to prevent a forever loop.

while x < y  #limit 10
  // do something
end

for i in db #limit 39
  // do something
end

### conditional statements
the same ol' if-else syntax

if (x == y)
  // do something
end

if (flag)
  // do something
else
  // do something else
end

if (name == "James")
  // do something
else if (name == "Bond")
  // do something
else if (name == "specter")
  // do something
else
  // do something
end

#### ternary Ops
for a simple op, (condition)=> foo else bar
var x (flag)=> 4 else 2

### code blocks
define a code block using the block keyword, to exit a block, use the exit keyword

block
  // do something
  exit block
end



