% Encoding Structural Equality in CaPriCon
% Marc Coiffier

> Type 'A -> A 'x -> A 'y ->
> 
> 'Eq_context { A 'a -> Type ? '.Eq -> .Eq ( x ) '.refl -> } def
> 
> 'Eq Eq_context .Eq ( y ) ? ? "x = y" defconstr
> 'refl Eq_context .refl ! ! "refl x" defconstr

The type of {{Eq 'e -> e mu ! dup}} is {{type}}.

> 3 lambdas [ 'Eq 'refl ] export
