# compiler syntax
## directives, guards, annotations

### directives

stuff the complier takes to change the code

`#single-use` // used to prevent double use of a variable, nullifies the var and compiler error \
`#replace` // use this 
### guards

these are value checks, but with extra steps.  
to run with guards on, use the -g or --guards flag.\\


```@(condition)``` is a primitive guard, throws if the condition is true. \
```@type<arg, Type>``` asserts the type of arg, throws if the type is different \
```@max<iteration>``` limit a loop's iteration, throws if the limit is exceeded


### annotations

these are for debugging and expermenting, they need a -a or --annotations flag to run.

?var // prints the value(s) of the variable(s) in the current line  
?read // prints every time the variable is accessed  
?set // prints every time the variable is re-assigned  
?call // prints the function call every time the function is called  
?trace // traces the last function's call  
?type // prints the type(s) of the variable(s) in the current line