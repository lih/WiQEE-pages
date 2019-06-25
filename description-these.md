% Thèse : Définition et implémentation de schémas calculatoires pour la preuve de programmes
% Marc Coiffier

Ma thèse se faisant dans le cadre du project VOCAL (Verified OCAml
Library, pour les intimes), j'ai tout d'abord découvert l'univers de
la preuve formelle assistée par ordinateur, en me familiarisant avec
le code dudit projet. Cette familiarisation a été principalement
dirigée par la volonté d'y intégrer une preuve de la correction de
l'algorithme MergeSort implémenté dans la librairie standard OCaml.

Une fois familiarisé avec les bases d'un assistant de preuve (Coq), et
de son modèle de calcul, j'ai exploré différentes modélisations de
théories mathématiques établies, afin de me faire une idée des limites
que l'on pouvait rencontrer, et peut-être de trouver une contribution
intéressante à apporter.

Lors de ces explorations, j'ai voulu modéliser des omega-catégories
(si je ne m'abuse sur les nomenclatures), définies intuitivement comme
suit :

Soient $O$ un type d'objets, et pour toute paire d'objets $x$ et $y$,
un type $M x y$ des morphismes de $x$ vers $y$. On peut définir les
types $O_{n}$ et $M_{n} x y$ (indexés par un naturel $n$) comme suit :

$$
oO : O \rightarrow O_{0} \\
oS : \forall n (x y : O_{n}), M_{n} x y \rightarrow O_{S n}
$$

$$
M_{n} : O_{n} \rightarrow O_{n} \rightarrow Type
mO : \forall (x y : O), M_{0} (o0 x) (o0 y)
mS : \forall n (x y z t : O_{n}) (f : M_{n} x y) (g : M_{n} z t), M_{S n} (oS ... f) (oS ... g) 
$$


