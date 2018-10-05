% Booleans, the original true-false dichotomy
% Marc Coiffier

Booleans can have two values, in any given universe.
First, we define the Boolean context :

> { Type 'Bool intro
>   'Bool variable 'true intro
>   'Bool variable 'false intro }
> 'Bool_context swap def

In this context, the type of booleans is simply the Bool type in
context, and the 'true' and 'false' values are respectively the 'true'
and 'false' hypotheses.

> 'Bool  Bool_context 'Bool variable  3 foralls def
> Bool 'Boolean showdef
> 'true 'false  Bool_context 'true variable swap 'false variable 3 lambdas def def
> true 'true false 'false showdef showdef

We can test that 'true' and 'false' have the correct type :

  - type of 'true' : {{true type stache}}
  - type of 'false' : {{false type stache}}
  - type of 'mu(b)' : {{Bool 'b intro 'b variable mu type extro-forall stache}}

Functions on Booleans
---------------------

Then, we can start defining first-level combinators, such as 'not', 'and' and 'or' :

> 'not
>    Bool 'b intro
>    Bool_context 'b variable [ 'Bool variable 'false variable 'true variable ] applyl
>  4 lambdas def 

not is now defined to {{not stache}}. 'not true' is {{true not apply
stache}}, and 'not false' is {{false not apply stache}}; 'not (not b)'
is {{Bool 'b intro 'b variable not apply not apply stache extro-forall}}.

> 'and
>   Bool dup [ 'x 'y ] { intro } each
>   Bool_context 'x variable [
>     'Bool variable
>     'y variable [ 'Bool variable 'true variable 'false variable ] applyl
>     'false variable ] applyl
> 5 lambdas def

'and' is {{and stache}}, 'and true true' is {{and [ true true ] applyl
stache}}. 'and false true' is {{Bool 'x intro and [ false 'x variable ] applyl 1 lambdas
stache}}. 'and true false' is {{and [ true false ] applyl stache}}.

> 'or
>   Bool dup [ 'x 'y ] { intro } each
>   Bool_context 'x variable [
>     'Bool variable
>     'true variable
>     'y variable [ 'Bool variable 'true variable 'false variable ] applyl ] applyl
> 5 lambdas def

'or true false' is {{or [ true false ] applyl stache}}.
