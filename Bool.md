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

We can test that 'true' and 'false' have the correct type :

  - type of {{true dup stache}} : {{type stache}}
  - type of {{false dup stache}} : {{type stache}}
  - type of {{Bool 'b -> b mu ! dup stache}} : {{type stache}}

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not Bool 'b -> Bool_context b ( .Bool .false .true ) ! ! ! ! def

not is now defined to {{not stache}}. 'not true' is {{true not apply
stache}}, and 'not false' is {{false not apply stache}}; 'not (not b)'
is {{Bool 'b intro 'b variable not apply not apply stache extro-forall}}.

> 'and Bool 'x -> Bool 'y -> Bool_context x ( .Bool y ( .Bool .true .false ) .false ) ! ! ! ! ! def

'and' is {{and stache}}, 'and true true' is {{and [ true true ] applyl
stache}}. 'and false true' is {{Bool 'x intro and [ false 'x variable ] applyl 1 lambdas
stache}}. 'and true false' is {{and [ true false ] applyl stache}}.

> 'or Bool 'x -> Bool 'y -> Bool_context x ( .Bool .true y ( .Bool .true .false ) ) ! ! ! ! ! def

'or true false' is {{or [ true false ] applyl stache}}.

> [ 'Bool 'true 'false 'not 'and 'or ] export
