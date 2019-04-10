% Miscellaneous utilities
% Marc Coiffier

Reminder : all builtin functions can be found documented [here](lexicon.html)

#### Exporting definitions

\begin{code}
'defX { 1 dupn swap def export } def 'defX export
\end{code}



#### Navigating the environment

\begin{code}
'show-context {
   "" hypotheses
   { dup variable type swap "%s : %v\n%s" format } each
   print pop
 } defX
'showdef { pattern-index 1 swapn swap index-insert set-pattern-index } defX
'vis { show-context "-------\n" printf show-stack } defX
\end{code}



#### Binders and contexts

\begin{code}
'binder { 2 shaft { ${ swap } -> ${ } ${ } } } defX
'funs { swap reverse { swap '! $ binder } each exec } defX
'prods { swap reverse { swap '? $ binder } each exec } defX
'# { swap cons } defX
\end{code}



#### Constructing typed terms

\begin{code}
'Type { 0 universe } defX
\end{code}



\begin{code}
'foralls { { extro-forall } swap times } defX
'lambdas { { extro-lambda } swap times } defX
'applys { range { pop apply } each } defX
'applyl { { swap apply } each } defX
'recursor { dup 2 shaft -> variable mu ! } defX
\end{code}



\begin{code}
'( '[ $ defX
') { ] applyl } defX
\end{code}



#### Managing the type environment

\begin{code}
'-> { dup 1 swapn swap intro { ,{ dup } variable pull } def } defX
'! 'extro-lambda $ defX
'? 'extro-forall $ defX
\end{code}



#### Defining inductive constructors

\begin{code}
'defconstr { 1 dupn swap showdef def } defX
\end{code}



#### Acting on list as stacks

\begin{code}
'in-list {
  swap {
    ,{ } set-stack ${ }
    { ,{ ,{ stack } } set-stack ,{ stack } } exec
  } exec
} defX
\end{code}


