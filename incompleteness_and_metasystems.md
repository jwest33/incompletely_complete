**Incompleteness, language, and mathematical practice: what makes a formal limit matter?**

Research note begun on 17 September 2026. Version 3.1, 18 September 2026.

**Purpose.** The question guiding this investigation is whether Gödel incompleteness tells us something consequential about mathematics as a communicated, interpreted, and developing practice. Establishing the theorem's validity, or listing compatible successes of incomplete theories, does not by itself answer that question.

The earlier draft developed nine useful formal results but changed the direction of the investigation. Those results are preserved in the [technical companion](incompleteness_technical_results.md). They supply constraints and examples. The main document now examines the additional assumptions needed to connect those results to the activity they are supposed to explain.

**Working thesis to investigate.** Mathematical expression, interpretation, and justification are interdependent. A formal theory captures a specified arrangement of these activities. Incompleteness constrains that arrangement when its arithmetic content and accepted deductions meet the theorem's hypotheses. To infer a limitation on the wider practice, one must justify treating the arrangement as exhaustive of the relevant means of understanding and justification. To infer practical importance, one must additionally show that the excluded conclusions matter to an independently motivated inquiry.

This thesis does not settle whether such an exhaustive account exists. It puts that question, rather than the defense or refutation of a familiar theorem, at the center of the research.

**Status.** This is a developing argument, with explicit conditional propositions and open questions. The formal observations below use standard logic and elementary constructions; no claim of novelty is made. A distinctive contribution would require a more developed account of how changes in language, interpretation, and justification interact. The present revision identifies that work instead of presenting established consequences of incompleteness as its completion.

**Minimal notation.** A theory is *consistent* if it proves no contradiction, and *sound for* \(\mathbb N\) if everything it proves is true of the standard natural numbers. Write \(T\vdash\varphi\) when \(T\) proves the sentence \(\varphi\), and \(T\nvdash\varphi\) when it does not. The sentence \(\neg\varphi\) is its negation. A theory is *incomplete* when some sentence has neither a proof nor a refutation. \(\operatorname{Th}(\mathbb N)\) denotes the set of true arithmetic sentences. An *effective* theory has an algorithmically enumerable axiom set and effective proof rules. These definitions are expanded in the companion.

**1. The concern about mathematics and language.**

Take *language* provisionally in a broad sense: the shared means by which mathematical claims and reasons become expressible and interpretable. This includes notation and diagrams, and can include explanations, gestures, computational demonstrations, and other representational practices. If language instead means natural-language sentences alone, the claim that all mathematical communication requires it would need a different argument.

On the broad reading, the concern is that mathematics is not first a self-contained activity and then optionally wrapped in language. Mathematical communication depends on people understanding how expressions are to be used, what they refer to, what counts as the same claim in another representation, and what warrants an inference. Formalization makes some of those commitments explicit. It may also leave interpretive work with the users of the formalization.

**Example.** A diagram shows two triangles sharing a side. The marks do not determine on their own whether lengths are exact, whether apparent angles are assumptions, or whether the drawing is merely illustrative. An algebraic encoding can settle these issues once its interpretation is specified. The encoding and its interpretation are parts of the mathematical activity under discussion. Representability of the diagram is not yet a proof that one formal calculus exhausts all legitimate reasoning about it.

The central question is therefore:

> When a theorem limits what follows within a formal representation, under what conditions does that limit also constrain the practice that creates, interprets, and revises the representation?

