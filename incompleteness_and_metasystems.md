**Incompleteness, formal descriptions, and functional systems**

Research note prepared on 17 September 2026. Version 1.0.

Status: mathematical exposition and proposed interpretation, with proofs of the stated auxiliary results. This is not a refutation of Gödel's theorems, a claim of a new discovery, or a machine-checked proof. The theorem names below are descriptive names for this note; the underlying ingredients are standard.

The motivating request was to formulate a theorem showing that incompleteness is either not functionally valid or concerns partially constituted systems defined by a metasystem rather than complex systems as a whole. The defensible result is that **incompleteness of a formal description does not, by itself, imply failure of a system's specified functions or incompleteness of every description of that system.** A separate result explains precisely how an effective arithmetic description can be a proper part of a complete semantic theory.

The stronger assertion that Gödel's theorem is mathematically invalid is not established here. The phrase “complex systems as a whole” also requires a definition before it can appear in a theorem. The examples below establish a failure of a universal inference; they do not estimate how representative incompleteness is across real complex systems.

**Definitions and scope.** Work in ordinary classical mathematics, in an ambient metatheory capable of discussing natural numbers, finite strings, and structures; ZFC is one suitable example. This specifies the standpoint of the argument, not a proof that this standpoint is infallible or self-justifying.

A formal theory consists of axioms in a specified language, with a specified proof calculus. Write \(T\vdash\varphi\) when a finite proof of the sentence \(\varphi\) exists from those axioms. Write \(\operatorname{Thm}(T)\) for the set of its provable sentences.

A structure \(\mathcal A\) supplies a domain and interpretations of the language's symbols. Write \(\mathcal A\models\varphi\) when \(\varphi\) is true in that structure, and define

\[
\operatorname{Th}(\mathcal A)
 = \{\varphi:\varphi\text{ is a sentence and }\mathcal A\models\varphi\}.
\]

These notions must be distinguished:

| Property | Meaning in this note |
| --- | --- |
| Consistency | The theory does not prove a contradiction. |
| Soundness for \(\mathcal A\) | Every sentence the theory proves is true in \(\mathcal A\). |
| Syntactic completeness | For every sentence \(\varphi\), the theory proves \(\varphi\) or proves \(\neg\varphi\). |
| Effective axiomatization | An algorithm can enumerate the axioms; with the usual effective proof rules, the theorems are also computably enumerable. |
| Decidability of \(\operatorname{Th}(\mathcal A)\) | An algorithm halts on every sentence and correctly determines its truth in \(\mathcal A\). |
| Adequacy for a query class \(\mathcal C\) | For every \(\varphi\in\mathcal C\), the theory proves the answer that is true in the intended structure. |

Functional success additionally requires a task specification. For a question-answering task, adequacy for \(\mathcal C\) is a useful formalization. Actual performance within a time or memory budget is an additional condition.

Use the following standard background result: every consistent, computably axiomatized first-order theory interpreting Robinson arithmetic \(Q\) is syntactically incomplete. This is the Gödel–Rosser form of the first incompleteness theorem. The interpretation requirement concerns arithmetic expressiveness, not system size or an informal notion of complexity. [Moschovakis, *Lecture Notes in Logic*, Theorem 4C.4, printed p. 151](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=155).

**Theorem 1 — An effective description can be a proper part of a complete semantic theory.**

Let \(T\) be a computably axiomatized theory in the language of arithmetic, extending \(Q\), and sound for the standard natural numbers \(\mathbb N\). Then:

1. \(\operatorname{Thm}(T)\subsetneq\operatorname{Th}(\mathbb N)\).
2. \(\operatorname{Th}(\mathbb N)\), called true arithmetic, is consistent, deductively closed, and syntactically complete.
3. \(\operatorname{Th}(\mathbb N)\) is not computably enumerable.
4. Every particular true sentence unprovable in \(T\) can be made provable in a sound effective extension of \(T\), but that extension is still incomplete.

**Proof.** Soundness gives the non-strict inclusion in part 1 and implies that \(T\) is consistent. By Gödel–Rosser, some sentence \(\rho\) has neither a proof nor a refutation in \(T\). Classical semantics makes exactly one of \(\rho,\neg\rho\) true in \(\mathbb N\). That true sentence belongs to \(\operatorname{Th}(\mathbb N)\) but not to \(\operatorname{Thm}(T)\). The inclusion is strict.

