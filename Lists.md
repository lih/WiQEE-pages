% Lists : a general sequence of elements
% Marc Coiffier

Sometimes in life, we want to do a series of tasks in a certain order,
or sort objects in a sequence. In mathematical disciplines, lists play
a similar semantic role, allowing us to express sequences of related
elements.

The simplest kind of list is either an empty list, or a list
containing one element, followed by another list. Given a type {{Type
'A -> A}} of elements, we can define lists of type {{A}} in
the following context :

> 'List_context {
>   Type '.List ->
>   A 'a -> .List 'l -> .List ? ? '.cons ->
>   .List '.nil -> } def

> 'List List_context .List ? ? ? "List A" defconstr
> A 'a -> List 'l -> 'cons List_context .cons ( a l ( .List .cons .nil ) ) ! ! ! "cons a l" defconstr ! !
> 'nil List_context .nil ! ! ! "nil" defconstr

The list recursor, {{List 'l recursor dup tex}}, has type {{type tex}}

> !
> 'list_map Type 'A -> Type 'B -> A 'x -> B ? 'f -> List ( A ) 'l ->
>    l (
>      List ( B ) 
>      A 'x -> List ( B ) 'l -> cons ( B f ( x ) l ) ! !
>      nil ( B )
>    ) ! ! ! ! def

> 'list_append Type 'A -> List ( A ) dup 'x -> 'y -> x (
>    List ( A )
>    cons ( A )
>    y ) ! ! ! def
