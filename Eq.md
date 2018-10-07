% Encoding Structural Equality in CaPriCon
% Marc Coiffier

> 'Eq_context {
>   'x swap def 'A swap def
>   A 'a intro 0 universe 1 foralls 'Eq intro
>   x 'Eq variable apply 'refl intro } def

> Type 'A intro 'A variable dup 'x intro 'y intro

> 'Eq 'A variable 'x variable Eq_context 'y variable 'Eq variable apply 2 foralls def
> 'refl 'A variable 'x variable Eq_context 'refl variable 2 lambdas def
>  Eq "x = y" showdef
>  refl "refl x" showdef

The type of {{Eq 'e intro 'e variable mu 1 lambdas dup stache}} is {{type stache}}.

> 3 lambdas