For part 2, the true sentences cannot include a contradictory pair. Sound inference preserves truth, so they are deductively closed. For each sentence \(\varphi\), either \(\varphi\) or \(\neg\varphi\) is true in \(\mathbb N\); thus one belongs to this theory and is available as an axiom.

For part 3, suppose that true arithmetic were computably enumerable. Taking its sentences as axioms would yield a consistent, effective, complete extension of \(Q\), contradicting Gödel–Rosser.

For part 4, fix a true sentence \(\psi\) unprovable in \(T\). Set \(U=T+\psi\). Appending a single fixed sentence preserves effective axiomatizability. Its axioms remain true in \(\mathbb N\), so \(U\) remains sound, and it proves \(\psi\). Since \(U\) still meets the incompleteness hypotheses, some other sentence is undecided in \(U\). \(\square\)

This gives “partially constituted” a precise possible meaning: the provable content of an effective description is a proper subset of an intended structure's full first-order theory. It does not say that the structure itself lacks parts or fails to exist.

Part 4 is an existence construction. It does not supply an algorithm for recognizing arbitrary true sentences. Adding an assumption is also different from justifying that assumption. A separate argument or metatheory would be needed to warrant a particular addition.

Nor does writing \(\operatorname{Th}(\mathbb N)\) give us a usable all-purpose truth oracle. It defines the complete set semantically. Part 3 states why an effective proof system cannot enumerate it. Even a complete first-order theory need not uniquely characterize its intended infinite structure up to isomorphism; completeness is not categoricity.

**Theorem 2 — Incompleteness does not transfer automatically to a system's functions.**

For every nonempty finite relational structure \(\mathcal A\) in a finite language, there is a consistent, computably axiomatized theory \(T_{\mathcal A}\) such that:

1. \(T_{\mathcal A}\) interprets arithmetic and is incomplete.
2. Every first-order sentence about the \(\mathcal A\) part alone is correctly decided by \(T_{\mathcal A}\).
3. Truth for those sentences is uniformly decidable from the finite tables specifying \(\mathcal A\).
4. The axioms describing the \(\mathcal A\) part characterize it up to isomorphism.

Consequently, the existence of an undecidable sentence somewhere in a formal theory does not entail an unanswered question in every specified operational domain described by that theory.

**Proof.** Suppose the domain of \(\mathcal A\) is \(\{a_1,\ldots,a_n\}\), with \(n\geq1\). Introduce names \(c_1,\ldots,c_n\) for these elements. Construct the following finite axiom set \(D_{\mathcal A}\):

- Distinctness: \(c_i\neq c_j\) for \(i\neq j\).
- Domain closure: \(\forall x\,(x=c_1\lor\cdots\lor x=c_n)\).
- Complete relation tables: for each relation symbol \(R\) and each tuple of names of the appropriate length, include the corresponding atomic sentence if it is true in \(\mathcal A\), and its negation otherwise.

If the original language has constants, include equations giving their values among the \(c_i\). Relations of arity zero, if present, receive their truth values in the same way.

Every model of \(D_{\mathcal A}\) has exactly the named elements and the specified relation tables. The map sending \(c_i\) to \(a_i\) is an isomorphism. This proves part 4.

For any formula, domain closure allows each universal quantifier to be replaced by a conjunction over the names and each existential quantifier by a disjunction. Repeating this reduces a sentence to a finite Boolean combination of ground atomic sentences. The tables and distinctness axioms settle every such atom. Hence \(D_{\mathcal A}\) proves the sentence if it is true in \(\mathcal A\), and proves its negation otherwise. This also gives a terminating evaluation algorithm, uniformly from the finite input tables.

Now use two sorts, one for arithmetic and one for \(\mathcal A\), with no symbols connecting the sorts. Put Peano arithmetic \(PA\) on the arithmetic sort and \(D_{\mathcal A}\) on the system sort:

\[
T_{\mathcal A}=PA\;\sqcup\;D_{\mathcal A}.
\]

