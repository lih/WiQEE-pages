Equality
========

> 'Eq_context {
>   'x swap def 'A swap def
>   A 'a intro 0 universe 1 foralls 'Eq intro
>   x 'Eq variable apply 'refl intro } def

> Type 'A intro 'A variable dup 'x intro 'y intro

> 'Eq 'A variable 'x variable Eq_context 'y variable 'Eq variable apply 2 foralls def
> Eq "x = y" showdef

> 2 lambdas

> Eq show 
