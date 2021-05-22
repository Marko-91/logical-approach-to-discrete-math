# Relaxing The Proof Style

## An Abbreviation for proving implication

### (4.1) p => (q => p) 

**(q => p)**

= def =>

q v p == p

= idempotency

q v p == p v p &or;

= distributivity of v over ==

p v (p == q)

<= weakening p => p v q

p

**p**

<= weakening p => p v q

p v (p == q)

= distributivity of v over ==

q v p == p v p

= idempotency

q v p == p

= def =>

q => p

### (4.2) Monotonicity of v: (p => q) => (p v r => q v r) 

**p v r => q v r**

= def =>

p v r v q v r == q v r

= idempotency of v

p v q v r == q v r

= distributivity of v over ==

(p v q == q) v r

<= weakening p => p v q

p v q == q

= def ->

p => q

**p => q**

dev ->

p v q == q

=>  weakening p => p v q

(p v q == q) v r

= distributivity of v over ==

p v q v r == q v r

= idempotency of r

p v r v q v r == q v r

= def ->

p v r => q v r

### (4.3) Monotonicity of &: (p => q) => (p & r => q & r) 