Here \(\sqcup\) means this explicitly disjoint, two-sorted combination. The pair \((\mathbb N,\mathcal A)\), with the specified names, is a model, so the combined theory is consistent. Its axioms are effectively enumerable. It contains an interpretation of \(Q\) on its arithmetic sort. Gödel–Rosser therefore makes it incomplete; the usual effective translation of sorted first-order logic into first-order logic gives the same conclusion.

Every proof from \(D_{\mathcal A}\) remains a proof in \(T_{\mathcal A}\). The correct decisions and algorithm already established for the system language therefore persist. This proves all four parts. \(\square\)

This construction deliberately separates the arithmetic domain from the system domain. That is enough to refute a universal inference from global incompleteness to failure in every domain. It does not establish the same separation for a theory where arithmetic and system behavior are coupled.

There is also a direct result requiring no appended arithmetic: \(D_{\mathcal A}\) itself is a finite, consistent, complete description of the named finite structure, and its theorem set is decidable. Thus being a system described within a larger mathematical framework does not itself force incompleteness.

**An operational example.** Let \(\mathcal A=(S,E)\) be a finite transition graph: \(S\) is the state set and \(E(s,t)\) means that a permitted transition takes \(s\) to \(t\). Theorem 2 applies for every finite size, however large.

For example, take \(S=\{a,b,c\}\) with exactly the transitions \(a\to b\), \(b\to c\), and \(c\to c\). The formula

\[
\exists y\,(E(a,y)\land E(y,c))
\]

is true, witnessed by \(b\). The formula

\[
\exists y\,(E(c,y)\land y\neq c)
\]

is false, because \(c\)'s only successor is \(c\) itself. The finite description proves the first sentence and the negation of the second.

More generally, reachability in a graph with \(n\) states is decidable: if a path from \(s\) to \(t\) exists, deleting loops gives a path of length at most \(n-1\), allowing length zero when \(s=t\). Search those paths or perform ordinary graph traversal. Whether a specified bad state can ever be reached is therefore decidable as well. This is an unbounded-time reachability claim for a fixed finite graph, not merely a bounded simulation.

The fixed finite graph and its available transition table are essential assumptions. A family of machines with unbounded memory, an unknown environment, or a language quantifying over arbitrary programs poses a different problem. Large state spaces can also make an existing decision procedure impractical. Decidability does not promise affordable computation.

Calling these examples “complex” is an interpretation, not a proved classification. They permit arbitrary finite network size and interaction tables. They establish that those features alone do not imply Gödel incompleteness.

**Proposition — Undecidability can express underdetermination by the axioms.**

Suppose \(T\) is a consistent first-order theory in a countable language and neither \(\varphi\) nor \(\neg\varphi\) is provable in it. Then there are models \(\mathcal B,\mathcal C\) of \(T\) with

\[
\mathcal B\models\varphi,\qquad
\mathcal C\models\neg\varphi.
\]

**Proof.** If \(T+\varphi\) were inconsistent, the deduction theorem would give \(T\vdash\neg\varphi\), contrary to the hypothesis. Similarly, \(T+\neg\varphi\) is consistent. The first-order completeness theorem supplies a model of each. \(\square\) The model-existence result used here is [Moschovakis, Theorem 1I.1, printed p. 38](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=42).

This is another precise version of the partial-description idea. The axioms leave open alternatives that different models settle differently. An intended model, when one is specified, has its own truth value for \(\varphi\); the original axioms do not settle which alternative holds.

The word “complete” in the first-order completeness theorem means that every consequence true in all models of given axioms has a formal proof. It does not mean that those axioms decide every sentence. Consequently, this proposition and Gödel incompleteness are compatible.

**Theorem 3 — Effective accumulation of metasystems remains incomplete.**

Let

\[
T_0\subseteq T_1\subseteq T_2\subseteq\cdots
\]

be nested consistent axiom sets in a common effective first-order language. Suppose \(T_0\) extends \(Q\), and the axiom sets are uniformly computably enumerable: one algorithm can enumerate all pairs \((n,\alpha)\) with \(\alpha\) an axiom of \(T_n\). Then the union

\[
T_\infty=\bigcup_{n\in\mathbb N}T_n
\]

is consistent, computably axiomatized, and incomplete.

