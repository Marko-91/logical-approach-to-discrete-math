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



### (3.6) Proof method: to prove that P == Q is a theorem, transform P to Q or Q to P using Leibniz.

### (3.7) Metatheorem: any two theorems are equivalent.

## Negation, inequivalence, and false ("&not;", "!=", "false")

### (3.8) Axiom, definition of false: false == ~true  

### (3.9) Axiom, distributivity of ~ over ==: ~(p == q) == ~p == q  

### (3.10) Axiom, definition of !=: (p != q) == ~(p == q)

### (3.11) ~p == q == p == ~q

```pseudocode
LHS
test &not;
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
LHS
<(3.9) definition of false>
~~true

= <(3.12) dobule negation>
true .
```



### (3.14) (p != q) == ~p == q

```pseudocode
LHS
= <(3.10) def !=>
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



### (3.16) Symmetry of !=: (p != q) == (q != p)

```pseudocode
LHS
= <(3.14) (p != q) == ~p == q>
~p == q

= <(3.9) distributivity of ~ over ==>
~(p == q)

= <(3.2) symmetry of ==>
~(q == p)

= <(3.9) distributivity of ~ over ==>
~q == p

= <(3.14) (p != q) == ~p == q>
(q != p) .
```



### (3.17) Associativity of !=: ((p != q) != r) == (p != (q != r))

```pseudocode
((p != q) != r) LHS

= <(3.14) (p != q) == ~p == q, p:= (p != q)>
~(p != q) == r

= <(3.14) (p != q) == ~p == q>
~(~p == q) == r

= <(3.9) distributivity of ~ over ==>
~~p == q == r

= <(3.12) double negation>
((p != q) != r) == p == q == r : lemma 3.12.1

(p != (q != r)) RHS

= <(3.14) (p != q) == ~p == q>
~p == (q != r)

= <(3.14) (p != q) == ~p == q>
~p == ~q == r

= <(3.11) ~p == q == p == ~q, q := ~q)
~~p == q == r

= <(3.12) double negation>
p == q == r

<(3.12.1) ((p != q) != r) == p == q == r>
((p != q) != r) .
```



### (3.18) Mutual associativity: ((p != q) == r) == (p != (q == r))

```pseudocode
RHS
= <(3.14) (p != q) == ~p == q>
~p == q == r

= <(3.14) (p != q) == ~p == q>
(p != q) == r .
```



### (3.19) Mutual interchangeability: p != q == r == p == q != r

```pseudocode
LHS
= <(3.14) (p != q) == ~p == q>
= ~p == q == r

= <(3.11) ~p == q == p == ~q)
= p == ~q == r

= <(3.14) (p != q) == ~p == q>
= p == q != r .
```



### (3.20) P0 == P1 == ... == P*n* is true exactly when

> an even number of the P*i* are false.



### (3.21) Heuristics: Identify applicable theorems by matching the structure of expressions or subexpressions.

### (3.22) Principle: Structure proofs to avoid repeating the same subexpression on many lines.

### (3.23) Heuristics of Definition Elimination: To prove a theorem concerning an operator O1 that is defined in terms of O2, expand the definition of O1 to arrive at a formula that contains O2; exploit the property of O2 to manipulate the formula; and then reintroduce O1 using its definition.



## Disjunction ("v")

<hr>

### (3.24) Axiom, symmetry of v: p v q == q v p

### (3.25) Axiom, associativity of v: (p v q) v r == p v (q v r)

### (3.26) Axiom, idempotency of v: p v p == p

### (3.27) Axiom, distributivity of v over ==: p v (q == r) == p v q == p v r

### (3.28) Axiom, excluded middle: p v ~p

### (3.29) Zero v: p v true == true 

```pseudocode
LHS
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
RHS
= <(3.26) idempotency of v>
p v q v r

= <(3.25) associativity of v>
= p v (q v r) .
```



### (3.32) p v q == p v ~q == p

```pseudocode
= <(3.27) distributivity of v over ==, r:= ~q>
p v (q == ~q) == p

=<(3.15)>
p v false == p .
```



### (3.33) Heuristics: To prove P == Q transform the expression with the most structure (either P or Q) into the other.

### (3.34) Principle: Structure proofs to minimize the number of rabbits pulled out of a hat.



## Conjunction ("&")

<hr>

### (3.35) Axiom, golden rule: p & q == p == q == p v q

### (3.36) Symmetry of &: p & q == q & p

```pseudocode
= <(3.35) golden rule>
p == q == p v q == q == p == q v p

