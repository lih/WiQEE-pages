% Booleans, the original true-false dichotomy
% Marc Coiffier

> 'utils require import

Booleans can have two values, in any given universe.
First, we define the Boolean context :

> 'Bool-context [ { Type '.Bool } { .Bool '.true } { .Bool '.false } ] def

In this context, the type of booleans is simply the .Bool type in
context, and the 'true' and 'false' values are respectively the '.true'
and '.false' hypotheses.

> 'Bool Bool-context { .Bool } prods  "Boolean" defconstr
> 'true Bool-context { .true } funs   "true"    defconstr 
> 'false Bool-context { .false } funs "false"   defconstr
> [ 'Bool 'true 'false ] { export } each
>? [ true false ] { [ swap dup type ] } each vis

We can test that $true$ and $false$ have the correct type :

  - type of {{true dup}} : {{type tex}}
  - type of {{false dup}} : {{type tex}}
  - type of {{Bool 'b recursor dup tex}} : {{type tex}}

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not { Bool 'b } Bool-context # { b ( .Bool .false .true ) } funs def
> 'and { Bool 'x } { Bool 'y } Bool-context # #
>   { x ( .Bool y ( .Bool .true .false ) .false ) } funs def
> 'or { Bool 'x } { Bool 'y } Bool-context # #
>   { x ( .Bool .true y ( .Bool .true .false ) ) } funs def
> 'implies { Bool 'x } { Bool 'y } Bool-context # #
>   { x ( .Bool y ( .Bool .true .false ) .true ) } funs def
>? [ true false ] [ true false ] { {@ swap @} { [ 2 shaft and 1 dupn apply 2 dupn apply 2 shaft ] } each } each vis

As always, we should verify the type of our combinators, and test
whether they truly conform to their specification :

> [ 'not 'or 'and 'implies ] { dup $ type swap "  - $%s : %l$\n" printf } each

