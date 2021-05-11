# Chapter 3 - Propositional Calculus

------



## Equivalence ("==")

<hr>

### Leibniz

$$
\frac{P == Q}{E[r:= P] == E[r:= Q]}
$$

### Transitivity

$$
\frac{P == Q, Q == R}{P == R}
$$

### Substitution

$$
\frac{P}{P[r:= Q]}
$$



### (3.1)  Axiom, associativity of ==: ((p == q) == r) == (p == (q == r))

### (3.2) Axiom, symmetry of ==: (p == q) == (q == p)

### (3.3) Axiom, identity of ==: true == q == q

### (3.4) True

```pseudocode
= <(3.3) identity of ==, where q:= true>
true == true

= <(3.3) identity of ==, where RHS true:= q == q>
true == q == q .
```



### (3.5) Reflexivity of ==: p == p

```pseudocode
= <(3.3) p == p == true
true .
```



### (3.6) Proof method

> To prove that P == Q is a theorem, transform P to Q or Q to P using Leibniz.
>

### (3.7) Metatheorem

> Any two theorems are equivalent.

## Negation, inequivalence, and false ("~", "!==", "false")

### (3.8) Axiom, definition of false: false == ~true

### (3.9) Axiom, distributivity of ~ over ==: ~(p == q) == ~p == q

### (3.10) Axiom, definition of !==: (p !== q) == ~(p == q)

### (3.11) ~p == q == p == ~q

```pseudocode
= <(3.2) symmetry of ==, q:= ~q>
~q == p

= <(3.9) distributivity of ~ over ==>
~(q == p)

= <(3.2) symmetry of ==>
~(p == q)

= <(3.9) distributivity of ~ over ==>
~p == q .
```



### 3.12 Double negation: ~~p == p

```pseudocode
= <(3.9) distributivity of ~ over ==>
~~(p == p)

= <(3.3) identity of ==>
~~(true)

= <(3.3) identity of ==>
~~(true == true)

= <(3.9) distributivity of ~ over ==>
~(~true == true)

= <(3.9) definition of false>
~(false == true)

= <(3.9) distributivity of ~ over ==>
~false == true

= <(3.11), p, q := false, true>
false == ~true

= <(3.9) definition of false>
false == false 

= <(3.3) identity of ==)
true .
```



### (3.13) ~false == true

```pseudocode
<(3.9) definition of false>
~~true

= <(3.12) dobule negation>
true .
```



### (3.14) (p !== q) == ~p == q

```pseudocode
= <(3.10) def !==>
~(p == q)

= <(3.9) distributivity of ~ over ==>
~p == q .
```



### (3.15) ~p == p == false

```pseudocode
= <(3.9) distributivity of ~ over ==>
~(p == p) == false

= <(3.2) identity of ==>
~true == false

= <(3.8) def false>
false == false

= <(3.3) identity of ==>
true .
```



### (3.16) Symmetry of !==: (p !== q) == (q !== p)

```pseudocode
= <(3.14) (p !== q) == ~p == q>
~p == q

= <(3.9) distributivity of ~ over ==>
~(p == q)

= <(3.2) symmetry of ==>
~(q == p)

= <(3.9) distributivity of ~ over ==>
~q == p

= <(3.14) (p !== q) == ~p == q>
(q !== p) .
```



### (3.17) Associativity of !==: ((p !== q) !== r) == (p !== (q !== r))

```pseudocode
((p !== q) !== r) LHS

= <(3.14) (p !== q) == ~p == q, p:= (p !== q)>
~(p !== q) == r

= <(3.14) (p !== q) == ~p == q>
~(~p == q) == r

= <(3.9) distributivity of ~ over ==>
~~p == q == r

= <(3.12) double negation>
((p !== q) !== r) == p == q == r : lemma 3.12.1

(p !== (q !== r)) RHS

= <(3.14) (p !== q) == ~p == q>
~p == (q !== r)

= <(3.14) (p !== q) == ~p == q>
~p == ~q == r

= <(3.11) ~p == q == p == ~q, q := ~q)
~~p == q == r

= <(3.12) double negation>
p == q == r

<(3.12.1) ((p !== q) !== r) == p == q == r>
((p !== q) !== r) .
```



### (3.18) Mutual associativity: ((p !== q) == r) == (p !== (q == r))

```pseudocode
= <(3.14) (p !== q) == ~p == q>
~p == q == r

= <(3.14) (p !== q) == ~p == q>
(p !== q) == r .
```



### (3.19) Mutual interchangeability: p !== q == r == p == q !== r

```pseudocode
= <(3.14) (p !== q) == ~p == q>
= ~p == q == r

= <(3.11) ~p == q == p == ~q)
= p == ~q == r

= <(3.14) (p !== q) == ~p == q>
= p == q !== r .
```



### (3.20) P0 == P1 == ... == P*n* is true exactly when

> an even number of the P*i* are false.



### (3.21) Heuristics

> Identify applicable theorems by matching the structure of expressions or subexpressions.

### (3.22) Principle

> Structure proofs to avoid repeating the same subexpression on many lines.

### (3.23) Heuristics of Definition Elimination:

> To prove a theorem concerning an operator O1 that is defined in terms of O2, expand the definition of O1 to arrive at a formula that contains O2; exploit the property of O2 to manipulate the formula; and then reintroduce O1 using its definition.



## Disjunction ("v")

<hr>

### (3.24) Axiom, symmetry of v: p v q == q v p

### (3.25) Axiom, associativity of v: (p v q) v r == p v (q v r)

### (3.26) Axiom, idempotency of v: p v p == p

### (3.27) Axiom, distributivity of v over ==: p v (q == r) == p v q == p v r

### (3.28) Axiom, excluded middle: p v ~p

### (3.29) Zero v: p v true == true 

```pseudocode
= <(3.3) identity of ==>
p v p == p

= <(3.26) idempotency of v>
p v p == p v p

= <(3.26) idempotency of v>
p == p

= <(3.3) identity of ==>
= true .
```



### (3.30) Identity of v: p v false == p

```pseudocode
= <(3.27) def false ==>
p v ~true == p

= <(3.29) zero of v>
p v ~(p == p) == p

= <(3.9) distributivity of ~ over ==> 
p v ~p == p == p

= <(3.27) distributivity of v over ==>
p v ~p == p v p == p

= <(3.26) idempotency of v>
p v ~p == p == p

= <(3.3) identity of ==>
p v ~p == true

= <(3.7) metatheorem>
true == true 

= <(3.3) identity of ==>
true .

```



### (3.31) Distributivity of v over v: p v (q v r) == p v q v p v r

```pseudocode
= <(3.24) symmetry of v>
q v p v p v r

= <(3.26) idempotency of v>
p v q v r

= <(3.25) associativity of v>
= p V (q v r)
```



### (3.32) p v q == p v ~q == p