<(3.24, 3.2) symmetry of v, ==>
(p == q == p v q) == (p == q == p v q)

<(3.3) identity of ==>
true . 
```



### (3.37) Associativity of &: (p & q) & r == p & (q & r)

```pseudocode
LHS
= <(3.35) golden rule, twice>
(p == q == p v q) == r == (p == q == p v q) v r

= <(3.1) associativity of == >
p == q == p v q == r == (p == q == p v q) v r

= <(3.27) distributivity of v over ==>
p == q == p v q == r == p v r == q v r == p v q v r

= <symmetry of ==> 
p == q == r == p v q == q v r == r v p == p v q v r LEMMA 3.37.1

RHS
= <(3.35) golden rule, twice>
p == (q == r == q v r) == p v (q == r == q v r)

= <(3.1) associativity of == >
p == q == r == q v r == p v (q == r == q v r)

= <(3.27) distributivity of v over ==>
p == q == r == q v r == p v q == p v r == p v q v r

= <symmetry of ==> 
p == q == r == p v q == q v r == r v p == p v q v r

<lemma 3.37.1>
 (p & q) & r .
```



### (3.38) Idempotency of &: p & p == p

```pseudocode
= <(3.35) golden rule>
p == p == p v p == p

= <(3.26) idempotency of v>
p == p == p == p

<(3.3) identity of ==>
true == true .
```



### (3.39) Identity of  &: p & true == p

```pseudocode
= <(3.35) golden rule>
p == true == p v true == p

= <(3.29) zero of v>
p == true == true == p

= <identity of ==>
p == true == p

= <symetry of ==>
true == p == p .
```



### (3.40) p & false == false

```pseudocode
= <(3.35) golden rule>
p == false == p v false == false

= <(3.30) identity of v>
p == false == p == false

= <symmetry of ==>
p == p == false == false

= <identity of ==>
true == false == false . (3.20)
```



### (3.41) Distributivity of & over &: p & (q & r) == (p & q) & (p & r)

```pseudocode
RHS
= <(3.38) idempotency of &>
p & q & r

= <(3.37) associativity of &)
p & (q & r) .
```



### (3.42) Contradiction: p & ~p == false

```pseudocode
<golden rule>
= p == ~p == p v ~p == false

= <(3.15) ~p == p == false>
false == p v ~p == false

= <excluded middle>
false = true = false

= <(3.20) even number of false>
= true .
```



### (3.43) Absorption: (a) p & (p v q) == p	(b) p v (p & q) == p

```pseudocode
(a)
= <golden rule>
p == (p v q) == p v p v q == p

= <idempotency of v>
p == p v q == p v q == p

= <identity, symmetry of ==>
true == p == p .

(b)
= <golden rule>
p v (p == q == p v q) == p

= <distributivity of v>
p v p == p v q == p v p v q == p

= <idempotency of p, symmetry of ==>
p == p == p v q == p v q

= <identity of ==, twice>
true .
```

### (3.44) Absorption (a) p & (~p v q) == p & q	(b) p v (~p & q) == p v q

```pseudocode
(a)
= <golden rule>
p == ~p v q == p v ~p v q == p == q == p v q

= <excluded middle, zero of v>
p == ~p v q == true == p == q == p v q

= <identity, symmetry of ==>
true == true == q == p v q == ~p v q

= <symmetry of v>
true == q == q v p == q v ~p

= <(3.32) p:= q>
true == true .

(b)
= <golden rule>
p v (~p == q == ~p v q) == p v q

= <distributivity of v over ==
p v ~p == p v q == p v ~p v q == p v q

= <excluded middle>
true == p v q == true v q == p v q

= <zero of v, symmetry of ==>
true == true == p v q == p v q

= <identity of ==>
true == p v q == p v q .
```



### (3.45) Distributivity of v over &: p v (q & r) == (p v q) & (p v r)

```
LHS
= <golden rule>
p v (q == r == q v r)

= <distributivity of v over ==>
p v q == p v r == p v q v r LEMMA 3.45.1

RHS
= <golden rule>
p v q == p v r == p v q v p v r

