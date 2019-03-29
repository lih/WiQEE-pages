% Miscellaneous utilities
% Marc Coiffier

### Exporting definitions

> 'defX { 1 dupn swap def export }

### Binders and contexts

> 'Type { 0 universe } defX

> 'foralls { { extro-forall } swap times } defX
> 'lambdas { { extro-lambda } swap times } defX
> 'applys { range { pop apply } each } defX
> 'applyl { { swap apply } each } defX
> 
> 'show-context { "" hypotheses { dup variable type swap "%s : %v\n%s" format } each print pop } defX
> 
> 'showdef { pattern-index 1 swapn swap index-insert set-pattern-index } defX
> 
> 'vis { show-context "-------\n" printf show-stack } defX
> 
> '-> { dup 1 swapn swap intro { {@ dup @} variable pull } def } defX
> '! 'extro-lambda $ defX
> '? 'extro-forall $ defX
> 
> '( '[ $ defX
> ') { ] applyl } defX
> 
> 'defconstr { 1 dupn swap showdef def } defX
> 
> 'recursor { dup 2 shaft -> variable mu ! } defX

> 'binder { 2 shaft { {@ swap @} exec -> {@ @} exec {@ @} exec } } defX
> 'funs { swap reverse { swap '! $ binder } each exec } defX
> 'prods { swap reverse { swap '? $ binder } each exec } defX
> '# { swap cons } defX

