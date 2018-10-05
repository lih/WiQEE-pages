% WiQEE : A Wiki for mathematical proofs
% Marc Coiffier

The Quod Erat Edificandum Wiki -- WiQEE for short -- is a mix of two
ideas. First of all, it is a documentation platform, whose main
content is the articles written by its contributors. Secondly, it aims to
become a formally-verified library of mathematical proofs and
programs, that can be extracted to executable form, or composed
together to prove more complicated theories.

Every page on this wiki is generated from a source file, written in a
language called CaPriCon. The source of a page can be downloaded from
its menu. If you want to know how the sausage gets made, I invite you
to take a look at [this index's source](index.md) for an example of
such source files.

If you do so, you may notice that the source doesn't look that
different from the article itself. That is because CaPriCon is an
exclusively [literate programming
language](https://en.wikipedia.org/wiki/Literate_programming), in
which most text is simply text, and the code is specially identified
through dedicated syntaxes. The comment formatting language itself is
Markdown in this case, although it would be trivial to adapt it to
other textual markup languages such as TeX.

Literate Programming 
--------------------

Everything you've read until now is a comment of the "index.md"
program. If you want to write programs, though, you will probably need
to write some *code*, which in this case consists in a sequence of
*steps* that are executed in the order in which they appear. The first
sort of code that you can execute is a code paragraph, and is
indicated in the source by starting a line with `> `.

> "<p>Such code is executed, and its output is added to the document.</p>" printf

You can also write some inline code between "mustaches" (a mustache is
a pair of nested `{}` inside the source), which will be executed as
part of a paragraph, and whose output {{"will look like this"
printf}}. If all works well, you should see a small image of steps
next to the generated output. Clicking on those steps will, as in the
previous case and without surprises, show you the steps that were
taken to produce this output.

A Concatenative Language
------------------------

If you peeked at the examples given before, you may have noticed
something strange. In order to produce some output, you'd expect a
sentence to look like `print "..."`, but instead the program was
written in the reverse order, as `"..." print`.

Indeed, in the tradition of PostScript, CaPriCon is a concatenative,
stack-based language. In such a language, programs are represented as
sequences of symbols, that are executed from first to last, and that
may keep intermediate results on a shared stack. All the power of the
language comes from the words that are made available, rather than
from the particular syntax of those words.

Concatenative languages have a few interesting properties that make
them perfect candidates for integration into a literate environment
like the one CaPriCon provides :

  - _simplicity :_ every program is only a sequence of words that are
    evaluated in order, nothing more. You don't have to learn any fancy
    syntax, only the words and what they mean.

    The CaPriCon language only has ~50 basic words in its vocabulary,
    which are referenced [here][:capricon-words]. Beyond that, you can
    define your own words by composing the existing ones into
    so-called "quotes", written `{ word1..wordn }`.

  - _exploration :_ concatenative languages are very well-suited to
    implement incremental development environments, in which you can
    devise programs (and proofs) by walking through their execution
    step by step, with complete control and visibility over the state
    of the environment at every stage.

    To facilitate this process of exploration, you can install the
    [interactive CaPriCon
    interpreter](downloads/capricon.linux.x86_64.tar.xz), that is used
    to power this site.

If you still aren't quite sure how to go about writing your own
scripts, [this tutorial](capricon-tutorial.md) may help walk you
through the first hurdles.

Proofs With Prismatic Constructions
-----------------------------

While CaPriCon is a decent documentation format, it was first designed
as an interactive interface for the construction of proof terms,
described in the Calculus of Prismatic Constructions (hence the name
CaPriCon), which is an extension of the basic CoC with a lifting
operator for naturally inductive values.

That operator is called $\mu$, and it works by projecting inductive
values onto a larger version of themselves, universe-wise. For
example, given the "inductive" type $Id := \forall T:Set_n, T
\rightarrow T$, and a hypothesis $id : Id$, $\mu(id)$ represents a
computationally sound proof of $\forall (T^*:Id \rightarrow
Set_{n+1}), T^*\ (\lambda (T:Set_n) (t:T), t) \rightarrow T^*\ id$.
Each branch of the base inductive type is "projected" through $\mu$ to
a parallel branch in a larger universe, with additional "rays" to
provide reflection into that universe. $\mu$ thus acts like a sort of
*prism* (in fact, an *endoprism*) that continuously projects inductive
values onto their induction principle, hence the name of the calculus.

This generalization can be applied to model many common cases which
previously required the introduction of abstract-only inductive types,
including but not limited to : general dependent inductive types,
complete with recursive and mutually-recursive types; co-inductive
types and their associated semantics; and even some kinds of quotient
types (I haven't fully fleshed out all the useful bits yet).

Where to start ?
----------------

The basics :

  - [Booleans][:Bool]
  - [Equalities][:Eq]
  - [Natural numbers][:Nat]