**Proof.** Enumerate the pairs and discard their first coordinates to enumerate the union's axioms. Any proof of a contradiction from the union uses finitely many axioms. Each belongs to some stage, and the largest of those finitely many stage indices supplies a single \(T_N\) containing them all. That would make \(T_N\) inconsistent. Hence the union is consistent. It contains \(Q\); Gödel–Rosser makes it incomplete. \(\square\)

Uniformity matters. The fact that every stage individually has an effective axiomatization does not mean that the whole sequence can be generated by one algorithm.

For a concrete contrast, effectively list all arithmetic sentences as \(\varphi_0,\varphi_1,\ldots\). Using semantic truth in the metatheory, choose

\[
\theta_i=
\begin{cases}
\varphi_i,&\mathbb N\models\varphi_i,\\
\neg\varphi_i,&\mathbb N\not\models\varphi_i.
\end{cases}
\]

Put \(U_n=PA+\{\theta_0,\ldots,\theta_n\}\). Every \(U_n\) is a sound effective theory, since it is a finite extension of \(PA\). The deductive closure of their union is true arithmetic: every true sentence eventually appears, and sound deduction produces only truths.

However, the sequence of selected answers is not effective. If its stage axioms were uniformly enumerable, true arithmetic would be computably enumerable, contrary to Theorem 1. The construction therefore illustrates the exact price of this complete union: an externally specified, non-effective supply of correct answers.

The same obstruction applies to an adaptive process whenever all of its accepted axioms can ultimately be enumerated by an ordinary algorithm and their accumulated theory is consistent and contains \(Q\). Changing rules, learning, or adding stages does not by itself establish that these hypotheses fail. If revisions retract axioms, the nested-union proof above need not describe the process; a different formal analysis is then required.

