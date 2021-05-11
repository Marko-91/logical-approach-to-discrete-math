# Chapter 3 - Propositional Calculus

## Equivalence ("==")

### Leibniz:  P == Q | E[r:= P] == E[r:= Q]

### Transitivity: P == Q, Q == R | P == R

### Substitution: P | P[r:= Q]

### (3.1)  Axiom, associativity of ==: ((p == q) == r) == (p == (q == r))

### (3.2) Axiom, symmetry of ==: (p == q) == (q == p)

### (3.3) Axiom, identity of ==: true == q == q

### (3.4) True

`= <(3.3) identity of ==, where q:= true>`

`= true == true`

`= <(3.3) identity of ==, where RHS true:= q == q>`

`= true == q == q .`

### (3.5) Reflexivity of ==: p == p

`= <(3.3) p == p == true`

`= true .`

### (3.6) Proof method

To prove that P == Q is a theorem, transform P to Q or Q to P using Leibniz

### (3.7) Metatheorem

Any two theorems are equivalent.