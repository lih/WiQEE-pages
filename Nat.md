% Natural Numbers, or the best way to enumerate anything
% Marc Coiffier

> 'Nat_context {
>    Type 'Nat intro
>   'Nat variable 'zero intro
>   'Nat variable 'n intro 'Nat variable 1 foralls 'succ intro
> } def

> 'Nat Nat_context 'Nat variable 3 foralls def
> Nat 'Nat showdef
> 'zero Nat_context 'zero variable 3 lambdas def
> zero "0" showdef
> 'succ Nat 'n intro Nat_context 'succ variable [ 'n variable ] applyl 3 lambdas def
> succ "S n" showdef 1 lambdas

The `Nat` type is defined to {{Nat stache}}. {{Nat 'n
intro 'n variable mu extro-lambda dup stache}} has type {{type stache}}.