= <idempotency of v, lemma 3.45.1>
p v q == p v r == p v q v r .
```

### (3.46) Distributivity of & over v: p & (q v r) == (p & q) v (p & r)

```
LHS
<golden rule>
p == q v r == p v q v r lemma 3.46.1

RHS
<golden rule>
(p == q == p v q) V (p == r == p v r)

<distributivity of v over ==>
(p == q == p v q) v p == (p == q == p v q) v r == (p == q == p v q) v p v r

<distributivity, symmetry of v over ==>
p v p == p v q == p v p v q == p v r == q v r == p v q v r == p v p v r == p v q v r == p v p v q v r

<idempotency of v>
p == p v q == p v q == p v r == q v r == p v q v r == p v r == p v q v r == p v q v r

<identity of ==>
p == true == true == q v r == true == p v q v r

<identity of ==, lemma 3.46.1>
p == q v r == p v q v r . 
```



### (3.47) De Morgan: (a) ~(p & q) == ~p v ~q	(b) ~(p v q) == ~p & ~q

```
(a)
~(p & q) == ~p v ~q
<golden rule>
~(p == q == p v q) == ~p v ~q

<distributivity of ~ over ==>
~p == ~q == ~(p v q) == ~p v ~q

<golden rule>
~p & ~q == ~(p v q)
~(p & q) == ~p v ~q == ~(p v q) == ~p & ~q . lemma 3.47.1

(b)
~(p v q) == ~p & ~q
<golden rule>
~(p == q == p & q) == ~p & ~q

<distributivity of ~ over ==>
~p == ~q == ~(p & q) == ~p & ~q

<golden rule>
~(p & q) == ~p v ~q by lemma 3.47.1 .

```



### (3.48) p & q == p & ~q == ~p

```
<(3.11) ~p == q == p == ~q>
~(p & q) == p & ~q == p

<golden rule>
~(p & q) == p v ~q == ~q

<(3.11) ~p == q == p == ~q>
p & q == p v ~q == ~~q

<double negation>
p & q == p v ~q == q

<golden rule>
p == q == p v q == p v ~q == q

<identity, symmetry of ==>
true == p == p v q == p v ~q

<symmetry of ==, (3.11)>
true == p v q == p v ~q == p . by 3.11
```



### (3.49) p & (q == r) == p & q == p & r == p

```
p & (q == r) == p
<golden rule>
p v (q == r) == q == r

<distributivity>
p v q == p v r == q == r

<symmetry of ==>
p v q == q == p v r == r

<golden rule>
p & q == p == p & r == p

<identity of ==>
p & q == p & r .

```



### (3.50) p & (p == q) == p & q

```
(3.49)
p & p == p & q == p == p & q

<idempotency of &>
p == p & q == p == p & q

<identity of ==, symmetry>
true == true .

```



### (3.51) Replacement: (p == q) & (r == p) == (p == q) & (r == q)

```
RHS
<golden rule>
p == q == r == q == p == q v r == q

<symmetry, identity of ==>
q == r == q v r

<golden rule>
q & r

LHS
<golden rule>
p == q == r == p == p == q v r == p

<symmetry, identity of ==>
q == r == q v r

<golden rule>
q & r , rhs == lhs .

```



### (3.52) Definition of ==: p == q == (p & q) v (~p & ~q)

```
<distributivity>
(p & q) v ~p & (p & q) v ~q

<distributivity>
(~p v p) & (~p v q) & (~q v p) & (~q v q) . | p, ~p, q, ~q LEMMA 3.52.1

<excluded middle>
~p v q & ~q v p (note that xor is proved here with duality between & and v)

~p v q == ~q v p == ~p v q v ~q v p

~p v q == ~q v p

RHS
p v q == p & q
p v q == ~p v ~q
```



### (3.53) XOR: p != q == (~p & q) v (p & ~q)

```
<distributivity>
(~p & q) v p v (~p & q) v ~q

<distributivity>
(~p v p) & (p v q) & (~p v ~q) & (~q v ~q)

<excluded middle>
p v q & ~p v ~q

LHS:
<def !=>
~(p == q)
```



*skipping enumeration of lemmas*

### (3.56) Heuristics: Exploit the ability to parse theorems like the golden rule in many different ways.



## Implication ("=>")

<hr>

### (3.57) Axiom, definition of implication: p => q == p v q == q

### (3.58) Axiom, consequence: p <- q == q => p

### (3.59) Definition of implication: p => q == ~p v q

```
<3.57 def =>>
p v q == ~p v q == q

