% Miscellaneous utilities
% Marc Coiffier

### Binders and contexts

> 'binder { 2 shaft { {@ swap @} exec -> {@ @} exec {@ @} exec } } def
> 'funs { swap reverse { swap '! $ binder } each exec } def
> 'prods { swap reverse { swap '? $ binder } each exec } def
> '# { swap cons } def
