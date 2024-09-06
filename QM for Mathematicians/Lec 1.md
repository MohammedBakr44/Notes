---
share_link: https://share.note.sx/krv181he#yEgR1nxEELB5Gn/AbPrLALbr8HDNKqHmtk1eQOVEEc4
share_updated: 2024-08-13T09:14:56+03:00
---

### Isomorphism
Two ${} \mathcal{H} {}$ are Isomorphic if there's a *bijective linear map* between them
$$T: \ \mathcal{H}_1 \rightarrow \mathcal{H}_2$$
#### Bijective Linear Map
A *bijective linear map* is a linear transformation between two vector spaces that is both bijective (one-to-one and onto) and linear. 
$$T : V \rightarrow W$$
- *Linear* means preserving the operations of vector addition and scalar multiplication when mapped from a space to another ${} \forall \vec{u}, \vec{v} \in V {}$
$$T(u+v) = T(u) + T(v)$$
$$T(cu) = cT(u)$$

- *Bijective Map* means ${} T : V \rightarrow W {}$ is
	- Injective(one-to-one) Every element in $W {}$ is mapped from a unique element in ${} V {}$
	$$T(u) = T(v) \implies u = v, \ \forall u, v \in V$$
	- Surjective(Onto) Every element in $W {}$ is the image of at least one element in $V$ 
	$$\forall w \in W \ \exists v \in V$$
### Canonical Isomorphism
Canonical Isomorphism exists between two Hilbert Spaces when there's an Isomorphism between them that preserves vector space structure and inner product.

$$\mathcal{H}^* \cong \mathcal{H}$$

### Endomorphism
Endomorphism is a linear map from a vector space to itself.
$$A: \mathcal{H} \rightarrow \mathcal{H}$$
${} End(\mathcal{H})$ is the set of all Endomorphisms of ${} \mathcal{H}$ in which all operators of ${} \mathcal{H} {}$ resides. So  the notation
$$A \in End(\mathcal{H})$$
denotes the operator *A* maps vectors from space ${} \mathcal{H} {}$ to itself.