Two factual qualifications help locate this question. Gödel's result applies across a class of sufficiently expressive effective theories; it is not confined to one particular choice of arithmetic axioms. It also does not assume that only one metalanguage exists or that mathematics and language are independent entities. Arithmetic's ability to encode expressions and proofs is part of the argument itself. [Moschovakis, *Lecture Notes in Logic*, §§4A–4C](https://www.math.ucla.edu/~ynm/lectures/lnl.pdf).

The issue is consequently the adequacy of a proposed formal description of the wider activity. Merely adding languages need not change that adequacy, while changes in how expressions acquire meaning or warrant may be directly relevant.

**2. Four claims that must not be silently identified.**

| Claim | What it asserts | What it does not establish by itself |
| --- | --- | --- |
| Mathematical communication uses shared representations | Claims must be expressed and interpreted to be communicated | A fixed algorithm recognizes every sound mathematical justification |
| Each finished argument admits a formal reconstruction | Particular arguments can be rendered in specified calculi | One sound effective calculus contains every possible warranted argument |
| A coupled practice has an effective formal description | Relevant expressions, translations, and accepted inferences can be generated uniformly | The description faithfully captures every means of justification relevant to the inquiry |
| A formal theory is incomplete | Some expressible sentences have neither proof nor refutation in it | Those sentences are important, frequent, or permanently inaccessible to the practice |

The second distinction contains a quantifier issue. A family of individual formalizations is not automatically a uniformly effective formalization of the family.

For a precise illustration, work temporarily in ordinary classical arithmetic. For every true arithmetic sentence \(\varphi\), the theory

\[
T_\varphi=Q+\varphi
\]

is sound and effectively axiomatized, where \(Q\) is Robinson arithmetic. Nevertheless, no sound effective arithmetic theory proves all those \(\varphi\). Its theorem set would be all arithmetic truth, which is not computably enumerable. Here *computably enumerable* means that an algorithm can list the set's members.

Thus

\[
\forall\varphi\in\operatorname{Th}(\mathbb N)\;
\exists T_\varphi\;[T_\varphi\text{ is sound and effective and }
T_\varphi\vdash\varphi]
\]

does not imply the existence of one sound effective theory proving every such sentence.

This example concerns the quantifiers. Adjoining a true sentence as an axiom does not supply a justification for accepting it, and the example does not identify all truths with actual human knowledge. It shows why the uniformity step requires an argument.

A related distinction concerns finite expression. Every arithmetic truth has a finite expression. The set of arithmetic truths still has no effective enumeration. **Finite communicability is weaker than effective recognition of all correct communications.** The fact that an argument can be expressed through language does not, by itself, give an algorithm that determines which expressions constitute sound arguments.

**3. A model that keeps expression and interpretation together.**

To investigate the coupling, represent a mathematical activity by its finite histories. A history \(h\) records the context accumulated so far: expressions introduced, explanations given, accepted assumptions, and changes in interpretation or inferential practice. An expression \(e\) is assessed in that context.

Let \(W\) be the collection of pairs \((h,e)\) for which \(e\) has a warrant treated as conclusive in the relevant history. This is a proposed mathematical model, not an assertion that real mathematical practice has a determinate, infallible acceptance relation. Conjectures, temporary guesses, and incompatible assumptions cannot simply be collected as jointly true conclusions.

To compare arithmetic claims across contexts, introduce a translation

\[
\tau(h,e)\in\operatorname{Sent}(L_{\mathrm{arith}}),
\]

defined for the warranted arithmetic expressions under consideration. Its intended role is to say which arithmetic claim the contextual expression makes. Whether such translations exist, preserve meaning, and can be obtained effectively are substantive questions.

**Example.** One context introduces a recursively specified numerical sequence; another introduces ordinal notation to reason about its termination. Comparing their conclusions requires identifying the same termination claim in both contexts. Counting two vocabularies gives no answer about what changed in the justification.

**Conditional proposition A — Effective capture of the coupled activity.** Suppose:

1. \(W\) is computably enumerable.
2. \(\tau\) is computable on every pair in \(W\), with arithmetic sentences as outputs.
3. Every translated warranted assertion is true in the standard natural numbers.

Then the arithmetic theory

\[
T_{\mathcal P}
 =Q+\{\tau(h,e):(h,e)\in W\}
\]

is sound, effectively axiomatized, and incomplete.

**Proof.** Enumerate \(W\) and interleave the computations of its translations. Each translation on an enumerated pair eventually finishes, so this enumerates the additional axioms. They and the axioms of \(Q\) are true in \(\mathbb N\), giving soundness. Gödel–Rosser applies to the resulting consistent effective extension of \(Q\). \(\square\)

**Meaning of the result.** Independence between mathematics and language is unnecessary for this conditional argument. The histories may include their interaction. Multiple representations, communities, and layers of metareasoning do not change the conclusion if their jointly warranted arithmetic content satisfies the three assumptions.

**What the result leaves open.** It does not establish those assumptions for mathematical practice. In particular:

- Enumerating things people say is different from enumerating all and only their conclusively warranted assertions.
- Encoding an expression is different from effectively preserving its meaning across contexts.
- Capturing a particular history is different from capturing the relevant possibilities for future development.
- Human acceptance is fallible; soundness is an idealization that needs to be identified as such.

A limit on \(T_{\mathcal P}\) becomes a limit on the modeled practice only to the extent that its arithmetic warrants are exhaustively captured by this construction. If there are relevant warrants outside that capture, the formal conclusion has not yet been transferred to them. Conversely, claiming that such warrants exist does not demonstrate that humans can reliably transcend every effective theory.

This is the substantive point to investigate: **which account of warrants and interpretation makes the capture faithful, and what evidence supports that account?**

**4. Communication and final certification are different requirements.**

The previous section can be restated in terms of communicated evidence, without presuming that all arguments use the same visible notation.

**Conditional proposition B — No complete mechanical certification of arithmetic truth.** There is no decidable relation \(V(p,\varphi)\) on finite certificate codes and arithmetic sentence codes satisfying both:

\[
V(p,\varphi)\ \Longrightarrow\ \mathbb N\models\varphi,
\]

and

\[
\mathbb N\models\varphi\ \Longrightarrow\
\exists p\;V(p,\varphi).
\]

**Proof.** Enumerate all finite pairs \((p,\varphi)\), run the stipulated terminating check, and output \(\varphi\) whenever it accepts. Soundness and completeness of certification would make this an enumeration of true arithmetic, contradicting its non-enumerability. \(\square\)

A certificate could encode a diagram, a conventional derivation, or a finite dialogue. That matters only if the proposed verifier can establish its warrant from the encoded material. If validity depends on unformalized interpretation or external facts, the decidable relation \(V\) has not yet been supplied.

This exposes a precise possible significance of incompleteness: it limits a proposal for exhaustive mechanical certification of arithmetic, including proposals that admit several kinds of representation. It does not establish that every worthwhile mathematical activity needs such certification.

The proof uses classical truth in \(\mathbb N\) as its semantic standard. Naming that structure does not give an observer access to truth outside every language or practice. It supplies a mathematical reference for the conditional claim. Whether this semantic framework is the best account of mathematical meaning is a philosophical question the proof does not settle.

**5. Incompleteness supplies no measure of its own practical importance.**

The assertion that a theory leaves some questions open contains no distribution of questions, no account of their importance, and no measure of the cost of changing theories.

A small formal result makes the missing information visible.

**Proposition C — No workload-independent bound on exposure to incompleteness.** Fix a consistent effective arithmetic theory \(T\supseteq Q\). Let \(\mathcal S\) be the set of all arithmetic sentences, and define

\[
U_T=\{\varphi\in\mathcal S:
T\nvdash\varphi\text{ and }T\nvdash\neg\varphi\}.
\]

For a probability distribution \(\mu\) on \(\mathcal S\), let

\[
E_\mu(T)=\mu(U_T).
\]

This is the probability that a sampled question has neither answer provable in \(T\). For every rational \(0<\varepsilon<1\), there are computable probability distributions \(\mu_{\mathrm{low}}\) and \(\mu_{\mathrm{high}}\), each assigning positive probability to every sentence, such that

\[
E_{\mu_{\mathrm{low}}}(T)\le\varepsilon,
\qquad
E_{\mu_{\mathrm{high}}}(T)\ge1-\varepsilon.
\]

Here computability of a distribution means that its individual sentence probabilities can be computed to arbitrary prescribed precision.

**Proof.** List all arithmetic sentences without repetition as
\(\varphi_0,\varphi_1,\ldots\), effectively. Set

\[
\nu(\varphi_i)=2^{-(i+1)}.
\]

This is a computable probability distribution with positive mass at every sentence. Choose a theorem \(\theta\) of \(T\), such as \(0=0\), and a sentence \(\rho\) independent of \(T\), whose existence follows from Gödel–Rosser. Let \(\delta_\psi\) denote the probability distribution concentrated at the single sentence \(\psi\). Define

\[
\mu_{\mathrm{low}}=(1-\varepsilon)\delta_\theta+\varepsilon\nu,
\qquad
\mu_{\mathrm{high}}=(1-\varepsilon)\delta_\rho+\varepsilon\nu.
\]

Both distributions are computable, since the chosen sentences have fixed finite codes, and both have full support. Because \(\theta\notin U_T\) and \(\rho\in U_T\),

\[
E_{\mu_{\mathrm{low}}}(T)=\varepsilon\nu(U_T)\le\varepsilon,
\]

while

\[
E_{\mu_{\mathrm{high}}}(T)
=1-\varepsilon+\varepsilon\nu(U_T)\ge1-\varepsilon.
\]

No computation of the set \(U_T\), or of its exact probability, is required. \(\square\)

**Plain-language example.** Keep the same incomplete theory. One workload mostly asks an elementary arithmetic question and occasionally samples every other possible question. Another mostly asks an independent question and occasionally samples every other possible question. Incompleteness is arbitrarily rare in the first workload and arbitrarily common in the second. Neither workload excludes any question altogether.

These distributions are deliberately constructed; they are not estimates of real mathematics. Their role is to prove that the theorem alone cannot supply such an estimate. The probability of a question is also distinct from its importance: a rare unanswered question could be decisive.

The measure counts missing proofs, not proofs that exist but are too expensive to find. It therefore separates incompleteness from resource limitations. Nor is a probability based on sentence codes automatically meaningful for mathematical practice: different encodings can assign different weights to equivalent formulations. A relevance argument needs a motivated account of the questions, their meanings, and their stakes.

**6. A demanding example for the claim that incompleteness is merely artificial.**

Goodstein sequences provide a useful test. Starting with a natural number, repeatedly write it in hereditary base notation, increase the base, and subtract one. Each such sequence eventually reaches zero. Kirby and Paris proved that the universal arithmetic assertion of this termination is unprovable in Peano arithmetic. Their statement is about numerical sequences, without mentioning formal provability. [Kirby and Paris, *Accessible Independence Results for Peano Arithmetic*, Theorem 1](https://www.cs.tau.ac.il/~nachumd/term/Kirbyparis.pdf).

For each particular standard starting number, its terminating run is finite. In principle that run can be verified in \(PA\), although it may be extraordinarily long. What \(PA\) lacks is the universal guarantee for every starting number. This last observation follows from finite verification, as explained in the companion.

This example makes the research question harder and more useful. The obstruction need not look like a sentence commenting on its own proof status. But independence from \(PA\) still does not establish inaccessibility to mathematical reasoning: a stronger framework proves the termination theorem. Its significance depends on whether the inquiry concerns individual runs, a universal explanation, the strength of induction, or some application.

The relevant investigation is what the stronger argument contributes, how its additional concepts are justified, and whether their use preserves the original problem's meaning.

**7. Existing work and the contribution still needed.**

The question of relevance is not unexplored. Feferman's 2006 essay explicitly distinguishes the importance of incompleteness within logic from its philosophical significance and its impact elsewhere in mathematics. His assessment of the latter was skeptical. This is a historical position to engage, not a current survey establishing that applications do not exist. [Feferman, *The Impact of the Incompleteness Theorems on Mathematics*](https://math.stanford.edu/~feferman/impact.pdf).

His discussion of conceptual structuralism also examines mathematical concepts and schematic principles whose applications are not fixed once and for all by a chosen formal language. That is a closer predecessor for the present concern about developing expression and interpretation than a catalogue of incomplete theories. [Feferman, *Logic, Mathematics, and Conceptual Structuralism*, especially the discussion of mathematical practice](https://math.stanford.edu/~feferman/papers/Logic_Math_ConceptStructuralism.pdf).

A useful continuation must therefore do more than rename established results. Three concrete investigations are available:

1. **Study a change of representation and justification together.** Trace a mathematical argument as a new language or conceptual apparatus becomes available. Specify which original claims remain the same, what new warrants become admissible, and whether the change is a conservative definition, a new assumption, or a change of subject.
2. **Test the assumption of exhaustive formal capture.** For an explicitly described practice, distinguish its finished arguments from its rules for admitting future arguments. Establish, or exhibit a failure of, the enumeration and translation assumptions in proposition A. Difficulty constructing a translation alone does not prove that none exists.
3. **Supply an independent criterion of relevance.** Choose a problem family for mathematical or practical reasons before selecting an independence witness. Determine whether a formal limitation blocks an important proof, an explanation, an algorithm, or only a preferred axiomatization. Proposition C explains why that criterion cannot be read off from incompleteness itself.

One promising case study is the passage from arithmetic descriptions of Goodstein sequences to their ordinal termination argument. It concerns the same numerical question in different representational settings and makes the extra justificatory commitments identifiable. It would be a study of how a limitation is encountered and overcome in practice, not a claim that adding ordinal notation by itself bypasses a theorem.

**8. An effective method can exceed its theory's ability to justify it.**

The distinction between solving particular problems and proving a universal guarantee needs care. There are at least three claims:

1. Every individual instance has a proof in a given theory.
2. One algorithm produces a proof for every instance.
3. The theory proves the universally quantified mathematical claim.

Under ordinary effectiveness assumptions, the first actually implies the second. Neither by itself gives the third.

**Proposition D — Instancewise provability admits uniform proof search.** Let \(T\) be an effectively axiomatized theory and let \(n\mapsto q(n)\) be a computable sequence of sentences. If

\[
\forall n\in\mathbb N,\qquad T\vdash q(n),
\]

then there is a total computable function \(f\) that, on input \(n\), returns a \(T\)-proof of \(q(n)\).

**Proof.** Compute \(q(n)\), enumerate the finite proofs of \(T\), and stop when a proof with that conclusion appears. For c.e. axioms, proofs can carry finite certificates recording when their axioms were enumerated. The hypothesis guarantees termination on every input. The construction is one algorithm, not a separate choice of algorithm for each \(n\). \(\square\)

If \(q(n)\) is the numeral instance \(\theta(\bar n)\) of a formula, this argument does not give \(T\vdash\forall x\,\theta(x)\). The assertion that the search terminates on every standard input has been made in the surrounding mathematics.

This is consistent with section 2. There we allowed a *different theory* for each sentence, with no effective way of selecting sound theories. Here one fixed effective theory already proves every instance, so searching that theory suffices.

**The Goodstein case developed.** Let \(G(n,t)\) mean that the standard Goodstein sequence starting at \(n\) has reached zero by step \(t\), using its usual arithmetic encoding. The external mathematical facts are

\[
\forall n\in\mathbb N\;\exists t\;G(n,t),
\qquad
PA\nvdash\forall x\,\exists t\,G(x,t).
\]

For each fixed standard \(n\), the finite terminating trace gives a \(PA\)-proof of \(\exists t\,G(\bar n,t)\). Proposition D therefore supplies one effective proof generator for all these instances. There is also the direct algorithm: compute the successive terms and stop at zero. It actually terminates for every input, although \(PA\) cannot prove its totality; for this specified algorithm, the totality assertion is the universal termination statement. The unprovability result is the one cited in section 6; see also [Rathjen, *Goodstein Revisited*](https://arxiv.org/abs/1405.4484).

**What this changes in the investigation.** In this case incompleteness does not imply that no single effective method can carry out the task. The gap concerns a universal justification within the chosen theory. The method may be too slow to use, but that is a separate limitation.

We should therefore assess three things separately: performance on inputs, the mathematical explanation of that performance, and where the explanation can be justified. Some incompleteness phenomena distinguish these levels. This does not mean that every unprovable sentence is merely a disguised request for self-certification.

**9. How can changing language change what mathematics can do?**

“Use a richer language” covers several different interventions. A new term may abbreviate an old expression. A diagram may make a long argument easier to discover. A new quantifier or induction principle may license conclusions that were unavailable before. A reinterpretation may alter the claim being considered.

**Proposition E — Explicit definitions alone preserve old-language consequences.** Let \(T\) be a first-order theory in language \(L\). Introduce a new relation symbol \(R\), and define it by

\[
U=T+\{\forall\vec x\,[R(\vec x)\leftrightarrow\eta(\vec x)]\},
\]

where \(\eta\) is an \(L\)-formula whose free variables are among \(\vec x\). For every \(L\)-sentence \(\varphi\),

\[
U\vdash\varphi\quad\Longleftrightarrow\quad T\vdash\varphi.
\]

**Proof.** In any \(U\)-proof, replace each \(R(\vec t)\) with the corresponding instance of \(\eta\), renaming bound variables when needed. The new defining axiom becomes a logical validity. Original axioms are unchanged, and logical inference is preserved by this substitution. The result is a \(T\)-proof when the conclusion belongs to \(L\). The converse follows because \(U\) contains \(T\). \(\square\)

An extension with this property is called *conservative over \(T\) for \(L\)*. The proposition treats a precise, limited kind of linguistic innovation. It does not classify every change of mathematical language as an explicit definition.

For an old arithmetic claim to become provable, some change must do more than such an eliminable abbreviation: additional assumptions, stronger inference principles, or extra semantic commitments must contribute. Identifying that contribution is part of explaining the advance.

Yet a conservative change can still matter greatly to a finite reasoner. Introducing the term “even” abbreviates “equal to twice an integer”; it can make a pattern easier to state and recognize without creating additional arithmetic consequences. Likewise, more economical notation can change the amount of information a person must hold and manipulate. Proposition E measures provability, not ease of discovery or understanding.

**A revised question about language.** Does a new representation change the available conclusions, the feasibility of finding them, or what counts as understanding them? These are different forms of mathematical progress. A measure that records only which sentences are provable can miss the latter two. This is a specific way a formal account of *consequences* can fail to be a sufficient account of *activity*, even when it correctly records every consequence.

**10. Does accepting a theory involve commitments beyond its deductions?**

Using a theory as a hypothetical calculus and endorsing its axioms as true are different activities. The second raises a question about the justification for trusting its inferences. Are assertions expressing that trust already implicit in the endorsement, or do they require a further argument?

For a consistent effective extension \(T\) of \(PA\), the familiar candidate is \(\operatorname{Con}(T)\): the standard arithmetic assertion that \(T\) has no proof of a contradiction. The theory does not prove this assertion under the usual hypotheses. Whether a person warranted in accepting \(T\) is thereby warranted in accepting \(\operatorname{Con}(T)\) is an additional question about acceptance and justification.

If such a transition is warranted in a specified account, then identifying the person's commitments with \(\operatorname{Thm}(T)\) omits something that account recognizes. This would be a failure of that proposed identification. It would not establish that the person's full commitments evade every effective description.

This question has a developed literature rather than being an unexplored objection. Łełyk and Nicolai propose principles of implicit commitment from which forms of reflection follow, and later extend the analysis to iteration and theories in different languages. Their conclusions depend on the proposed principles; acceptance of those principles is part of the philosophical issue. [*A Theory of Implicit Commitment*](https://link.springer.com/article/10.1007/s11229-022-03601-5), [*Implicit Commitment in a General Setting*](https://arxiv.org/abs/2302.02783).

The useful research task here is to examine a particular warrant for reflection. Replacing \(T\) with \(T+\operatorname{Con}(T)\) describes what has been added; it does not by itself explain why the addition is justified.

There is a further constraint. An evolving method can have a fixed effective description. For example, starting with sound \(PA\), the ordinary iteration \(T_{n+1}=T_n+\operatorname{Con}(T_n)\) is uniformly effective. Its union is sound and incomplete, as the companion explains. Continual growth therefore does not by itself demonstrate a failure of effective capture. The claim at issue concerns justified possibilities for extension, not growth alone.

**11. What would count as further progress?**

The original either/or question can now be sharpened. Incompleteness may constrain a proposed exhaustive account of conclusions while mathematical activity remains capable of producing more than a particular earlier theory certifies. Some of that activity can itself be effective. Some representational improvements can leave provability unchanged while altering discovery and understanding. These possibilities should be separated before deciding what the theorem limits.

A concrete next investigation can follow one transition:

- Fix an arithmetic question whose meaning will be preserved, such as universal Goodstein termination.
- Identify the initial theory's available instance proofs and effective methods.
- State the stronger argument and its extra principles explicitly.
- Distinguish the representation of those principles from the justification for accepting them.
- Ask which relevant accomplishment was unavailable before: a computation, a uniform proof, an explanation, or a justified endorsement.

The formal side can establish conservation, unprovability, and the extra strength needed. The interpretive side must explain why the stronger principles belong to the practice and what their use accomplishes. A historical or cognitive study could also address whether the representation changed discovery, but the formal results alone cannot establish that.

There is an evidential limit to keep in view. Any finite collection \(F\) of true arithmetic assertions fits inside the sound effective theory \(PA+F\). Thus a finite record of successful mathematical innovations cannot by itself show that no sound effective theory captures them. That observation neither predicts future mathematics nor supplies a faithful model of its methods; it limits one proposed inference from observed success to essential non-effectiveness.

**Current assessment.** The paths are not exhausted, but their status differs. The distinction between effective success and internal universal justification can already be demonstrated precisely. The contribution of changes in representation can be analyzed through conservation and proof methods. The proposed connection between justified acceptance and further reflection needs substantive philosophical premises. None of these establishes that mathematical activity is complete, that humans exceed all algorithms, or that incompleteness is irrelevant.

**Research question.**

> Does the demand for a single effective, exhaustive account of mathematical justification describe the practice we are trying to understand, or does imposing that demand remove essential features of how mathematical meaning and warrant develop?

Both answers require work. If the demand is appropriate for a particular project, incompleteness can be a decisive constraint. If it is inappropriate, a limit on the resulting formalization may have little bearing on that project's actual aims. The dependence of mathematics on shared representation is a reason to investigate this issue; it does not determine the answer in advance.

The formal results retained in the companion help police individual inferences. They do not substitute for an account of mathematical practice or demonstrate their own relevance to it.

**Source and revision record.**

Version 3.0 restores the inquiry into the significance of incompleteness as the main direction. Version 3.1 develops effective success without internal universal justification, changes of representation, and implicit commitment. Version 2.0's full text and nine numbered theorems are retained in the technical companion. Propositions A–E above are explicitly conditional or elementary derived observations; the broader thesis remains an investigation.

The primary author sources linked above were consulted on 18 September 2026. The Kirby–Paris paper states the Goodstein termination and unprovability results together as Theorem 1; its independence proof is cited, not reproduced here. Rathjen provides a further treatment of Goodstein sequences and unprovability. The Feferman and Łełyk–Nicolai papers are used as identified philosophical analyses, not as demonstrations that the current thesis is correct. Moschovakis supplies the background logic. Propositions D and E have their elementary derivations written out above. No proof assistant was used.
