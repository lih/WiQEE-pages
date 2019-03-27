% Natural Numbers, or the best way to enumerate anything
% Marc Coiffier

> 'Nat_context { Type '.Nat -> .Nat '.zero -> .Nat 'n -> .Nat ? '.succ -> } def

> 'Nat Nat_context .Nat 3 foralls "Natural" defconstr
> 'zero Nat_context .zero 3 lambdas "0" defconstr
> Nat 'n -> 'succ Nat_context .succ ( n ( .Nat .zero .succ ) ) 3 lambdas "S n" defconstr !

The `Nat` type is defined to {{Nat tex}}. {{Nat 'n recursor dup tex}} has type {{type svg}}.

{{succ dup tex}} has type {{type tex}}.
