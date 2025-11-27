## Chapter 1 - Foundations of Propositional Logic  

These notes present the elementary syntactic and semantic machinery of classical propositional logic.  
The exposition follows the style common in modern mathematical logic: explicit inductive definitions, semantic clauses stated with full precision, and a clear separation between the object language and the metalanguage.

---

## 1. Syntax

### 1.1 Alphabet
We fix:

1. A countable set **PROP** of propositional variables:  
   $$\[
   p, q, r, p_0, p_1, \ldots
   \]$$

2. Logical connectives:  
   $$\[
   \lnot, \quad \land,\quad \lor,\quad \to,\quad \leftrightarrow
   \]$$

3. Parentheses: $$\( (, ) \)$$

No other symbols are permitted.

---

### 1.2 Formation of Formulas
The set **FORM** of formulas is the smallest set such that:

1. **Atomic stage:**  
   Every variable \( p \in \mathrm{PROP} \) is a formula.

2. **Inductive stage:**  
   If $$\( \varphi, \psi \in \mathrm{FORM} \)$$, then:
   - $$\( \lnot \varphi \in \mathrm{FORM} \)$$
   - $$\( (\varphi \land \psi) \in \mathrm{FORM} \)$$
   - $$\( (\varphi \lor \psi) \in \mathrm{FORM} \)$$
   - $$\( (\varphi \to \psi) \in \mathrm{FORM} \)$$
   - $$\( (\varphi \leftrightarrow \psi) \in \mathrm{FORM} \)$$

3. **Closure:**  
   Nothing else is a formula.

---

### 1.3 Structural Properties
- **Unique Readability:** Each formula admits a unique parse tree; there is no ambiguity about the placement of connectives.  
- **Scope:** The scope of a connective is explicitly delimited by parentheses unless standard precedence conventions are adopted.  
- **Induction on Structure:** Proofs concerning formulas proceed by structural induction on the rules above.

---

## 2. Semantics

### 2.1 Valuations
A **valuation** is a function  
$$\[
v:\mathrm{PROP}\to\{0,1\}
\]$$  
assigning a truth value to each propositional variable.

The valuation extends uniquely to all formulas by the following **truth clauses**:

- $$\( v(\lnot \varphi)=1 \)$$ iff $$\( v(\varphi)=0 \)$$.  
- $$\( v(\varphi\land\psi)=1 \)$$ iff $$\( v(\varphi)=1 \)$$ and $$\( v(\psi)=1 \)$$.  
- $$\( v(\varphi\lor\psi)=1 \)$$ iff $$\( v(\varphi)=1 \)$$ or $$\( v(\psi)=1 \)$$.  
- $$\( v(\varphi\to\psi)=0 \)$$ iff $$\( v(\varphi)=1 \)$$ and $$\( v(\psi)=0 \)$$; otherwise 1.  
- $$\( v(\varphi\leftrightarrow\psi)=1 \)$$ iff $$\( v(\varphi)=v(\psi) \)$$.

This completes the inductive semantic definition.

---

### 2.2 Truth Tables
Each connective corresponds to a specific Boolean function.  
Example: the material conditional.

| $$\(p\) | \(q\) | \(p\to q\)$$ |
|------|------|-------------|
| 1 | 1 | 1 |
| 1 | 0 | 0 |
| 0 | 1 | 1 |
| 0 | 0 | 1 |

A formula’s meaning is its *truth function* under all valuations.

---

## 3. Semantic Properties

### 3.1 Tautologies
A formula $$\( \varphi \)$$ is a **tautology** if:
$$\[
v(\varphi)=1 \quad \text{for every valuation } v.
\]$$
Notation:  
$$\[
\models \varphi.
\]$$

---

### 3.2 Satisfiability
A formula $$\( \varphi \$$) is:

- **Satisfiable** if there exists a valuation $$\( v \)$$ with $$\( v(\varphi)=1 \)$$.  
- **Unsatisfiable** if for all valuations $$\( v \), \( v(\varphi)=0 \)$$.

A set $$\( \Gamma \)$$ is satisfiable if some valuation makes all members of \( \Gamma \) true.

---

### 3.3 Logical Consequence
For a set of formulas $$\( \Gamma \)$$ and formula $$\( \varphi \)$$:

