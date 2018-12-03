% Booleans, the original true-false dichotomy
% Marc Coiffier

Booleans can have two values, in any given universe.
First, we define the Boolean context :

> 'Bool_context { Type '.Bool -> .Bool '.true -> .Bool '.false -> } def

In this context, the type of booleans is simply the .Bool type in
context, and the 'true' and 'false' values are respectively the '.true'
and '.false' hypotheses.

> 'Bool Bool_context .Bool ? ? ? "Boolean" defconstr
> 'true Bool_context .true ! ! ! "true"    defconstr 
> 'false Bool_context .false ! ! ! "false" defconstr

We can test that $true$ and 'false' have the correct type :

  - type of {{true dup}} : {{type}}
  - type of {{false dup}} : {{type}}
  - type of {{Bool 'b -> b mu ! dup}} :

> type "$%l$\n" printf

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not Bool 'b -> Bool_context b ( .Bool .false .true ) ! ! ! ! def
> 'and Bool 'x -> Bool 'y -> Bool_context x ( .Bool y ( .Bool .true .false ) .false ) ! ! ! ! ! def
> 'or Bool 'x -> Bool 'y -> Bool_context x ( .Bool .true y ( .Bool .true .false ) ) ! ! ! ! ! def

As always, we should verify the type of our combinators, and test
whether they truly conform to their specification :

> [ 'not 'or 'and ] { dup $ type swap "  - $%s : %l$\n" printf } each
