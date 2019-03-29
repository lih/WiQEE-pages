% Booleans, the original true-false dichotomy
% Marc Coiffier

Booleans can have two values, in any given universe.
First, we define the Boolean context :

> 'Bool_context {
>   'close swap $ def
>    Type '.Bool -> .Bool '.true -> .Bool '.false ->
>    exec 3 close
> } def

In this context, the type of booleans is simply the .Bool type in
context, and the 'true' and 'false' values are respectively the '.true'
and '.false' hypotheses.

> 'Bool { .Bool } 'foralls Bool_context "Boolean" defconstr
> 'true { .true } 'lambdas Bool_context "true"    defconstr 
> 'false { .false } 'lambdas Bool_context "false" defconstr

We can test that $true$ and $false$ have the correct type :

  - type of {{true dup}} : {{type tex}}
  - type of {{false dup}} : {{type tex}}
  - type of {{Bool 'b recursor dup tex}} : {{type tex}}

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not Bool 'b -> { b ( .Bool .false .true ) } 'lambdas Bool_context ! def
> 'and Bool 'x -> Bool 'y -> { x ( .Bool y ( .Bool .true .false ) .false ) } 'lambdas Bool_context ! ! def
> 'or Bool 'x -> Bool 'y -> { x ( .Bool .true y ( .Bool .true .false ) ) } 'lambdas Bool_context ! ! def
> 'implies Bool 'x -> Bool 'y -> { x ( .Bool y ( .Bool .true .false ) .true ) } 'lambdas Bool_context ! ! def

As always, we should verify the type of our combinators, and test
whether they truly conform to their specification :

> [ 'not 'or 'and 'implies ] { dup $ type swap "  - $%s : %l$\n" printf } each