$$\[
\Gamma \models \varphi
\]$$
means:

> For every valuation $$\( v \)$$, if $$\( v(\gamma)=1 \)$$ for all $$\( \gamma\in\Gamma \)$$, then $$\( v(\varphi)=1 \)$$.

Equivalently: there is no valuation that makes all members of $$\( \Gamma \)$$ true and $$\( \varphi \)$$ false.

---

## 4. Normal Forms

### 4.1 Literals
A **literal** is either $$\( p \)$$ or $$\( \lnot p \)$$.

### 4.2 Clauses and Terms
- A **term** is a conjunction of literals.  
- A **clause** is a disjunction of literals.

These provide the building blocks of the normal forms.

---

### 4.3 Disjunctive Normal Form (DNF)
A formula is in **DNF** if it is a disjunction of terms, i.e. a disjunction of conjunctions of literals:

$$\[
(\ell_{11}\land \cdots\land \ell_{1k}) \ \lor \ \cdots\ \lor\ (\ell_{n1}\land\cdots\land\ell_{nk}).
\]$$

### 4.4 Conjunctive Normal Form (CNF)
A formula is in **CNF** if it is a conjunction of clauses:

$$\[
(\ell_{11}\lor \cdots\lor \ell_{1k}) \ \land\ \cdots\ \land\ (\ell_{m1}\lor\cdots\lor\ell_{mk}).
\]$$

---

### 4.5 Representability Theorems
Every propositional formula $$\( \varphi \)$$ is logically equivalent to both:

- a formula in DNF, and  
- a formula in CNF.

Two constructive routes:

1. **Truth-table method:**  
   - Identify the rows where $$\( \varphi = 1 \)$$ → assemble canonical DNF.  
   - Identify the rows where $$\( \varphi = 0 \)$$ → assemble canonical CNF.

2. **Equivalence-preserving rewrites:**  
   - Eliminate $$\( \to \)$$ and $$\( \leftrightarrow \)$$.  
   - Apply De Morgan’s laws.  
   - Use distributivity $$\( \land \) over \( \lor \)$$, and conversely.

---

## 5. Soundness and Completeness (Informal Treatment)

### 5.1 Derivation
Let **⊢** denote provability in a chosen deductive calculus (e.g., natural deduction or a Hilbert system).  
The syntactic machinery is distinct from, but intended to reflect, semantic consequence.

---

### 5.2 Soundness
**The Soundness Theorem (informal):**

> If a formula is derivable in the proof system, then it is valid under all valuations.

Formally:  
$$\[
\vdash \varphi \quad \Rightarrow \quad \models \varphi.
\]$$

Intuition:  
Each inference rule preserves truth in all valuations; thus proofs cannot produce semantic falsehoods.

---

### 5.3 Completeness
**The Completeness Theorem (informal):**

> If a formula is valid under all valuations, then it is derivable in the proof system.

Formally:  
$$\[
\models \varphi \quad \Rightarrow \quad \vdash \varphi.
\]$$

Intuition:  
The deductive system is strong enough to prove every semantic truth.

---

### 5.4 Harmony of Syntax and Semantics
Combining both directions:

$$\[
\vdash \varphi \quad \text{iff} \quad \models \varphi.
\]$$

This provides the exact correspondence between formal proofs and truth under all interpretations—an alignment that is central to metalogical analysis.

---

## 6. Meta-Level Commentary

A few higher-level remarks useful for the aspiring metalogician:

- Syntax is the combinatorial core of logic; semantics is the interpretive layer.  
- Truth tables provide a complete semantic characterization of propositional logic.  
- Normal forms expose structural content relevant to automated reasoning, satisfiability procedures, and proof search.  
- Soundness protects against “syntactic overreach”; completeness ensures “semantic coverage.”  
- Propositional logic is a model for understanding how syntax and semantics interact in richer systems (first-order logic, modal logic, etc.).

---

## 7. Further Directions
To advance beyond the elementary theory:

- Proof theory (natural deduction, Hilbert systems, sequent calculi)  
- Model theory (structures, definability, compactness)  
- Modal logic  
- First-order logic  
- Arithmetization of syntax  
- Gödel’s incompleteness theorems  
- Advanced meta-theory (interpolation, definability theorems, algebraic semantics)

---

*End of Text.*