<3.32 q == q v p == q v ~p>
p v q == ~p v q == q v p == q v ~p

<symmetry of v>
p v q == ~p v q == p v q == ~p v q

<identity of ==>
true == true .
```



### (3.60) Definition of implication: p => q == p & q == p

```
<3.59 def of =>>
p v q == q == p & q == p

< symmetry of ==>
p == q == p v q == p & q . by golden rule

```



### (3.61) Contrapositive p => q == ~q => ~p

```
~q => ~p
<def =>>
p => q == ~p v q

<def =>>
p v q == q == ~p v q

<symmetry of ==, 3.32 q == q v p == q v ~p>
p v q == ~p v q == q v p == q v ~p 

<symmetry of v>
p v q == ~p v q == p v q == ~p v q

<identity of ==>
true == true .
```

### (3.62) p => (q == r) == p & q == p & r

```
p & q == p & r
<3.49>
p & (q == r) == p

p => (q == r)
<def =>>
p & (q == r) == p 
lhs == rhs .

```



### (3.63) Distributivity of => over ==: p => (q == r) == p => q == p => r

```
p => q == p => r
<def =>>
p v q == q == p v r == r lemma 3.63.1

p => (q == r)
<def =>>
p v (q == r) == q == r

<distributivity>
p v q == p v r == q == r

<symmetry ==>
p v q == q == p v r == r . by lemma 3.63.1

```



### (3.64) p => (q => r) == (p => q)  => (p => r)

```
(p => q) => (p => r)
<def =>>
(p => q) v (p => r) == p => r

<def =>>
(p v q == q) v (p v r == r) == p => r

<distributivity of v over ==>
(p v q == q) v (p v r) == (p v q == q) v r == p => r

<distributivity of v over ==>
p v q v p v r == p v q v r == p v q v r == q v r == p => r

<idempotency of v>
p v q v r == p v q v r == p v q v r == q v r == p => r

<identity of ==>
p v q v r == q v r == p => r

p => (q => r)
<def =>>
p => (q v r == r)

<def =>>
p => q v r == p => r

<def =>>
p v q v r == q v r == p => r . lhs == rhs

```



### (3.65) Shunting: p & q => r == p => (q => r)

```
p & q => r
<def =>>
p & q & r == p & q

p => (q => r)
<def =>>
p & (q & r == q) == p

<3.49 distributivity of & over add p>
p & q & r == p & q == p == p

<identity>
p & q & r == p & q . lhs == rhs

```





### (3.66) p & (p => q) == p & q

```
p & (p => q)
def =>
p & (p & q == p)

<3.49 distributivity of & over add p>
p & p & q == p & p == p

idempotency of &
p & q == p == p

identity of ==
p & q .
```



### (3.67) p & (q => p) == p

```
 p & (q => p)
 (3.66, p:= q, q:= p)
 p & p
 
 idempotency of &
 p .
 
```



### (3.68) p v (p => q) == true

```
def =>
p v (p v q == q)

distributivity
p v p v q == p v q

idempotency of v
p v q == p v q

identity 
true .
```



### (3.69) p v (q => p) == q => p

```
p v (q => p)

def =>
p v (q v p == p)

distributivity
p v q v p == p v p

idempotency of v
p v q == p

q => p
def =>
q v p == p

symmetry of v
p v q == p . lhs == rhs


```



### (3.70) p v q => p & q == p == q

```
 p v q => p & q == p == q
 golden rule
 p v q => p & q == p & q == p v q
 
 identity of == 
 p v q => p v q . by reflexivity of =>

```



### (3.71) Reflexivity of =>: p => p == true

```
def v
p v p == p

idempotency of v
p == p

identity of ==
true .
```

### (3.72) Right zero of =>: p => true == true

```
def =>
p v true == true

zero of v
true == true

identity of ==
true .
```



### (3.73) Left identity of =>: true => p == p

```
def =>
true v p == p

zero of v
true == p

identity of ==
p .
```



### (3.74) p => false == ~p

```
def =>
p v false == false

identity of v
p == false == ~p . by 3.15

```



### (3.75) false => p == true

```
def =>
false v p == p

identity of v
p == p

identity of == 
true .
```



### (3.76) Weakening/strengthening

#### (a) p => p v q

```
def =>
p v p v q == p v q

