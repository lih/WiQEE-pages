% Natural Numbers, or the best way to enumerate anything
% Marc Coiffier

> 'utils require import

> 'Nat_context [ { Type '.Nat } { .Nat '.zero } { .Nat 'n -> .Nat ? '.succ } ] def

> 'Nat Nat_context { .Nat } prods "Natural" defconstr
> 'zero Nat_context { .zero } funs "0" defconstr
> Nat 'n -> 'succ Nat_context { .succ ( n ( .Nat .zero .succ ) ) } funs "S n" defconstr !

The `Nat` type is defined to {{Nat tex}}. {{Nat 'n recursor dup tex}} has type {{type tex}}.

{{succ dup tex}} has type {{type tex}}. 
