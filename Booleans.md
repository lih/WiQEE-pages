% Booleans, the original true-false dichotomy
% Marc Coiffier

Booleans can have two values, in any given universe.
First, we define the Boolean context :

> 'in {
>    { {@ 2 shift @} exec
>      {@ @} {@ $ @} exec } exec
> } def
> 'fun { { {@ swap @} exec -> {@ @} exec ! } } def
> 'funs { swap reverse { swap fun } each } def
> 'make-Bool {
>    Type '.Bool -> .Bool '.true -> .Bool '.false ->
>    3 in
> } def

In this context, the type of booleans is simply the .Bool type in
context, and the 'true' and 'false' values are respectively the '.true'
and '.false' hypotheses.

> 'Bool { .Bool } 'foralls make-Bool "Boolean" defconstr
> 'true { .true } 'lambdas make-Bool "true"    defconstr 
> 'false { .false } 'lambdas make-Bool "false" defconstr

We can test that $true$ and $false$ have the correct type :

  - type of {{true dup}} : {{type tex}}
  - type of {{false dup}} : {{type tex}}
  - type of {{Bool 'b recursor dup tex}} : {{type tex}}

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not Bool 'b -> { b ( .Bool .false .true ) } 'lambdas make-Bool ! def
> 'and Bool 'x -> Bool 'y ->
>   { x ( .Bool y ( .Bool .true .false ) .false ) } 'lambdas make-Bool
>   ! ! def
> 'or Bool 'x -> Bool 'y ->
>   { x ( .Bool .true y ( .Bool .true .false ) ) } 'lambdas make-Bool
>   ! ! def
> 'implies Bool 'x -> Bool 'y ->
>   { x ( .Bool y ( .Bool .true .false ) .true ) } 'lambdas make-Bool
>   ! ! def

As always, we should verify the type of our combinators, and test
whether they truly conform to their specification :

> [ 'not 'or 'and 'implies ] { dup $ type swap "  - $%s : %l$\n" printf } each

