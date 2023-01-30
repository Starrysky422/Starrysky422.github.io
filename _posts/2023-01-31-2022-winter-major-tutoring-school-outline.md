---
layout: post
title: 2022 Winter Major Tutoring School Lecture Notes
comments: true
tags: 
- Mathematical Analysis
- Lecture Note
---

During this winter vacation, I conducted a 9-lecture course previewing the upcoming semester's major subject *Introduction to Mathematical Analysis (with practice) 1* in the College of Natural Sciences, Seoul National University. Below are lecture notes that briefly summarize the past classes.

---

## Course Description
In high school and freshman year *Calculus*, we learned several mathematical concepts such as limits of sequences, continuity, differentiation, and integration. However, the question remains: do we truly understand these concepts? How are limits defined, and how are the notions of continuity, differentiation, and integration described? Additionally, what are the real numbers? There were too many explanations based on intuition, not logic, to say that we fully understood them. *Introduction to Mathematical Analysis (with practice) 1* aims to thoroughly re-establish the contents of *Calculus* on strict logic, and to gain a deeper understanding of *Calculus* in the process.

*Mathematical Analysis*, along with *Linear Algebra*, is the first subject that students encounter rigorous mathematics. This course will provide an overall flow and structure of the subject, *Introduction to Mathematical Analysis (with practice) 1* to help the mentees not get lost in the repetition of theorem-and-proofs.

We will rigorously construct the real numbers, and study basic topology on top of them. We will also define the limits of sequences and functions, and explore the continuity, differentiation, and integration of single-variable real functions. Furthermore, we will study the properties of sequence spaces and function spaces.

### Required Textbooks
- 김도한·김성기·계승혁, 《해석개론》, 제2개정판, 서울대학교출판문화원, 2011.