idempotency of v
p v q == p v q

identity of ==
true .
```



#### (b) p & q => p

```
def =>
p & q & p == p & q

idempotency of &
p & q == p & q

identity of ==
true .
```



#### (c) p & q => p v q

```
def =>
~(p & q) v p v q

de morgan
~p v ~q v p v q

symmetry of v
~p v p v ~q v q

excluded middle
true v true

zero of v
true .
```



#### (d) p v (q & r) => p v q

```
distributivity
p v q & p v r => p v q
 (p)  &	 (q)  =>   (p) .

weakening/strenghtening
```



#### (e) p & q => p & (q v r)

```
p & q => p & q v p & r
 (p)  =>  (p)  v  (q) . 
 
 weakening/strenghtening
```



### (3.77) Modus ponens: p & (p => q) => q

```
def =>
p & (~p v q)

3.44 absorption
p & q => q . by 3.76 (b)
```



### (3.78) Form of case analysis: (p => r) & (q => r) == (p v q => r)

```
p v q => r
golden rule
p v q v r == r

(p => r) & (q => r)
def =>
(p v r == r) & (q v r == r)

golden rule
(p v r == r) v (q v r == r) == p v r == r == q v r == r

distributivity
p v r v q v r == p v r v r == r v q v r == r v r ==
p v r == r == q v r == r

idempotency 
p v q v r == p v r == q v r == r == 
		    p v r == q v r

symmetry
p v q v r == r .
```



### (3.79) Form of case analysis: (p => r) & (~p => r) == r

```
(p => r) & (~p => r)
def =>
(p v r == r) & (~p v r == r)

golden rule
(p v r == r) v (~p v r == r) == p v r == r == ~p v r == r

distributivity
p v r v ~p v r == p v r v r == r v ~p v r == r v r == r

zero of v
true v r == p v r == ~p v r == r == r

identity of ==
p v r == ~p v r

symmetry of v
r v p == r v ~p

3.32
r .
```



### (3.80) Mutual implication: (p => q) & (q => p) == p == q

```
(p => q) & (q => p)
def =>
(p v q == q) & (q v p == p)

golden rule
(p v q == q) v (q v p == p) == p v q == q == q v p == p

distributivity of v
p v q v q v p == p v q v p == q v q v p == q v p == p v q == q == q v p == p

idempotency, symmetry of v
p v q == p v q == p v q == p v q == p v q == q == p v q == p

identity, symmetry of ==
p == q .
```

### (3.81) Antisymmetry: (p => q) & (q => p) => (p == q)

```
(p => q) & (q => p) 
3.80
p == q => (p == q) . by reflexivity of =>
```



### (3.82) Transitivity

#### (a) (p => q) & (q => r) => (p => r)

```
3.78, form of case analysis
p v q => r => p => r

def =>
p v q v r == r => p v r == r

def =>
(p v q v r == r) v (p v r == r) == p v r == r

distributivity
p v q v r == p v q v r == p v r == r == p v r == r

identity, symmetry of ==
true == true == true .
```



#### (b) (p == q) & (q => r) => (p => r)

```
TODO
```



#### (c) (p => q) & (q == r) => (p == r)

```
TODO
```



### (3.83) Axiom, Leibniz (e = f) => (E[z:= e] = E[z:= f])

> If e = f is true in a state, then E[z:= e] = E[z:= f] is true in that state.

### (3.84) Substitution

#### (a) (e = f) & E[z:= e] == (e = f) & E[z:= f] 

```
***
Axiom, leibniz
(e = f) => (E[z:= e] = E[z:= f])

def =>
(e = f) v (E[z:= e] = E[z:= f]) == (E[z:= e] = E[z:= f])

def =>
(e = f) & (E[z:= e] = E[z:= f]) == (e = f)
***

(e = f) & E[z:= e] == (e = f) & E[z:= f] 
golden rule
(e = f) & E[z:= e] & (e = f) & E[z:= f] == (e = f) & E[z:= e] v (e = f) & E[z:= f]

distributivity
E[z:= e] & E[z:= f] == (e = f) & (E[z:= e] v E[z:= f])

Axiom, leibniz
E[z:= e] & E[z:= f] == (e = f)

E = z = e
z = e & z = e == e = f

E[z:= e], E[z:= f]
e = e & f = e == e = f

