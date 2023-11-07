# Purposes of the course
- Get better with proofs.
- Proof statements about real numbers, functions and limits.
- Getting better at real maths.
# Sets
#### Def
`A set is a collection of objects, called elements or members` 
#### Empty set
`A set with no elements denoted by`  ${} \phi$ 

# Notation
- ${} a \in S$ (" a is an element of S")
- $a \notin S$ ("a is not an element of S") 
- ${} \forall {}$ "For all"
- $\exists {}$ "There exists"
- ${} \implies {}$ "implies"
- ${} \iff {}$ "if and only if"  ${} p \implies q \land q \implies p$  
*\*not mentioned in the lecture but I'm going to use them
- ${} \land {}$ and
- ${} \lor {}$ or
### Def
- Set A is a subset of B, ${} A \subset B {}$ if  ${} a \in A \implies a \in B$ 
- Two sets are equal, A = B, if $A \subset B$ and $B \subset A$
- A is a proper subset of B, $A \subseteq B$, $$A \subset C \land A \neq B$$
### Sets
- ${} \mathbb{N} = \{ 1, 2, 3, 4 \} {}$
- ${} \mathbb{Z} = \{0, 1 , -1, 2, -2\} {}$
- ${} \mathbb{Q} = \{\frac{m}{n} \quad m, n \in \mathbb{Z}, n \neq 0\}$
- $\mathbb{R}$, Real numbers
- Odd numbers, ${} \{2m - 1 : m \in \mathbb{N}\} {}$
- $\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R}$

	First goal: describe $\mathbb{R} {}$
### Union
 $${} A \cup B = \{x : x \in A \lor x \in B\} {}$$
### Intersection
$$A \cap B = \{x : x \in A \land x \in B\}$$
### Set difference
$$A \setminus B = \{x \in A : x \notin B\}$$
### Complement

$$A^C = \{x : x \notin A\}$$
### Disjoint sets
$$A \cap B = \phi$$
## Theroem
#### Def
${} P \implies Q {}$                                        if P then Q

# Thm (De Morgan's)
	If A, B, C are sets then:
- ${} (B\cap C)^c =  {}$  ${} B^c \cup C^c {}$ 
- ${} (B \cap C)^c = B^c \cup C^c {}$ 
- ${} A \setminus (B \cup C) =  {}$ ${} (A \setminus B) \cap (A \setminus C) {}$
- ${} A \setminus (B \cap C) =  {}$ $(A \setminus B) \cup (A \setminus C) {}$
### Proof
	Let B, C be sets proof that 

$$(B \cup C)^c = B^c \cap C^c$$
   and
$$B^c \cap C^c = (B \cup C)^c$$
##### wts(want to show): 
$$ (B \cup C)^c \subset B^c \cap C^c $$
   let ${} x \in (B \cup C)^c {}$  then  $${} x \notin B \cup C \implies x \notin B \land x \notin C  \implies x \in B^c \land x \in C^c \implies x \in B^c \cap C^c {}$$
   Thus 
$$(B \cup C)^c \subset B^c \cap C^c$$




##### wts: ${} {} B^c \cap C^c \subset (B \cup C)^c {} {}$
  let ${} x \in B^c \cap C^c$ then
$${} x \in B^c \land x \in C^c \implies x \notin B \land x \notin C \implies x \notin B \cup C \implies x \in (B \cup C)^c {}$$
   Thus
$$B^c \cap C^c \subset (B \cup C)^c$$
   Thus by the definition of equality of two sets
$$B^c \cap C^c = (B \cup C)^c$$
${} \Box {}$
## Ordering
${} \mathbb{N} = \{1, 2, 3, \dots\} {}$ has an ordering, ${} 1 \lt 2 \lt 3 \lt 4 {}$ 

##### Axiom(well ordering property of ${} \mathbb{N} {}$)
if ${} S \subset \mathbb{N} \quad S \neq \phi {}$ thus ${} S {}$ has a least element
${} \exists x \in S$ s.t ${} x \leq y \quad \forall y \in S {}$

## Thm(Induction)
let ${} P(n) {}$ be a statement depending on ${} n \in \mathbb{N} {}$ Assume
- (Base case) ${} P(1) {}$ is true
- (Inductive step) ${} P(m) \iff P(m+1) {}$
Then ${} P(n) {}$ is true ${} \forall n \in \mathbb{N} {}$
### proof
#### Contradiction
let ${} \{n \in \mathbb{N}: \neg P(n)\} {}$  w.t.s $S = \phi {}$ 
least element ${} x \in S {}$  Since P(1) is true,
${} 1 \notin S \implies x \neq 1 \implies x \gt 1 {}$
Since ${} x {}$ is the least element of $S {}$,
and ${} x - 1 \lt x {}$, then ${} x - 1 \notin S {}$ thus
${} P(x-1) {}$ By (2) ${} P(x) \implies x \notin S {}$ then
${} S = \phi, \quad \exists x \in \mathbb{N} \land x \notin \mathbb{N} {}$ 
${} \to \gets {}$
$S = \phi \quad \Box {}$ 

# Thm
$$(*) \quad \forall c \neq 1, \quad \forall n \in \mathbb{N} \quad 1 + c + c^2 + \dots + c^n = \frac{1-c^{n+1}}{1-c}$$
### proof
- (Base case) = ${} P(1) = 1 + c = \frac{1 - c^{1 + 1}}{1-c} {}$ 
   ${} \frac{1-c^2}{1-c} = \frac{\bcancel{(1 - c)}(1 + c)}{\bcancel{1-c}} = 1 + c {}$
- (Inductive step) = $P(m) {}$
   
   $$1 + c + c^2 + \dots + c^m + c^{m+1} = \frac{1-c^{m+1}}{1 - c} + c^{m+1} $$
  $$ \frac{1-c^{m+1} + {c^{m+1}(1-c)}}{1-c} = \frac{1-c^{(m+1)+1}}{1-c} \quad (**)$$
 
  Thus (\*) holds for ${} P(n+1) {}$.
	By induction, (\*) holds ${} \forall n \in \mathbb{N}$  ${} \Box {}$ 
  
  
  *full steps*
 $$\frac{1-c^{(m+1)} + c^{(m+1)} \space(1-c)}{1-c} = \frac{1-\bcancel{c^{(m+1)}} + \bcancel{c^{(m+1)}} - c^{(m+1)+1}}{1-c}$$ 



### Thm
if ${} c \geq -1 {}$, then ${} \forall n \in \mathbb{N} {}$
$$(***) \quad \quad (1+c)^n \geq 1 + nc$$
#### proof
- (Base Case)               
 ${} (1+c)^1 = 1 + 1c \quad {}$ holds for ${} n = 1 {}$
-   (Inductive step)

$$ (1+c)^m \geq 1+mc $$
$$(1+c)^{m+1} = (1+c)(1+c)^m \geq (1+c)(1+mc)$$
  $$(1+c)^{m+1} \geq 1 + (m + 1)c + mc^2$$
  $$\geq 1 + (m+c)$$
  $$(1+c)^{m+1} \geq 1+(m+1)c$$
  then ${} n = m+1 {}$ in case of (\*\*\*)
  By induction, (\*\*\*) holds ${} \forall n \in \mathbb{N} {}$.
  