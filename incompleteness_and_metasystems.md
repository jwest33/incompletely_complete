**Incompleteness and metasystems: truth, task adequacy, and the limits of effective reasoning**

Research note begun on 17 September 2026; expanded on 18 September 2026. Version 2.0.

Status: mathematical exposition with explicit hypotheses, proofs, examples, and interpretations. The results assemble standard ideas from logic, computability, and verification; their arrangement and descriptive names are for this note. No claim of mathematical novelty or machine-checked verification is made.

**Abstract.** A theory can leave some arithmetic questions unanswered while completely resolving a specified class of operational questions. This note makes that distinction precise. Its central characterization is that, for an effectively presented family of questions about an intended structure, **a sound effective theory can answer every question if and only if the family's truth set is decidable**. One-sided certification has the corresponding weaker condition: the answers of that sign must be computably enumerable. These statements concern the existence of a suitable theory, potentially extending a sound base theory; they do not say that an arbitrary fixed theory already proves every answer.

The examples strengthen this result in two directions. Peano arithmetic can settle every question about any explicitly given finite relational structure encoded inside arithmetic, including unbounded-time reachability in a finite graph. An infinite transition system can also have decidable reachability questions when it admits a supplied, exact finite abstraction. Conversely, general program safety includes true claims that any given sound effective arithmetic theory fails to prove.

The metasystem results identify what stronger frameworks can and cannot achieve. A uniformly effective increasing sequence of consistent arithmetic theories remains incomplete at its union. Allowing retractions goes beyond that union argument, but even a computable process that may revise every answer finitely often cannot eventually answer every arithmetic sentence correctly. Finally, Löb's theorem explains the limits of proving the reliability of one's own proof system from within that same system.

**In everyday language.** A rulebook may answer every question needed to run a particular machine without answering every mathematical question that can be expressed in the rulebook's language. Adding rules can solve old problems. Whether this gives a complete method depends on the questions, on how the new rules are obtained, and on what counts as an answer: a terminating decision, a certificate, or a provisional guess.

Theorems 1–3 preserve the main results of version 1.0. Theorems 4–9 develop the stronger direction. The original motivating claims are retained near the end as an argument record, rather than used to determine the conclusions.

**Definitions and scope.** Work in ordinary classical mathematics, in an ambient metatheory capable of discussing natural numbers, finite strings, and structures; ZFC is one suitable example. This specifies the standpoint of the argument, not a proof that this standpoint is infallible or self-justifying.

A formal theory consists of axioms in a specified language, with a specified proof calculus. Write \(T\vdash\varphi\) when a finite proof of the sentence \(\varphi\) exists from those axioms. Write \(\operatorname{Thm}(T)\) for the set of its provable sentences.

A structure \(\mathcal A\) supplies a domain and interpretations of the language's symbols. Write \(\mathcal A\models\varphi\) when \(\varphi\) is true in that structure, and define

\[
\operatorname{Th}(\mathcal A)
 = \{\varphi:\varphi\text{ is a sentence and }\mathcal A\models\varphi\}.
\]

**Reading the notation.** A sentence is a statement with no free variables. Read \(\neg\varphi\) as “not \(\varphi\),” \(\land\) as “and,” \(\lor\) as “or,” \(\forall\) as “for every,” and \(\exists\) as “there exists.” The symbols \(\to\) and \(\leftrightarrow\) mean “implies” and “if and only if.” Set inclusion \(A\subseteq B\) allows equality; proper inclusion \(A\subsetneq B\) means that \(B\) has something extra. The central distinction is between \(T\vdash\varphi\), a claim about a proof, and \(\mathcal A\models\varphi\), a claim about truth in a specified structure.

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

Here \(\mathbb N\) means the standard natural numbers with their usual arithmetic. Robinson arithmetic \(Q\) is a small, finitely axiomatized theory sufficient to express basic computation and proof coding. Peano arithmetic \(PA\) adds the usual induction scheme. These are particular formal theories, not names for all mathematical truth. When a theorem assumes soundness, the reference structure is stated explicitly.

A set is **computably enumerable**, abbreviated **c.e.**, if an algorithm can list its members, with repetition allowed. Equivalently, membership can be recognized by a procedure that halts on members and may run forever on nonmembers. A set is **decidable** if one algorithm halts on every input and answers membership correctly. Listing successful computations is possible even when deciding that a computation will never succeed is not.

An effective language has computably recognizable finite expressions and effective syntactic operations, such as forming a negation. All languages used below have this property. Even if an axiom set is only c.e., its theorems can be enumerated: enumerate axioms and systematically interleave all finite derivations from the axioms seen so far. Thus the proof searches below do not assume a decision procedure for axiom membership.

**What counts as a metasystem here?** An *object theory* \(T\) is the theory currently being studied. An *extension* \(U\supseteq T\) retains its axioms and adds others, so every \(T\)-proof remains a \(U\)-proof. A *metatheory* \(M\) reasons about \(T\), for example by coding its sentences and proofs and asking whether a contradiction is provable. These roles can overlap: a stronger arithmetic theory can serve as a metatheory for a weaker one. A rule for generating or revising theories is a further object, a process. The term *metasystem* is used for these specified roles, rather than as an additional mathematical property. Each result states whether it concerns an extension, a metatheoretic assertion, or an evolving process.

**A terminology example.** Suppose a controller has three states. “Can state 2 be reached from state 0?” is a task question. “Does this arithmetic proof calculus decide every sentence in its language?” is a question about the calculus. The controller question may have a complete finite solution even when the answer to the calculus question is no. We use *independent of \(T\)* for a sentence with neither a proof nor a refutation in \(T\), and *algorithmically undecidable* for a problem admitting no total correct decision procedure. These are related but different notions.

Use the following standard background result: every consistent, computably axiomatized first-order theory interpreting Robinson arithmetic \(Q\) is syntactically incomplete. This is the Gödel–Rosser form of the first incompleteness theorem. The interpretation requirement concerns arithmetic expressiveness, not system size or an informal notion of complexity. [Moschovakis, *Lecture Notes in Logic*, Theorem 4C.4, printed p. 151](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=155).

**Theorem 1 — An effective description can be a proper part of a complete semantic theory.**

**Plain-language idea.** The truths about an object and the truths derivable from a chosen rulebook need not coincide. For ordinary arithmetic, every sound effective rulebook leaves out some truths, although each omitted truth can individually be added as a new rule.

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