identity of =
e = f == e = f . by identity of ==
```



#### (b) (e = f) => E[z:= e] == (e = f) => E[z:= f]

```
E = z = f
(e = f) => z = f[z:= e] == (e = f) => z = f[z:= f]

substitution
(e = f) => e = f == (e = f) => f = f

symmetry of = 
(e = f) => e = f == (e = f) => true

right zero of =>
(e = f) => e = f == true

reflexivity of =>
true == true .
```



#### (c) q & (e = f) => E[z:= e] == q & (e = f) => E[z:= f]

```
E = z = f
q & (e = f) => z = f[z:= e] == q & (e = f) => z = f[z:= f]

substitution
q & (e = f) => e = f == q & (e = f) => f = f

symmetry of = 
q & (e = f) => e = f == q & (e = f) => true

right zero of =>
q & (e = f) => e = f == true

<(3.65) Shunting: p & q => r == p => (q => r)>
q => (e = f => e = f == true)

reflexivity of =>
q => true . by right zero of =>
```



### (3.85) Replace by true

#### (a) p => E[z:= p] == p => E[z:= true]

```
E = z
p => z[z:= p] == p => z[z:= true]

substitution
p => p == p => true

right zero of =>
p => p == true . by right zero of =>
```



#### (b) q & p => E[z:= p] == p & q => E[z:= true] 

```
E = z
q & p => z[z:= p] == p & q => z[z:= true]

substitution
q & p => p == p & q => true

<(3.65) Shunting: p & q => r == p => (q => r)>
q => (p => p) == p & q => true

right zero of =>
q => (p => p) == true

reflexivity of =>
q => true == true

right zero of =>
true == true .
```



### (3.86) Replace by false

#### (a) E[z:= p] => p == E[z:= false] => p

```
E = z
z[z:= p] => p == z[z:= false] => p

substitution
p => p == false => p

<3.74 false => p == true>
p => p == true

right zero of =>
true .
```





#### (b) E[z:= p] => p v q == E[z:= false] => p v q

```
E = z
z[z:= p] => p v q == z[z:= false] => p v q

substitution
p => p v q == false => p v q

<3.74 false => p == true>
p => p v q == true

<(3.76) Weakening/strengthening p => p v q>
true == true .
```



### (3.87) Replace by true: p & E[z:= p] == p & E[z:= true]

```
E = z
p & z[z:= p] == p & z[z:= true]

substitution
p & p == p & true

idempotency of &
p == p & true

identity of &
p == p . 
```



### (3.88) Replace by false: p v E[z:= p]  == p v E[z:= false]

```
E = z
p v z[z:= p]  == p v z[z:= false]

substitution
p v p == p v false

idempotency of p
p == p v false

<identity of v p v false == p>
p == p .
```



### (3.89) Shannon: E[z:= p] == (p & E[z:= true]) v (~p & E[z:= false])

```
E = z
z[z:= p] == (p & z[z:= true]) v (~p & z[z:= false])

substitution
p == (p & true) v (~p & false)

identity of &
p == p v (~p & false)

<(3.40) p & false == false>
p == p v false

identity of v
p == p .
```



```
p & q => (p == q)
replace by true 3.85b
p & q => p == true

replace by true 3.85b
p & q => true == true

identity ==
p & q => true

right zero of =>
true .
```



## Exercises on duals

### (3.85) P == ~P<sub>d</sub>

```
P is of the form, q & r, q == r, q => r

de morgan
~(q & r) == ~q v ~r .

q == r == ~(q != r)
definition of !=
q == r == ~~(q == r)

double negation
q == r == q == r . by symmetry of ==

q => r == ~(q <- r) ...
```

## Exercises on normal forms

$$
E_{0} \wedge E_{1} \wedge ... \wedge E_{n-1}
$$

> where each Ei is a disjunction of variables and negation of variables.

` (a ^ ~b) v (a ^ b ^ c) v (~a)`

### (3.89) Exercise 

| A    | B    | C    | D    |
| ---- | ---- | ---- | ---- |
| 1    | 1    | 1    | 0    |
| 1    | 1    | 1    | 1    |
| 1    | 0    | 1    | 0    |
| 0    | 1    | 1    | 0    |

```
(p & q) v ~(q & ~p) v ~(p & ~p) v ~(p & ~q) - DNF

~(p v q) & (q v ~p) & (p v ~p) & ~(p v ~q) - CNF
```