Gödel himself noted, in footnote 48a of his original paper, that the undecidable propositions under discussion could become decidable after suitable higher types were added. The historical observation supports the relativity of particular undecidability results to a framework; it does not assert the existence of a final effective complete framework. [Gödel, 1931, Meltzer translation, printed p. 62, footnote 48a](https://homepages.uc.edu/~martinj/History_of_Logic/Godel/Godel%20%E2%80%93%20On%20Formally%20Undecidable%20Propositions%20of%20Principia%20Mathematica%201931.pdf#page=65).

**A precise formulation closest to the motivating thesis.**

> For any effective arithmetic theory \(T\) extending \(Q\) and sound for \(\mathbb N\), its provable content is a proper part of the complete semantic theory \(\operatorname{Th}(\mathbb N)\). This limitation of the description does not entail failure on every specified task: there exist consistent effective incomplete theories that completely and decidably describe a finite operational domain. Stronger frameworks can settle particular earlier questions, while any consistent effective accumulation retaining sufficient arithmetic remains incomplete.

Theorem 1 supplies the first sentence, Theorem 2 supplies the second, and Theorem 3 supplies the limitation in the third. This is a statement about the scope and consequences of incompleteness.

“A metasystem partially constitutes its object” can mean that a chosen language and axiom set determine what is expressible and derivable in a representation. That interpretation is consistent with these results. If it instead means that an external observer causes an otherwise complete effective arithmetic calculus to become incomplete, no such conclusion follows.

In particular, changing notation or recoding proofs cannot remove the obstruction while preserving the hypotheses. The arithmetic theory can encode its own finite proof syntax. A metatheory is where we establish the incompleteness result, but being studied from outside is not an extra defect in the object theory.

Nor does semantic completeness establish metaphysical wholeness. \(\operatorname{Th}(\mathcal A)\) comprises truths in one chosen language about one chosen structure. Additional languages, physical interpretation, and experimental adequacy remain separate questions.

The second incompleteness theorem concerns a further restriction: under its standard hypotheses, a consistent effective extension of \(PA\) cannot prove its own standard arithmetized consistency statement. It does not say that another theory cannot prove that statement. Moving a consistency argument to a stronger metatheory therefore changes the proving framework and its assumptions; it does not furnish unconditional self-certification. [Moschovakis, §4C](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=155).

**Preserved candidate arguments and their disposition.**

These are explicit candidate arguments considered for this note, with their mathematical status. They are retained for posterity rather than presented as established results.

| Candidate claim | Assessment | What can be retained |
| --- | --- | --- |
| “A metasystem proves a sentence that the original system cannot, so the incompleteness theorem is false.” | Invalid inference: provability in two different theories has been conflated. | Particular undecidability is relative to the specified theory. |
| “A complete semantic theory exists, so Gödel's theorem has a counterexample.” | Invalid as a refutation: true arithmetic fails effective axiomatizability. | Completeness and effectiveness are distinct requirements. |
| “Keep adding each missing truth; the resulting effective system will be complete.” | The effectiveness claim is unsupported. Theorem 3 excludes a consistent effective complete union extending \(Q\). | An externally truth-selected union can be complete, at the cost of a non-effective selection process. |
| “Complex systems cannot be represented by fixed theories.” | Unproved and too broad; neither “complex” nor “represented” has been specified. | Whether a particular representation meets the incompleteness hypotheses must be checked. |
| “An incomplete theory cannot correctly operate or analyze a system.” | False as a universal statement, by Theorem 2 and its finite graph example. | Some tasks may still encode genuinely undecidable problems. |
| “Finite systems are fully understood in practice.” | Too strong: decidability does not guarantee feasible computation, a known transition table, or an accurate physical model. | A specified finite relational structure has the complete finite description constructed above. |
| “The unknown truth value means reality itself is incomplete.” | This moves from a proof-theoretic property to an undefined ontological property. | An axiom system can underdetermine which model is intended. |
| “These examples show that incompleteness is generally unrepresentative of complex systems.” | Not established: no class of complex systems, distribution, or prevalence criterion was supplied. | They disprove an unrestricted inference from complexity or functional usefulness alone to incompleteness. |

A finite workload also cannot establish universal completeness. If \(F\) is a finite collection of arithmetic questions and \(T\) is sound, adjoining the correct answer to each question produces a sound effective theory adequate for \(F\). But identifying those correct answers may be unavailable, and the resulting theory is still incomplete if it extends \(Q\). This is an existence observation, not an algorithm for solving arbitrary finite lists of hard problems.

**What would be needed for a stronger result.** To assess an actual complex system, specify its states and dynamics, its representation, the questions that count as its functions, and the required computational resources. If the proposed claim concerns all systems in a class, specify that class and the quantifiers. To overturn the mathematical theorem itself, one would need a consistent effective theory with the required arithmetic interpretation that nevertheless decides every sentence, together with a demonstrable error in the applicable incompleteness proof. Nothing in this note provides that.

**Source and verification record.** The arguments above are written out as mathematical derivations, not presented as quotations or novel published research. The background incompleteness and completeness results were checked against the following sources on 17 September 2026:

- Kurt Gödel, “Über formal unentscheidbare Sätze der Principia Mathematica und verwandter Systeme I” (1931), consulted in B. Meltzer's English translation, *On Formally Undecidable Propositions of Principia Mathematica and Related Systems*. Relevant locations: Proposition VI, printed p. 57; generalization and footnote 48a, printed p. 62. Gödel's original formulation uses stronger consistency assumptions than the later Rosser version used here. [University of Cincinnati hosted translation](https://homepages.uc.edu/~martinj/History_of_Logic/Godel/Godel%20%E2%80%93%20On%20Formally%20Undecidable%20Propositions%20of%20Principia%20Mathematica%201931.pdf).
- Yiannis N. Moschovakis, *Lecture Notes in Logic*, dated 29 March 2014. Relevant locations: Theorem 1I.1 on first-order completeness, printed p. 38; Theorem 4C.4 on Gödel–Rosser incompleteness, printed p. 151; subsequent discussion in §4C. The posted document labels itself informal notes; it is used for its explicit theorem statements and proofs. [Author's UCLA notes](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf).

The proof review checked that Theorem 1 assumes soundness when relating provability to intended truth; that Theorem 2 includes domain closure and negative table entries; that its infinite arithmetic sort is separate from its finite system sort; and that Theorem 3 assumes both nesting and uniform effective enumeration. No proof assistant was used. The transition example illustrates the construction; it is not empirical validation of incompleteness or a model of all physical systems.

This file preserves both the supported thesis and the stronger claims that the present arguments do not establish. Future corrections should identify the affected assertion and its replacement, so that the original research direction remains intelligible.