**Example.** Let \(G\) be any true arithmetic sentence that \(PA\) does not prove. Then \(PA+G\) proves \(G\), simply because \(G\) is now an axiom. This is a sound extension in the ambient mathematics, but it still misses other truths. The example separates three questions: whether \(G\) is true, whether a particular theory proves it, and whether we have a justified method for selecting it as a new axiom.

**Theorem 2 — Incompleteness does not transfer automatically to a system's functions.**

**Plain-language idea.** A large rulebook may contain an unfinished arithmetic chapter and a completely settled chapter about a finite machine. An unanswered question in the first chapter does not erase the answers in the second.

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

**Plain-language idea.** Sometimes a description allows several mathematical situations. A question can then be true in one allowed situation and false in another, although it has a definite answer in the intended situation.

Suppose \(T\) is a consistent first-order theory in a countable language and neither \(\varphi\) nor \(\neg\varphi\) is provable in it. Then there are models \(\mathcal B,\mathcal C\) of \(T\) with

\[
\mathcal B\models\varphi,\qquad
\mathcal C\models\neg\varphi.
\]

**Proof.** If \(T+\varphi\) were inconsistent, the deduction theorem would give \(T\vdash\neg\varphi\), contrary to the hypothesis. Similarly, \(T+\neg\varphi\) is consistent. The first-order completeness theorem supplies a model of each. \(\square\) The model-existence result used here is [Moschovakis, Theorem 1I.1, printed p. 38](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=42).

This is another precise version of the partial-description idea. The axioms leave open alternatives that different models settle differently. An intended model, when one is specified, has its own truth value for \(\varphi\); the original axioms do not settle which alternative holds.

**Example.** A graph description may name two distinct vertices \(a,b\) but say nothing about an edge from \(a\) to \(b\). One model includes that edge; another omits it. Neither \(E(a,b)\) nor its negation follows from the description. Adding the missing table entry resolves this particular ambiguity. This elementary example illustrates underdetermination; Gödel's theorem establishes that suitable effective arithmetic theories cannot eliminate every such undecided sentence while remaining consistent.

The word “complete” in the first-order completeness theorem means that every consequence true in all models of given axioms has a formal proof. It does not mean that those axioms decide every sentence. Consequently, this proposition and Gödel incompleteness are compatible.

**Theorem 3 — Effective accumulation of metasystems remains incomplete.**

**Plain-language idea.** If every new rule is generated by one algorithm, collecting all stages still gives an algorithmically enumerable rulebook. Moving to more stages does not remove the hypotheses of incompleteness.

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

**Example: successively asserting consistency.** Start with \(T_0=PA\) and set

\[
T_{n+1}=T_n+\operatorname{Con}(T_n),
\]

where \(\operatorname{Con}(T_n)\) is the standard arithmetic statement that no \(T_n\)-proof of a contradiction exists. Fix the usual effective proof coding at every stage. In the ambient mathematics, \(PA\) is true in \(\mathbb N\); if \(T_n\) is sound, its consistency statement is true, so \(T_{n+1}\) is sound. The codes of these finite extensions and their consistency sentences can be constructed uniformly. Theorem 3 therefore applies. Each next stage settles its predecessor's consistency, while the union still leaves arithmetic questions undecided. Theorem 9 gives the precise self-consistency restriction behind this example.

The same obstruction applies to an adaptive process whenever all of its accepted axioms can ultimately be enumerated by an ordinary algorithm and their accumulated theory is consistent and contains \(Q\). Changing rules, learning, or adding stages does not by itself establish that these hypotheses fail. If revisions retract axioms, the nested-union proof above need not describe the process; a different formal analysis is then required.

