% Miscellaneous utilities
% Marc Coiffier

### Binders and contexts

> 'binder { 2 shaft { {@ swap @} exec -> {@ @} exec {@ @} exec } } def
> 'funs { swap reverse { swap '! $ binder } each exec } def
> 'prods { swap reverse { swap '? $ binder } each exec } def
> '# { swap cons } def

> [ 'binder 'funs 'prods '# ] export

> 'Type { 0 universe } def
> 
> 'foralls { { extro-forall } swap times } def
> 'lambdas { { extro-lambda } swap times } def
> 'applys { range { pop apply } each } def
> 'applyl { { swap apply } each } def
> 
> 'show-context { "" hypotheses { dup variable type swap "%s : %v\n%s" format } each print pop } def
> 
> 'showdef { pattern-index 1 swapn swap index-insert set-pattern-index } def
> 
> 'vis { show-context "-------\n" printf show-stack } def
> 
> '-> { dup 1 swapn swap intro { {@ dup @} variable pull } def } def
> '! 'extro-lambda $ def
> '? 'extro-forall $ def
> 
> '( '[ $ def
> ') { ] applyl } def
> 
> 'defconstr { 1 dupn swap showdef def } def
> 
> 'recursor { dup 2 shaft -> variable mu ! } def