### Unspecified Textbooks
- 김홍종, 《미적분학 1+》, 제2개정판, 서울대학교출판문화원, 2016.
- 김홍종, 《미적분학 2+》, 제2개정판, 서울대학교출판문화원, 2016.
- 이슬비, 《맛있는 해석학》, 제4개정판, 수학 나라의 앨리스, 2019. ([online](https://iseulbee.com/archives/the-art-of-analysis-4ed/))
- J. Munkres, *Topology*, Second Edition, Pearson, 2014.
- W. Rudin, *Principles of Mathematical Analysis*, Third Edition, McGrawHill Education, 1976.
- T. Tao, *Analysis I*, Third Edition, Springer, 2016.

---

## Lecture 1: What are Real Numbers? (2022.12.19.)
### Main Topics
- Number systems: $\mathbb{N}, \mathbb{Z}, \mathbb{Q}, \mathbb{R}, \mathbb{C}$
- Least upper bound property
- The real numbers as the complete ordered field
- Convergent sequences and Cauchy sequences
- Cauchy completeness

### Lecture Note
- What are real numbers? We learned in middle school that real numbers are *points on the number line*, but this is not a satisfactory definition. Another familiar and seeming approach is to define real numbers as *infinite decimals*. However, this definition can be challenging to work with as constructing multiplication over infinite decimals is a very complex task.[^1-InfiniteDecimal]
- Despite these adversities, we do know some properties of real numbers. One property is that we can perform addition, subtraction, multiplication, and division between two real numbers. A set on which these four operations are well-defined as a **field**. Additionally, we can compare the magnitudes of two real numbers, and such magnitude is compatible with the four operations. This makes real numbers an **ordered field**. However, these properties alone do not fully characterize real numbers; the rational number system $\mathbb{Q}$ also satisfies these properties.
- What makes real numbers different from rational numbers is **completeness**. Intuitively, completeness of real numbers can be understood as 'real numbers completely fill the number line.' There are several ways to define completeness of real numbers, and these methods are equivalent to each other. One means is the **least upper bound property**, which states that every nonempty subset of real numbers bounded above has a least upper bound, called the **supremum** of the set. Symmetrically, we may consider the **greatest lower bound property**, and the **infimum**, the greatest lower bound of a set.
- The amazing fact is that there exists a unique complete ordered field (up to isomorphism), and it is real numbers. In this sense, we define *the* real numbers as **the complete ordered field**.
- Nextly, we will rigorously define **limits of sequences**. It is usually defined using the $\varepsilon$-$\delta$ argument. Similarly, we can define **Cauchy sequences**.
- It can be easily proved that every convergent sequence is Cauchy, but the converse does not hold in general. For example, a rational sequence convergent to $\sqrt{2}$ is Cauchy but not convergent in $\mathbb{Q}$. However, in real numbers, every Cauchy sequence is convergent, and such property is called the **Cauchy completeness**. The Cauchy completeness can be adopted as an alternative definition of completeness of the real numbers. More precisely, it is slightly weaker than the least upper bound property, but becomes equivalent when a feature called the Archimedean property is added.[^1-Archimedean]
- On a side note, we briefly explore several ways to construct the real numbers, such as defining them as equivalence classes of Cauchy sequences in $\mathbb{Q}$---which is called the Cauchy completion of $\mathbb{Q}$---or as Dedekind cuts of $\mathbb{Q}$. Proving that these truly become the complete ordered field is not complicated, but it can be tedious.

[^1-InfiniteDecimal]: For example, the *long multiplication* of two infinite decimals involves infinitely many carries, infinite series, and many other difficulties.
[^1-Archimedean]: There exist Cauchy complete non-Archimedean ordered fields, such as the field $\mathbb{Q}_p$ of $p$-adic numbers.

---

## Lecture 2: Completeness of the Real Numbers (2022.12.21.)
### Main Topics
- The real numbers as a metric space
- Convergent sequences and Cauchy sequences in a metric space
- Monotone convergence theorem
- Nested intervals theorem
- Finite, countable, and uncountable sets

### Lecture Note
- The significance of *abstracting* mathematical concepts is highlighted: it helps us to gain a deeper understanding of the underlying essence of the subject. Examination of the real numbers from the perspective of **metric space** is introduced to address this, which enables a re-definition of limits of sequences and a generalization of Cauchy completeness in the context of metric spaces.
- The third definition of completeness of real numbers is presented through the **monotone convergence theorem**, and its proof under the least upper bound property is covered.
- The concepts of $\limsup$ and $\liminf$, as well as an alternative definition of $\lim$, are introduced.
- The fourth definition of completeness of real numbers is presented through the **nested intervals theorem**, and its proof under the least upper bound property is covered.
- The notion of **cardinality** of sets, including **countable** and **uncountable** infinity, is explored. **Cantor's diagonal argument** is used to prove the uncountability of the real numbers.
- As an off-topic note, it is worth mentioning that the set of real numbers is extremely large. The concepts of algebraic numbers and definable numbers are mentioned to illustrate the point.

---

## Lecture 3: Basic Topology (2022.12.26.)
### Main Topics
- Euclidean spaces as metric spaces, normed spaces and inner product spaces
- Cauchy completeness of $\mathbb{R}^d$
- (Metric) topology on $\mathbb{R}^d$
- Basic properties of topology
- Topological definition of convergence

### Lecture Note
- The Euclidean spaces, $\mathbb{R}^d$, are examined from the perspectives of metric spaces, **normed spaces**, and **inner product spaces**. It is noted that an inner product induces a norm, and a norm induces a metric.
- Aside from the usual norm $\norm{\blank}\subscr{2}$, alternative norms such as the *taxi norm* $\norm{\blank}\subscr{1}$ and the *sup norm* $\norm{\blank}\subscr{\infty}$ are introduced. The observation that the notions of convergence induced by these norms are the same suggests that convergence is not dependent on the specific metric defined on the space, but rather on a more fundamental underlying structure.
- The (metric) **topology** on Euclidean space is introduced. Also, the basic properties of topology, so-called the axiomatic definition of topology, are explored. The concept of convergence is re-defined in the topological context.
- The notion of **sequential closedness** is introduced to provide a handy intuition for topology. It is noted that every closed set is sequentially closed, and the converse holds in metric spaces (under the axiom of choice).[^3-MetricSpace]

[^3-MetricSpace]: In fact, all spaces covered in the course *Introduction to Mathematical Analysis (with practice) 1* are metric spaces.

---

## Lecture 4: Compactness (2022.12.28.)
### Main Topics
- Compactness
- Heine-Borel theorem

### Lecture Note
- The significance of compactness is highlighted: the extreme value theorem for continuous functions essentially originates from the domain, a closed and bounded interval.
- To give a better understanding of compactness, intuitive illustrations such as *a generalization of closed and bounded interval*, *a continuous analogue of finiteness*, and *solid and small*, are provided.
- The definition of **compactness** is presented through the finite intersection property definition, with a generalization of the nested intervals theorem serving as a hint. The contrapositive, the open cover definition, is also introduced.[^4-DefinitionOfCompactness]
- It is demonstrated that every compact subset of Euclidean space is closed and bounded. The proof is given from a topological perspective, allowing for generalization to metric spaces. The converse, the compactness of closed and bounded intervals and the **Heine-Borel theorem**, which provides a complete characterization of compact subsets of Euclidean spaces, are also covered, along with their proofs. It is noted that the completeness of real numbers is crucial for these proofs, indicating that the Heine-Borel theorem is merely a manifestation of completeness of real numbers, rather than a central aspect of compactness.
- As an alternative formulation of compactness, the concept of **sequential compactness** is introduced, along with the **Bolzano-Weierstrass theorem**, the sequential analogue of the Heine-Borel theorem.

[^4-DefinitionOfCompactness]: I struggled to figure out the best way to introduce the rigorous definition of compactness to my mentees, as the commonly-used open cover definition can be seemed to come out of nowhere at first. While I considered using alternative formulations such as sequential or limit point compactness, these concepts are only equivalent to compactness in metric spaces and might confuse my mentees when they take a topology course next year. I desired to present a more motivating approach and found that the finite intersection property definition fit my purpose, as it can be framed as *a generalization of closed and bounded interval*.

---

## Lecture 5: Connectedness, Continuity (2023.1.2.)
### Main Topics
- Connectedness
- Characterization of connected subsets of $\mathbb{R}$
- $\varepsilon$-$\delta$ definition of limit and continuity
- Topological definition of limit and continuity
- Extreme value theorem
- Intermediate value theorem

### Lecture Note
- The significance of connectedness is highlighted: the intermediate value theorem for continuous functions essentially originates from the domain, an interval.
- The rigorous definition of **connectedness** is presented. Also, the complete characterization of connected subsets of real numbers is covered, along with its proof. It is noted that the completeness of real numbers is crucial to the proof.
- The **limit** and **continuity** of functions are first defined using the $\varepsilon$-$\delta$ argument, then re-established in the contexts of metric spaces and topological spaces.
- As a related aside, the extended natural numbers $\mathbb{N}\cup\\{\infty\\}$ and the extended real line $[-\infty,\infty]$ are introduced, along with their topologies. The consistency between limits of functions, limits of sequences, and infinite limits of functions, with the latter two being previously defined using the $\varepsilon$-$N$ argument, is then discussed.
- The **extreme value theorem** and the **intermediate value theorem** are reformulated as *continuous mappings preserve compactness and connectedness*, which implies their classical statements. Their proofs are straightforwardly provided from a topological perspective, showcasing our current level of understanding of the nature of real numbers and continuity.

---

## Lecture 6: Local Property vs. Global Property (2023.1.4.)
### Main Topics
- Local property and global property
- Compactness *takes local properties to their global counterparts*
- Uniform continuity
- Sequential continuity and Cauchy continuity
- Cardinality of $C(\mathbb{R})$

### Lecture Note
- As a preface, the concept of **local and global properties** are introduced, along with their analogical examples such as local and global extrema. An additional aspect of compactness is then presented as *taking local properties to their global counterparts*. This is demonstrated by providing an alternative proof of the extreme value theorem that uses the idea that a locally bounded function on a compact set is globally bounded.[^6-CompactnessAspect]
- Continuity is highlighted as a local property, and the concept of **uniform continuity** is introduced as its global analogue. It is shown that a continuous function on a compact set is uniformly continuous, which further illustrates the *globalization aspect* of compactness.
- The concept of **sequential continuity** is introduced as an alternative formulation of continuity. It is noted that continuity implies sequential continuity, and the converse holds in metric spaces. Additionally, the notion of **Cauchy continuity** is mentioned as a sequential analogue of uniform continuity.
- As a side topic, the cardinality of the set of continuous functions on the real numbers is discussed. The cardinality is shown to be equal to that of the real numbers, by using the notion of sequential continuity and the separability of real numbers.

[^6-CompactnessAspect]: This approach towards the topic of uniform continuity was motivated by [this post](https://math.stackexchange.com/a/15492).

---

## Lecture 7: Differentiation & Integration (2023.1.9.)
### Main Topics
- Differentiation
- Mean value theorem
- Taylor expansion
- Riemann integral and Darboux integral
- Integrability of continuous functions on a bounded interval
- The fundamental theorem of Calculus
- Riemann-Stieltjes integral
- Function of bounded variation

### Lecture Note
- **Differentiation**, the **mean value theorem**, and **Taylor expansion** are briefly reviewed as they have already been covered in the *Calculus* course. A non-analytic smooth function and the concept of holomorphicity are mentioned as a side note.
- As a preface, the high school definition 
  
  $$\int_a^b f(x)dx := \lim_{n\to\infty}\sum_{k=1}^{n} f(x_k)\Delta x, \quad \left(x_k = a + k\Delta x,\ \Delta x = \frac{b-a}{n}\right)$$

  of integral is introduced, along with questions on: "Do we have to divide $[a,b]$ into $n$ equal parts?", "Do we have to choose $x\subscr{k}$ as endpoints of sub-intervals?", and "Are continuous functions integrable?"
- The definition of **Riemann integral** is given, using the notions of partition, mesh, and Riemann sum, as well as its alternative formulation using **upper and lower Darboux integrals**. The analogical aspect of the Darboux integral with $\limsup$ and $\liminf$ is emphasized.
- The Riemann integrability of continuous functions on a bounded interval, and its proof using the notion of uniform continuity are covered.
- The **Riemann-Stieltjes integral** is introduced as an analogue of the change of variables, and its consistency with the change of variables under a differentiable integrator is noted. The concepts of **total variation** and **functions of bounded variation** are introduced to address the integrability problem. It is noted that every continuous function is integrable if the integrator is of bounded variation and that every function of bounded variation can be written as a difference between two monotone functions, known as the **Jordan decomposition** of a function.
- As a final remark, it is noted that the Riemann-Stieltjes integral results in a discrete sum if the integrator has jump discontinuities, which hints at a connection between series and integrals.

---

## Lecture 8: Sequences of Sequences and Functions (2023.1.11.)
### Main Topics
- Pointwise convergence and uniform convergence
- *Exchangeability of limits* under uniform convergence
- Limits of derivatives and integrals
- Fubini theorem for double series

### Lecture Note
- As a preface, the paradox about computing the infinite sum 
  
  $$1-1+1-1+1-1+\dots$$
  
  using two different ways that yield different answers is introduced to emphasize the need for a rigorous approach to handling infinity, especially when exchanging the order of infinitely many terms.
- The topics that will be covered in this lecture---limits of double sequences, limits of sequences of functions, and double series---are outlined, which deal with the *exchangeability of two limits*.
- The concept of **pointwise convergence** is presented as a likely formulation of limits of sequences of sequences or functions. However, several counterexamples of failing to exchange two limits are shown to emphasize the localness of pointwise convergence. The global counterpart, **uniform convergence**, is then introduced.
- It is demonstrated that the uniform limit of a double sequence with convergent rows is convergent, and the uniform limit of a sequence of continuous functions is continuous, both using the $\varepsilon/3$-trick. Also, it is noted that for a convergent sequence of functions, the derivatives converge to the derivative of the limit if they converge uniformly, and the integrals converge to the integral of the limit if the functions converge uniformly. Additionally, the **Fubini theorem** for double series is mentioned, with its relationship with the concept of absolutely convergent series.

---

## Lecture 9: Spaces of Sequences and Functions (2023.1.16.)
### Main Topics
- Sequence spaces $\ell^\infty(\mathbb{N})$, $c(\mathbb{N})$, $c_0(\mathbb{N})$, $\ell^p(\mathbb{N})$ as Banach spaces
- Continuous function space $C(K)$ as a Banach space
- Riemann integrable function spaces and their non-completeness
- Arzelà-Ascoli theorem
- Stone-Weierstrass theorem

### Lecture Note
- The **sequence spaces** $\ell^\infty(\mathbb{N})$, $c(\mathbb{N})$, $c_0(\mathbb{N})$, and $\ell^1(\mathbb{N})$, along with their associated norms $\norm{\blank}\subscr{\infty}$ and $\norm{\blank}\subscr{1}$, are introduced. The significance of the sup norm is highlighted as it relates to uniform convergence. Also, the Cauchy completeness of these spaces are demonstrated and the concept of **Banach space** is introduced.
- The space $\ell^2(\mathbb{N})$ with its associated norm $\norm{\blank}\subscr{2}$ is introduced as an analogue of the usual norm on Euclidean spaces. The generalization of this to $\ell^p(\mathbb{N})$ and the $p$-norm $\norm{\blank}\subscr{p}$ with $p\in[1,\infty]$ is explained, along with the naming conventions of the norms.
- The **continuous function space** $C(X)$ is introduced, then its definition is narrowed down to the case of $C(K)$ where $K$ is compact, so that the sup norm is well-defined. The Cauchy completeness of $C(K)$ is noted, making it a Banach space.
- Other analogous function spaces such as $C_0(\mathbb{R})$ and Riemann integrable function spaces, along with their associated $p$-norms, are presented. It is noted that the Riemann integrable function spaces are not Cauchy complete, which hints at the need for the Lebesgue integral.
- Returning to $C(K)$, the **Arzelà-Ascoli theorem**, an analogue of the Heine-Borel theorem for $C(K)$, is stated. Its proof is outlined in three steps: separability of $C(K)$, finding a pointwise convergent subsequence using the diagonal argument, and showing its uniform convergence. The significance of separability is highlighted from its cruciality in the proof, then the **Stone-Weierstrass theorem** is mentioned as a demonstration of the separability of $C(\mathbb{R})$.

---

## Footnotes