Gödel himself noted, in footnote 48a of his original paper, that the undecidable propositions under discussion could become decidable after suitable higher types were added. The historical observation supports the relativity of particular undecidability results to a framework; it does not assert the existence of a final effective complete framework. [Gödel, 1931, Meltzer translation, printed p. 62, footnote 48a](https://homepages.uc.edu/~martinj/History_of_Logic/Godel/Godel%20%E2%80%93%20On%20Formally%20Undecidable%20Propositions%20of%20Principia%20Mathematica%201931.pdf#page=65).

**Theorem 4 — An exact characterization of effective task adequacy.**

**Plain-language idea.** To settle every question in a family with a sound mechanical proof method, the family must admit a mechanical yes-or-no solution. If we only require certificates for yes answers, it is enough to be able to recognize yes instances eventually. This gives a precise boundary between complete decision and one-sided verification.

Fix a structure \(\mathcal A\) in an effective language \(L\), and a c.e. theory \(B\) sound for \(\mathcal A\). Let

\[
q:\mathbb N\longrightarrow\operatorname{Sent}(L)
\]

be a total computable map. The sentence \(q(n)\) is the question with input \(n\). Repetitions are allowed; no algorithm for recognizing the image of \(q\) is assumed. Define its **truth set**

\[
D_q=\{n\in\mathbb N:\mathcal A\models q(n)\}.
\]

Then the following characterizations hold:

| Required property of some sound c.e. extension \(U\supseteq B\) | Necessary and sufficient condition |
| --- | --- |
| For every \(n\in D_q\), \(U\vdash q(n)\) | \(D_q\) is c.e. |
| For every \(n\notin D_q\), \(U\vdash\neg q(n)\) | \(\mathbb N\setminus D_q\) is c.e. |
| For every \(n\), \(U\) proves the true member of \(\{q(n),\neg q(n)\}\) | \(D_q\) is decidable |

Soundness is part of every row. Thus a positive certificate is never issued for a false question, and a negative certificate is never issued for a true one. Different rows initially quantify over possibly different extensions \(U\).

**Proof.** For the first row, suppose a suitable \(U\) exists. On input \(n\), compute \(q(n)\) and enumerate the theorems of \(U\) until that sentence appears. If \(n\in D_q\), the stipulated proof eventually appears. If \(n\notin D_q\), soundness prevents it from appearing. This semidecides \(D_q\), so \(D_q\) is c.e.

Conversely, if \(D_q\) is c.e., enumerate it and adjoin \(q(n)\) each time \(n\) appears:

\[
U=B+\{q(n):n\in D_q\}.
\]

Its axioms are c.e. because both enumerations and \(q\) are effective. Every added axiom is true in \(\mathcal A\); therefore \(U\) is sound. It proves every required positive answer. This establishes the first row. Apply the same argument to \(n\mapsto\neg q(n)\) to obtain the second.

For the third row, suppose \(U\) supplies the correct answer for every input. Enumerate its theorems, watching for both \(q(n)\) and \(\neg q(n)\). Adequacy ensures that one appears; soundness ensures that its sign gives the correct answer. This is a total decision procedure for \(D_q\).

Conversely, if \(D_q\) has a decision procedure, compute the correct sign for each \(n\) and take

\[
U=B+\{q(n):n\in D_q\}
    +\{\neg q(n):n\notin D_q\}.
\]

This is a sound c.e. extension with all the required proofs. Equivalently, the first two rows can be combined: a set and its complement are both c.e. exactly when the set is decidable. To prove that last fact directly, run their recognition procedures in parallel until one accepts. \(\square\)

**What is constructive here?** Given a program enumerating \(B\), a program for \(q\), and the indicated decision or enumeration program, the displayed construction effectively produces an axiom enumerator for \(U\). Given an adequate sound theorem enumerator, the proof effectively produces the corresponding solver. It does not produce such programs from a bare semantic assertion that a structure has definite answers.

**Example: a family of bounded searches.** Let \(q(n)\) say that an input graph contains a path of length at most the input bound; encode the graph, endpoints, and bound in \(n\). A finite search decides each question, so a sound effective theory adequate for this entire family exists. There are infinitely many inputs, and their sizes need not have a common bound. What matters is that each input supplies a finite search problem with an effective stopping rule.

**Example: finding a successful run.** Let \(q(n)\) say that program \(n\) eventually halts on empty input. Simulating the program recognizes every yes instance, so the positive answers are c.e. The negative answers are not c.e.; Theorem 6 proves the obstruction. Every successful run can be certified, but there is no sound effective proof method that certifies every nonhalting run as well.

**Corollary 4.1 — Complete task coverage can coexist with arithmetic incompleteness.** If \(B\) is a sound c.e. extension of \(Q\) in the arithmetic language and \(D_q\) is decidable, the extension \(U\) in the third row is adequate for the entire task family and is nevertheless syntactically incomplete, by Gödel–Rosser.

**The quantifier matters.** Theorem 4 asserts the existence of *some* suitable extension. A preselected theory can miss a decidable family. For example, if \(\psi\) is true but unprovable in \(B\), the constant query family \(q(n)=\psi\) has the decidable truth set \(\mathbb N\), but \(B\) answers none of its instances. The sound extension \(B+\psi\) does. Knowing externally that a solver exists is different from identifying the correct solver or proving its correctness within \(B\).

**Theorem 5 — Operational completeness inside arithmetic itself.**

**Plain-language idea.** The separation in Theorem 2 is not necessary. Ordinary arithmetic can directly encode a finite machine and prove the correct answer to every question in its finite-state query language, while remaining incomplete about arithmetic as a whole.

For each explicitly given nonempty finite relational structure \(\mathcal A\) with \(n\) elements, there is a computable translation \(\varphi\mapsto\varphi^{\mathcal A}\) from its first-order sentences to arithmetic sentences such that:

1. \(\mathcal A\models\varphi\) if and only if \(\mathbb N\models\varphi^{\mathcal A}\).
2. \(PA\) proves \(\varphi^{\mathcal A}\) if it is true, and proves its negation if it is false.
3. A single algorithm, given the finite tables and \(\varphi\), returns the correct sign and a \(PA\)-proof of that signed translation.
4. For any fixed finite directed graph \(G\) and vertices \(s,t\), \(PA\) likewise proves the correct answer to the standard arithmetic assertion that a finite path of any length exists from \(s\) to \(t\).

Nevertheless, \(PA\) is incomplete in the ambient mathematics, where \(\mathbb N\models PA\).

**Proof of parts 1–3.** Number the elements \(0,\ldots,n-1\), using \(\bar i\) for the arithmetic numeral denoting \(i\). Replace a relation symbol \(R\) by the finite table formula

\[
R^{\mathcal A}(x_1,\ldots,x_k)
=\bigvee_{(i_1,\ldots,i_k)\in R^{\mathcal A}}
  (x_1=\bar i_1\land\cdots\land x_k=\bar i_k).
\]

The superscript on the right refers to the relation's table; the left denotes its defining arithmetic formula. An empty disjunction is false and an empty conjunction is true; this also handles relations of arity zero. Translate constants to their numerals, preserve equality and Boolean connectives, and restrict quantifiers to the numbered domain:

\[
(\exists x\,\eta)^{\mathcal A}
 =\exists x<\bar n\,\eta^{\mathcal A},
\qquad
(\forall x\,\eta)^{\mathcal A}
 =\forall x<\bar n\,\eta^{\mathcal A}.
\]

Here \(\exists x<t\,\eta\) abbreviates \(\exists x(x<t\land\eta)\), and \(\forall x<t\,\eta\) abbreviates \(\forall x(x<t\to\eta)\). Induction on the original formula proves part 1, including formulas evaluated under assignments in the finite domain.

For every particular natural number \(n\), \(PA\) proves

\[
\forall x\bigl(x<\bar n\leftrightarrow
 (x=\bar0\lor\cdots\lor x=\overline{n-1})\bigr).
\]

Each restricted quantifier can therefore be expanded into a finite disjunction or conjunction. Ground arithmetic equalities can be calculated and proved or refuted in \(PA\). Recursively combining these derivations gives a proof of the true sign of the whole sentence. All steps are effective in the tables and syntax, proving parts 2 and 3.

This is an instance of the more general fact that \(PA\) decides every **closed bounded arithmetic formula**: each quantifier is restricted by an arithmetic term not containing its bound variable. Such formulas are often called \(\Delta_0\) formulas. Once outer variables receive numerical values, each inner bound is a particular finite number, so the same recursive evaluation and proof construction apply.

**Proof of part 4.** Use a standard arithmetic coding of finite sequences to express \(\operatorname{Reach}_G(\bar s,\bar t)\): there exists a code for a finite sequence beginning at \(s\), ending at \(t\), and obeying the graph's table at each step. Paths of length zero are allowed. The finite-sequence operations have their usual representations in \(PA\); one may use their conservative definitional extensions as notation.

If \(t\) is reachable, a particular path supplies a code. Its finite verification yields a \(PA\)-proof of reachability.

If \(t\) is not reachable, compute the finite set \(R_s\) of all vertices reachable from \(s\), and define

\[
I_s(x)=\bigvee_{v\in R_s}x=\bar v.
\]

The table calculations yield \(PA\)-proofs that \(I_s(\bar s)\), that \(\neg I_s(\bar t)\), and that

\[
\forall x\forall y\,
 \bigl(I_s(x)\land E_G(x,y)\to I_s(y)\bigr).
\]

The last sentence is provable by finite case analysis using the disjunctive definitions of \(I_s\) and \(E_G\). Induction on position in any coded finite path then proves that every vertex on a path from \(s\) satisfies \(I_s\). No such path can end at \(t\). This constructs a \(PA\)-proof of \(\neg\operatorname{Reach}_G(\bar s,\bar t)\).

The construction is effective: graph traversal supplies either a path or the finite invariant \(I_s\), and both certificates can be translated into proofs. Incompleteness of \(PA\) follows from its soundness and Gödel–Rosser. \(\square\)

**Worked example.** Number the earlier graph's states \(0,1,2\), with edges \(0\to1\), \(1\to2\), and \(2\to2\). Its arithmetic edge formula is

\[
E_G(x,y)\equiv
(x=0\land y=1)\lor(x=1\land y=2)\lor(x=2\land y=2).
\]

The formula \(\exists y<3\,(E_G(0,y)\land E_G(y,2))\) has witness \(1\). The formula \(\exists y<3\,(E_G(2,y)\land y\ne2)\) is false. Both answers have arithmetic proofs. For the unbounded question “Can 0 ever be reached from 2?”, use the invariant \(I_2(x)\equiv x=2\): it holds initially and every transition preserves it. Induction proves that any number of transitions still leaves the machine at 2.

The invariant is a fact that remains true after each step. Its role is to turn infinitely many possible run lengths into one finite proof. This is stronger than simulating the machine for a chosen number of steps and observing no failure.

**Scope.** “Every question” here means every translated first-order sentence about the supplied finite structure, together with the stated reachability queries. It does not include arbitrary arithmetic sentences merely mentioning a graph code. A sentence such as “this graph has three vertices and \(\psi\)” can inherit the difficulty of an unrelated arithmetic \(\psi\). Nor does an algorithm for producing proofs guarantee small proofs or practical running times.

**Theorem 6 — General program safety exceeds every sound effective arithmetic verifier.**

**Plain-language idea.** A completed computation leaves a finite record that can be checked. A computation that never finishes leaves no final record. This asymmetry becomes an impossibility theorem when the task covers arbitrary programs with unbounded memory.

Fix an effective enumeration \(M_0,M_1,\ldots\) of programs in a universal model of computation, and an effective encoding of pairs \((e,x)\) by natural numbers. Let

\[
H=\{(e,x):M_e\text{ halts on input }x\}.
\]

Use the standard arithmetic sentence \(\operatorname{Halt}(\bar e,\bar x)\) asserting the existence of a coded halting computation. Then:

1. \(H\) is c.e. and undecidable, and its complement is not c.e.
2. \(PA\) proves every true sentence \(\operatorname{Halt}(\bar e,\bar x)\).
3. Every sound c.e. extension \(T\supseteq PA\) fails to prove \(\neg\operatorname{Halt}(\bar e,\bar x)\) for infinitely many nonhalting pairs \((e,x)\). For each such pair, neither sign of its halting sentence is provable in \(T\).
4. There is no algorithm that, for every program and input, correctly decides whether a designated bad state is ever reached. Every sound c.e. extension of \(PA\) also misses true safety assertions in this family.

**Proof.** Simulation semidecides \(H\). Suppose a total decider \(h(e,x)\) for \(H\) existed, returning 1 for halting and 0 for nonhalting. Construct a program \(D\) which, on input \(z\), loops forever if \(h(z,z)=1\) and halts if \(h(z,z)=0\). Let \(d\) be its program index. Applied to \((d,d)\), the decider says that \(D(d)\) halts exactly when the definition makes it not halt, a contradiction. If the complement of \(H\) were c.e., dovetailing its recognizer with the one for \(H\) would decide \(H\). This proves part 1.

A halting computation has a particular finite trace. The standard coding permits \(PA\) to verify each step of that trace and then introduce the existential quantifier asserting its existence. This is the same finite-calculation principle used in Theorem 5 and proves part 2. In usual terminology these halting assertions are \(\Sigma_1\) sentences: they assert that a finite certificate exists, with an effectively checkable arithmetic description.

For part 3, let

\[
P_T=\{(e,x):T\vdash\neg\operatorname{Halt}(\bar e,\bar x)\}.
\]

This set is c.e. by theorem enumeration. Soundness gives \(P_T\subseteq\overline H\). If \(\overline H\setminus P_T\) were finite, adjoining those finitely many pairs to an enumeration of \(P_T\) would enumerate \(\overline H\), contradicting part 1. Thus infinitely many true nonhalting assertions are unprovable. Their positive halting assertions are false, so soundness prevents proofs of those as well. The finite-set argument is an existence argument; it does not presume that we can identify the missing pairs.

For part 4, transform any pair \((e,x)\) into a program \(W_{e,x}\) that simulates \(M_e(x)\) and enters a designated bad state exactly if the simulation halts. The transformation is computable and

\[
W_{e,x}\text{ reaches bad}\quad\Longleftrightarrow\quad(e,x)\in H.
\]

A general reachability or safety decider would therefore decide \(H\). With the usual coding, \(PA\) proves this equivalence for the constructed simulator. A \(T\)-proof that \(W_{e,x}\) never reaches bad would give a \(T\)-proof of the corresponding nonhalting assertion. Part 3 supplies pairs for which no such proof exists. \(\square\)

**A concrete interpretation.** Consider a monitor whose failure flag is initially off and is switched on only after a simulated program halts. A failure can be demonstrated by showing the finite simulation that switches the flag. For some monitors the flag never switches, yet a chosen sound effective theory has no proof that it never switches. This is a limitation on general certification, not a claim that the monitor eventually fails.

Theorem 5 and Theorem 6 concern different inputs. In Theorem 5 the complete finite state table is supplied. In Theorem 6 a finite program description may generate infinitely many configurations through unbounded memory. Finite source code does not imply a finite state space. If all relevant memory and environment states really are bounded and explicitly modeled, finite-state reasoning applies again, with whatever computational costs that model entails.

These proofs are the standard computability ingredients behind the task boundary; see [Moschovakis, Chapter 3, on computation and undecidability](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf). Their application here concerns the specified halting and safety queries, not an assertion about all useful programs.

**Theorem 7 — A supplied exact finite abstraction can settle questions about an infinite system.**

**Plain-language idea.** A system can have infinitely many detailed states but only finitely many distinctions relevant to a task. A finite summary suffices when it preserves the possible transitions at that level of observation. Forgetting details is justified only after checking that preservation condition.

Let \((X,\to)\) be a transition system, possibly infinite. Let \((F,\Rightarrow)\) be a nonempty finite directed graph, and let \(\alpha:X\to F\) be a surjective observation map. Assume:

1. **Forward preservation:** if \(x\to y\), then \(\alpha(x)\Rightarrow\alpha(y)\).
2. **Lifting:** for every \(x\in X\) and \(b\in F\), if \(\alpha(x)\Rightarrow b\), there is \(y\in X\) such that \(x\to y\) and \(\alpha(y)=b\).

For any \(C\subseteq F\), let the concrete target be \(B=\alpha^{-1}(C)\). Then, for every initial state \(x_0\),

\[
\exists y\in B\;(x_0\to^{*}y)
\quad\Longleftrightarrow\quad
\exists b\in C\;(\alpha(x_0)\Rightarrow^{*}b),
\]

where \(\to^{*}\) and \(\Rightarrow^{*}\) mean reachability by finitely many steps, including zero. If states have effective encodings, \(\alpha\) is computable, and the finite tables of \(F\) and \(C\) are supplied, this task is decidable uniformly from the initial state and those tables, subject to the two stated conditions.

**Proof.** A concrete finite path maps to an abstract path by forward preservation. If its endpoint is in \(B\), its abstract endpoint lies in \(C\).

Conversely, suppose an abstract path starts at \(\alpha(x_0)\) and ends in \(C\). At each step, lifting supplies a concrete successor with the required next observation. Induction on the finite path length constructs a concrete path from \(x_0\) whose last observation is in \(C\); its last state is therefore in \(B\). This proves the equivalence. Compute \(\alpha(x_0)\) and search the finite graph to decide its right side. \(\square\)

**Worked example: an unbounded counter.** Let \(X=\mathbb N\) with the sole transition \(n\to n+2\). Observe only parity:

\[
\alpha(n)=
\begin{cases}
\mathrm{even},&n\text{ is even},\\
\mathrm{odd},&n\text{ is odd}.
\end{cases}
\]

The finite graph has two vertices and exactly the self-loops \(\mathrm{even}\Rightarrow\mathrm{even}\) and \(\mathrm{odd}\Rightarrow\mathrm{odd}\). Forward preservation holds because adding 2 preserves parity. Lifting holds because every concrete number has its \(+2\) successor. Starting at 2, no odd state is reachable. The counter has infinitely many reachable concrete states, but this safety question is completely resolved by a two-state graph.

The target must respect the observation. “Reach an odd number” does; “reach exactly 0” does not, because parity groups 0 with other even numbers. Indeed, from 2 the counter can reach an even number but cannot reach 0. The theorem gives completeness for the chosen observation-based tasks, not for every question about the counter.

**Why lifting cannot simply be dropped.** Take concrete states \(s,u,v,b\) and exactly two edges \(s\to u\) and \(v\to b\). Give \(s\) observation \(A\), both \(u,v\) observation \(M\), and \(b\) observation \(Z\). An abstract graph with edges \(A\Rightarrow M\) and \(M\Rightarrow Z\) preserves every concrete edge. It also has a path from \(A\) to \(Z\), although \(b\) is unreachable from \(s\): the actual intermediate state is \(u\), which has no successor. Lifting fails at \(u\). The abstraction has joined two steps that cannot occur consecutively in a concrete run.

With forward preservation alone, abstract unreachability still proves concrete unreachability. An abstract path may be spurious, as this example shows. With lifting as well, both answers are exact. The possibility of spurious errors in an overapproximation is a standard issue in verification. [Fredrikson and Platzer, *Lecture Notes on Software Model Checking*, §§1 and 5](https://www.cs.cmu.edu/~15414/f17/lectures/19-software.pdf).

**Where the work remains.** The theorem assumes a correct abstraction; it supplies no universal algorithm for discovering one or verifying lifting for arbitrary infinite systems. A method guaranteed to produce a valid exact finite abstraction with computable observations for every program-safety instance would yield the decider forbidden by Theorem 6. A finite abstraction is one sufficient route to a decidable task, not a necessary description of every decidable infinite-state problem. If the concrete reachability questions are effectively translated into arithmetic sentences, Theorem 4 also supplies a sound effective theory adequate for this task family. Getting the relevant abstraction proof inside a particular fixed theory is a further question.

**Theorem 8 — Retractions do not allow eventual correctness on all arithmetic.**

**Plain-language idea.** An evolving system might withdraw old answers instead of accumulating axioms forever. That falls outside Theorem 3. It can be more capable than a terminating decision procedure, but even unrestricted computable revision cannot eventually settle on the right answer to every arithmetic question.

Let \(\ulcorner\varphi\urcorner\) denote the natural-number code of an arithmetic sentence. There is no total computable function

\[
g:\mathbb N\times\mathbb N\longrightarrow\{0,1\}
\]

such that, for every arithmetic sentence \(\varphi\), there exists a stage \(S_\varphi\) for which

\[
\forall s\ge S_\varphi,\qquad
g(\ulcorner\varphi\urcorner,s)=
\begin{cases}
1,&\mathbb N\models\varphi,\\
0,&\mathbb N\not\models\varphi.
\end{cases}
\]

No computable bound on \(S_\varphi\) is being demanded. No requirement of consistency or correctness at earlier stages is being imposed. The claim rules out even this weak eventual guarantee for all arithmetic sentences.

**Background lemma: arithmetic can refer to its own sentence codes.** For every arithmetic formula \(F(v)\) with one free variable, the diagonal lemma supplies a sentence \(\delta\) such that

\[
PA\vdash\delta\leftrightarrow F(\ulcorner\delta\urcorner).
\]

Inside a formula, the corner notation means the numeral for the code. The construction uses the effective operation that substitutes a formula's own code into its free variable; representing that syntactic operation in arithmetic yields the fixed point. This is a precise syntactic construction, not an assumption that arithmetic contains a truth predicate. [Moschovakis, Theorem 4B.14, printed p. 149](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf#page=153).

**Proof of Theorem 8.** Suppose such a computable \(g\) exists. Computations have arithmetic descriptions, so let \(O_g(e,s,0)\) be an arithmetic formula true in \(\mathbb N\) exactly when the algorithm for \(g\), on input \((e,s)\), returns 0. Define

\[
F(e)\equiv\exists N\,\forall s\ge N\;O_g(e,s,0).
\]

This says that the answers for the sentence with code \(e\) are eventually always 0. The diagonal lemma gives a sentence \(\delta\) satisfying

\[
\mathbb N\models\delta
\quad\Longleftrightarrow\quad
\exists N\,\forall s\ge N\;
g(\ulcorner\delta\urcorner,s)=0.
\]

The assumed eventual correctness gives

\[
\exists N\,\forall s\ge N\;
g(\ulcorner\delta\urcorner,s)=0
\quad\Longleftrightarrow\quad
\mathbb N\not\models\delta.
\]

Together these say that \(\delta\) is true exactly when it is false, a contradiction. \(\square\)

**Reading the diagonal sentence.** Its content is: “This particular answer process eventually keeps calling this sentence false.” If the process settles on false, the sentence correctly describes that behavior and is true. If the process settles on true, it does not eventually keep calling the sentence false, so the sentence is false. Its reference is to a particular computable process, whose behavior arithmetic can describe.

**Example showing that revision still helps.** For a halting question, output 0 until a halting computation has been observed, then output 1 forever:

\[
g_H(\langle e,x\rangle,s)=
\begin{cases}
1,&M_e(x)\text{ halts within }s\text{ steps},\\
0,&\text{otherwise}.
\end{cases}
\]

This is computable. If the program halts, the answer eventually becomes 1; if it never halts, the answer stays 0. Thus every halting question receives an eventually correct answer, despite there being no terminating halting decider. The price is that a current 0 gives no general certificate that it will remain 0. A computable bound on the stabilization stage for every input would turn this procedure into a halting decider, contradicting Theorem 6.

The distinction is between eventual truth and recognizable completion. Theorem 8 says that even eventual truth for all arithmetic is too much to ask of one computable answer process. It concerns the explicit input/output guarantee above; systems with external information not generated by an ordinary algorithm require separate hypotheses. A deterministic learning or rule-revision process with computable data and computation is covered whenever it supplies answers in this form.

**Theorem 9 — Löb's theorem and the boundary of internal self-certification.**

**Plain-language idea.** A theory can check particular proofs and justify particular claims. Establishing within the theory a general rule that its own provability guarantees a given claim is more demanding. Löb's theorem identifies the exact restriction for each sentence.

Let \(T\) be a c.e. extension of \(PA\), and fix its standard arithmetized provability predicate. Write

\[
\Box\varphi
\quad\text{for}\quad
\operatorname{Prov}_T(\ulcorner\varphi\urcorner).
\]

This is an arithmetic sentence saying that a \(T\)-proof of \(\varphi\) exists. Use a conventional proof coding satisfying the following derivability conditions, for sentences \(\alpha,\beta\):

1. If \(T\vdash\alpha\), then \(T\vdash\Box\alpha\).
2. \(T\vdash\Box(\alpha\to\beta)\to(\Box\alpha\to\Box\beta)\).
3. \(T\vdash\Box\alpha\to\Box\Box\alpha\).

The first is a rule about actual proofs. The second formalizes combining a proof of an implication with a proof of its premise. The third formalizes that a proof's existence is itself provable when the proof is available. These conditions concern the specified proof predicate; an arbitrary formula informally called “provable” is not enough. Standard proof coding for c.e. arithmetic theories can include finite enumeration certificates for the axioms used.

For every arithmetic sentence \(\varphi\),

\[
T\vdash(\Box\varphi\to\varphi)
\quad\Longleftrightarrow\quad
T\vdash\varphi.
\]

The forward implication is Löb's theorem. The reverse implication is ordinary propositional reasoning. See [MIT OpenCourseWare, *The Logic of Provability*, pp. 1–2](https://ocw.mit.edu/courses/24-242-logic-ii-spring-2004/a1710eb936dcfe137dc5e5e0ad61b4f1_provablity_logic.pdf).

**Proof.** Assume \(T\vdash\Box\varphi\to\varphi\). The diagonal lemma supplies a sentence \(\delta\) such that

\[
T\vdash\delta\leftrightarrow(\Box\delta\to\varphi).
\]

All implications in the following calculation are derivable in \(T\). From the forward direction of this equivalence, conditions 1 and 2 give

\[
\Box\delta\to\Box(\Box\delta\to\varphi).
\]

Condition 2, with \(\alpha=\Box\delta\) and \(\beta=\varphi\), gives

\[
\Box(\Box\delta\to\varphi)
\to(\Box\Box\delta\to\Box\varphi).
\]

Condition 3 gives \(\Box\delta\to\Box\Box\delta\). Combining these three implications yields

\[
T\vdash\Box\delta\to\Box\varphi.
\]

Our assumption now yields \(T\vdash\Box\delta\to\varphi\). The reverse direction of the fixed-point equivalence gives \(T\vdash\delta\). Condition 1 therefore gives \(T\vdash\Box\delta\), and the already derived implication gives \(T\vdash\varphi\). Conversely, from a proof of \(\varphi\), propositional logic gives a proof of \(\Box\varphi\to\varphi\). \(\square\)

**Corollary 9.1 — Second incompleteness under the stated hypotheses.** Put \(\bot\equiv(0=1)\), and define

\[
\operatorname{Con}(T)\equiv\neg\Box\bot.
\]

If \(T\) is consistent, then \(T\nvdash\operatorname{Con}(T)\). Otherwise \(T\) would prove \(\Box\bot\to\bot\); Löb's theorem would make it prove \(\bot\), contrary to consistency. Soundness is not needed for this corollary: consistency and the stated syntactic hypotheses suffice.

**Example: a program that searches for a contradiction.** Build \(P_T\) to enumerate \(T\)'s proofs and halt when a proof of \(0=1\) appears. If \(T\) is consistent, this program never halts. With the standard coding, \(PA\) proves that its nonhalting is equivalent to \(\operatorname{Con}(T)\). Consequently \(T\) cannot prove this particular nonhalting fact about \(P_T\). Here the missing safety assertion has an explicit construction from the verifier itself.

If \(T\) is sound, the extension \(T+\operatorname{Con}(T)\) is sound and can prove that \(P_T\) never halts. Its own contradiction-search program raises the next consistency question. This gives concrete meaning to the hierarchy in Theorem 3.

**What the self-certification result means.** It concerns the theory's own standard provability predicate and proofs inside that same theory. It does not prevent external proofs of consistency, proofs about weaker proof systems, verification of individual proof objects, or restricted reliability results. For an unproved sentence \(\varphi\), one cannot obtain a new \(T\)-proof merely by first proving in \(T\) that “if \(T\) proves \(\varphi\), then \(\varphi\).” Löb's theorem says that establishing this implication already suffices for a proof of \(\varphi\).

**Synthesis: a specification determines the relevant limit.**

The strongest conclusion of this note is the task characterization in Theorem 4, together with the examples and obstructions that make its hypotheses meaningful:

> For an effectively indexed family of sentences about an intended structure, a sound effective extension of a sound effective base theory can supply every correct answer exactly when the family's truth set is decidable. One-sided complete certification corresponds to computable enumerability of the answers of that sign. This task adequacy can coexist with arithmetic incompleteness. Neither uniformly effective accumulation of consistent arithmetic theories nor computable revision of provisional answers yields complete access to arithmetic truth.

The following comparisons keep the guarantees separate:

| Task or method | What is available | What is not supplied |
| --- | --- | --- |
| First-order queries on a supplied finite structure | A correct decision and arithmetic proof for each query | An efficient procedure for every structure and formula size |
| Unbounded-time reachability in a supplied finite graph | A path certificate or a finite invariant excluding the target | Correctness of an unverified physical model |
| Observation-based reachability with a supplied exact finite abstraction | A decision even for some infinite-state systems | Automatic discovery of such an abstraction for arbitrary programs |
| Halting of an arbitrary program | A certificate for every actual halting run | A terminating correct yes-or-no answer on every input |
| Nonhalting of an arbitrary program | Sound proofs for some cases, including many useful invariants | Complete sound effective certification of every safe case |
| Provisional answers to halting questions | Eventual correctness by revising 0 to 1 when a run halts | A general signal that a current 0 is final |
| Provisional answers to all arithmetic sentences | No computable process has the stipulated eventual guarantee | Universal arithmetic truth even with unbounded revision time |
| Adding \(\operatorname{Con}(T)\) to a sound arithmetic theory \(T\) | A sound extension settling a particular earlier limitation | A final effective arithmetic theory proving its own consistency |

**Example of using the framework.** For a controller, first specify whether a task is “avoid an error in this supplied finite model,” “avoid an error for every memory size,” or “decide safety of arbitrary controller programs.” The first has the construction of Theorem 5. A suitable abstraction may settle a particular instance of the second by Theorem 7. A family of the third kind can contain the reduction in Theorem 6. The word *controller* does not determine the logical difficulty; the model, query family, and quantifiers do.

**Relation to the original motivating thesis.**

> For any effective arithmetic theory \(T\) extending \(Q\) and sound for \(\mathbb N\), its provable content is a proper part of the complete semantic theory \(\operatorname{Th}(\mathbb N)\). This limitation of the description does not entail failure on every specified task: there exist consistent effective incomplete theories that completely and decidably describe a finite operational domain. Stronger frameworks can settle particular earlier questions, while any consistent effective accumulation retaining sufficient arithmetic remains incomplete.

Theorem 1 supplies the first sentence, Theorem 2 supplies the second, and Theorem 3 supplies the limitation in the third. This is a statement about the scope and consequences of incompleteness.

“A metasystem partially constitutes its object” can mean that a chosen language and axiom set determine what is expressible and derivable in a representation. That interpretation is consistent with these results. If it instead means that an external observer causes an otherwise complete effective arithmetic calculus to become incomplete, no such conclusion follows.

In particular, changing notation or recoding proofs cannot remove the obstruction while preserving the hypotheses. The arithmetic theory can encode its own finite proof syntax. A metatheory is where we establish the incompleteness result, but being studied from outside is not an extra defect in the object theory.

Nor does semantic completeness establish metaphysical wholeness. \(\operatorname{Th}(\mathcal A)\) comprises truths in one chosen language about one chosen structure. Additional languages, physical interpretation, and experimental adequacy remain separate questions.

Theorem 9 makes the self-certification restriction precise. Moving a consistency argument to a stronger metatheory changes the proving framework and its assumptions. It can settle an earlier consistency question without supplying unconditional self-certification.

**Preserved candidate arguments and their disposition.**

The original request sought an argument that incompleteness was not functionally valid or applied only to systems partially constituted by metasystems. Version 1.0 separated the supported mathematical claims from the stronger proposed interpretations. The following record preserves that distinction; the results above now organize the investigation around task adequacy, verification, and effective reasoning.

| Candidate claim | Assessment | What can be retained |
| --- | --- | --- |
| “A metasystem proves a sentence that the original system cannot, so the incompleteness theorem is false.” | Invalid inference: provability in two different theories has been conflated. | Particular undecidability is relative to the specified theory. |
| “A complete semantic theory exists, so Gödel's theorem has a counterexample.” | Invalid as a refutation: true arithmetic fails effective axiomatizability. | Completeness and effectiveness are distinct requirements. |
| “Keep adding each missing truth; the resulting effective system will be complete.” | The effectiveness claim is unsupported. Theorem 3 excludes a consistent effective complete union extending \(Q\). | An externally truth-selected union can be complete, at the cost of a non-effective selection process. |
| “Allowing revisions will eventually give correct answers to all arithmetic questions.” | False for the computable answer process specified in Theorem 8. | Some undecidable query families, including halting, do admit eventual correct guesses without a recognizable stopping point. |
| “Complex systems cannot be represented by fixed theories.” | Unproved and too broad; neither “complex” nor “represented” has been specified. | Whether a particular representation meets the incompleteness hypotheses must be checked. |
| “An incomplete theory cannot correctly operate or analyze a system.” | False as a universal statement, by Theorem 2 and its finite graph example. | Some tasks may still encode genuinely undecidable problems. |
| “Finite systems are fully understood in practice.” | Too strong: decidability does not guarantee feasible computation, a known transition table, or an accurate physical model. | A specified finite relational structure has the complete finite description constructed above. |
| “An infinite state space makes every operational task undecidable.” | False: Theorem 7 gives infinite-state systems with exact finite answers to observation-based reachability questions. | The task's observable distinctions and dynamics matter, alongside the number of states. |
| “The unknown truth value means reality itself is incomplete.” | This moves from a proof-theoretic property to an undefined ontological property. | An axiom system can underdetermine which model is intended. |
| “These examples show that incompleteness is generally unrepresentative of complex systems.” | Not established: no class of complex systems, distribution, or prevalence criterion was supplied. | They disprove an unrestricted inference from complexity or functional usefulness alone to incompleteness. |

A finite workload also cannot establish universal completeness. If \(F\) is a finite collection of arithmetic questions and \(T\) is sound, adjoining the correct answer to each question produces a sound effective theory adequate for \(F\). But identifying those correct answers may be unavailable, and the resulting theory is still incomplete if it extends \(Q\). This is an existence observation, not an algorithm for solving arbitrary finite lists of hard problems.

**Further mathematical directions.** The next useful strengthening is to add resource bounds to task adequacy. Theorem 4 guarantees termination when a truth set is decidable, but gives no useful bound on proof length, proof-search time, or memory. A sharper analysis would fix a representation and compare the cost of deciding a query with the cost of producing and checking a proof of its answer.

A second direction is abstraction discovery for restricted program classes. Theorem 7 gives explicit conditions to aim for. One can study algorithms that find a suitable abstraction whenever a program belongs to a specified class, or procedures that may fail to finish outside that class. Theorem 6 rules out universal success across arbitrary programs; it leaves substantial room for results about particular languages, dynamics, and observation schemes.

A third direction is composition: when separately verified components interact, determine which interface assumptions preserve the combined safety property. The disjoint combination in Theorem 2 is a base case. Coupled components require a proof that each component maintains the assumptions used by the others. This would turn the informal phrase “system as a whole” into a defined mathematical question about an explicit composition operation.

**Source and verification record.** The arguments above are mathematical derivations and explanatory constructions, not quotations or claims of novel published research. The original background sources were checked on 17 September 2026 and revisited during the expansion on 18 September 2026. Sources for the added material were consulted on 18 September 2026:

- Kurt Gödel, “Über formal unentscheidbare Sätze der Principia Mathematica und verwandter Systeme I” (1931), consulted in B. Meltzer's English translation, *On Formally Undecidable Propositions of Principia Mathematica and Related Systems*. Relevant locations: Proposition VI, printed p. 57; generalization and footnote 48a, printed p. 62. Gödel's original formulation uses stronger consistency assumptions than the later Rosser version used here. [University of Cincinnati hosted translation](https://homepages.uc.edu/~martinj/History_of_Logic/Godel/Godel%20%E2%80%93%20On%20Formally%20Undecidable%20Propositions%20of%20Principia%20Mathematica%201931.pdf).
- Yiannis N. Moschovakis, *Lecture Notes in Logic*, dated 29 March 2014. Relevant locations: Theorem 1I.1 on first-order completeness, printed p. 38; Chapter 3 on computability; Theorems 4A.4–4A.5 on semantic diagonalization and undefinability of arithmetic truth; Theorem 4B.14 on the syntactic fixed-point lemma, printed p. 149; and Theorem 4C.4 on Gödel–Rosser incompleteness, printed p. 151. The posted document labels itself informal notes; it is used for its explicit theorem statements and proofs. [Author's UCLA notes](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf).
- Matt Fredrikson and André Platzer, *Lecture Notes on Software Model Checking*, Carnegie Mellon University, 15-414, Fall 2017, Lecture 19. Sections 1 and 5 explain finite approximations of infinite program state spaces and the possibility of spurious errors in an overapproximation. The exact lifting condition and its reachability proof are stated explicitly in Theorem 7 here. [Course notes](https://www.cs.cmu.edu/~15414/f17/lectures/19-software.pdf).
- MIT OpenCourseWare, *The Logic of Provability*, 24.242 Logic II, Spring 2004, pp. 1–2. Used for the arithmetic provability setting and Löb's principle. Theorem 9 writes out the derivation from the fixed-point lemma and the three specified derivability conditions. [Course notes](https://ocw.mit.edu/courses/24-242-logic-ii-spring-2004/a1710eb936dcfe137dc5e5e0ad61b4f1_provablity_logic.pdf).

The proof review tracked the assumptions on which the conclusions depend:

- Theorems 1–3 retain soundness for statements about intended arithmetic truth, domain closure and negative table entries for finite descriptions, and uniform enumeration and nesting for the union argument.
- Theorem 4 quantifies over suitable extensions, uses an effective query map, and requires soundness to identify provable answers with true answers.
- Theorem 5 bounds the finite-domain quantifiers and uses induction with an explicit finite invariant for unbounded path lengths.
- Theorem 6 distinguishes finite source code from finite state space and uses soundness when excluding false halting proofs.
- Theorem 7 requires lifting for exactness and restricts its targets to unions of observation classes; forward preservation alone supports only the stated one-sided safety inference.
- Theorem 8 uses arithmetic definability of a computable process and the diagonal lemma. It assumes eventual correctness for every arithmetic sentence, not a uniform stabilization time.
- Theorem 9 specifies the provability predicate and its derivability conditions. Consistency suffices for the second-incompleteness corollary; soundness is used separately when asserting that extensions have true axioms.

No proof assistant was used. The graph and counter examples illustrate the constructions; they are not empirical validation of incompleteness or models of all physical systems. Theorems 4–8 are presented as consequences and constructions using standard mathematical ingredients, and Theorem 9 is the classical theorem explicitly named there.

**Revision record.** Version 2.0 retains Theorems 1–3 and their argument history, adds Theorems 4–9 with worked examples, and replaces the original emphasis on refutation with an exact account of task adequacy and its limits. It also distinguishes finite-state reasoning inside arithmetic, one-sided certification, exact abstraction, revisable answers, and internal reflection. Future corrections should identify the affected assertion and its replacement.
