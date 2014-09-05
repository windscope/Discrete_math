<script type="text/javascript"
  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>  
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: ["tex2jax.js"],
    jax: ["input/TeX", "output/HTML-CSS"],
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
      processEscapes: true
    },
    "HTML-CSS": { availableFonts: ["TeX"] }
  });
</script>
Discrete Mathematics
===
MTH 309 Course Notes. Will continuously update as the class goes on.  
_Note Author: Yang Liu_


Counting
---
1. __Multiplication rule__ 	
	We perform a task, which can be broken into k independent steps. Each step can be complete d in  $n\_{1},n\_{2},...,n\_{k}$ ways. Entire task can be completed in $n\_{1},n\_{2},...,n\_{k}$ .
2. __Addition rule__ 	
	If a task can be completed in k mutually exclusive ways, then $N = n\_{1}+n\_{2}+...+n\_{k}$  is the number of choices for the $N = i_{th}$ order.
3. __Permutation__ 	
	In general, the number of permutation of n objects is _n!_.
	
4. __Selection with Repetition__
	+ Ordered with repetition	
	There are $n^{r}$ ways to do an ordered r selection out of n objects
	+ Unordered with repetition	
	
		There are ${n+r-1 \choose r}$ ways to do an unordered r selection out of n objects
	
5. __Important equation__
	+ ${n + 1\choose k}  =  {n\choose k}  +  {n\choose k-1}$

	+ ${n\choose m}{m\choose r} = {n\choose r} + {n-r \choose m-r}$

	+ $(x+y)^{n} = \sum_{k=0}^{n} {n\choose k}x^{n-k}y^{k}$
	
	+ $(2)^{n} = \sum_{k=0}^{n} {n\choose k}$
	
	+ $0^{n} = \sum_{k=0}^{n} {n\choose k}(-1)^{k}$

	

Recurrence
---
Recurrence relation is representation of nth number $a_{n}$ in a sequence is connect to previous states $a\_{i}$, i<n. 

__Solving recurrence equation__		

+	Level 1
	+  Homogeneous
	
		$a\_{n} = Ca\_{n-1}, a\_{1} = A       -> a\_{n} = AC^{n-1}$
	+ Non-homogeneous  
		1. Find special solution by substitute non-homogeneous part to the recurrence equation, and then calculate the equation, find the coefficient of special solution, _k_. 
		2. Substitute the special solution to the recurrence equation and then substitute the initial condition   $a_{1}$ to calculate the coefficient A. 
	
+ 	Level 2
	+  Homogeneous
		1. Given that $a_{n}=pa\_{n-1}+qa\_{n-2}$, write the characteristic equation by replace $a\_{n}$ by  $ \lambda ^{2} $ and others respectively. by solving the equation $\lambda^{2}+p\lambda+q$, we got $\lambda\_{1}$ and $\lambda\_{2}$. Then substitute the two $\lambda$ to the given recurrence equation, an pseudo equation can be calculated:  $a\_{n} = A\lambda\_{1}^{n}+b\lambda\_{2}^{n}$
		2. Substitute the initial conditions to the pseudo equation, calculate _A_ and _B_.
	+ Special case: 
	2 same solution-> $a_{n} = A\lambda\_{1}^{n}+bn\lambda\_{1}^{n}$	+ Non-homogeneous 

__Generating function__

Now define $a\_{1},a\_{2},a\_{3},...a\_{n}$ define by some recurrence relation, $f(x)=a\_{1}x^{1}+a_{2}x^{2}+...+a{n}x^{n}$ this f(x) is called the gearing function of the sequence. Idea: find f(x) and then represent it as a formal sense too solve an

+ power series:	
	+ $1+x+x^{2}+... = \frac{1}{1-x}$

+ GF approach to solve the recurrence function
	1. set $f(x)=a\_{1}x^{1}+a\_{2}x^{2}+...+a\_{n}x^{n}$ use the initial condition and the recursive relation to rewrite f(x)
	2. Collect the terms in f(x), so f(x) show the RHS as well. Solve for f(x).
	+ Use partial fraction to break f(x) into elementary fraction $\frac{A}{1+Cx}$
	+ Represent the generality function using power series, and then represent $a\_4, a\_5, a_6$ representatively and then guess the solution. 
	
__Catalan Numbers__

+ the An

	+ ${2n \choose n}-{2n \choose {n+1}}=\frac{1}{n+1}\*{2n \choose n}$
	

__Derangement__

+ recurrence function
	+ $d\_{n}=(n-1)(d\_{n-1}+d_{n-2})$
	+ $d\_{n}-nd\_{n-1}=(-1)^n$
	+ $\frac{d_{n}} {n!}=\frac {1}{e}$
	
Graphic Theory
---
+ Definitions
	
	+ graph
	
		A graph G is given by 2 pieces of data.

		+ V : vertices of the graph
		+ E : edges of the graph
			+ e includes in E, e = (v1,v2): pair of vertices
		+ p: number of vertices
		+ q: number of edges
		+ r: number of regions
		+ path: the sequential combination of vertices.
		+ Cycle: Path with the same starting and ending point
		+ kn: complete graph on n vertices
		+ deg(degree)
	
			1. Given a vertex r includes in v, denote by deg(r), the number of edges started by r. 
				+ pendant vertex: deg = 1
			2. It can also become the edges that bounded a region
			
		+ Connected 
		
			A graph G is connected if for any pair of vertices u, v INCLUDE V there exists a path starting at u and ending at v. 
			Otherwise, G is not connected, and it consists of k≥2 connected components. 
			+ To prove an image is connected, use proof	 by	 contradiction

		+ tree: A connected graph with no cycles is called a tree. 
			+ __properties__
				1. A connected graph G is a tree iff q = p-1(#of edges is one less than # of vertices)
			+ root: pendant vertices = "leaves"
			+ binary trees(rooted)
				degree of root is 2, degree of leaves =1, degree of insides = 3
				deg("leave") = 1; deg("inside");deg(root) = 2
		+ bipartite graph
			+ V = B U W (All edges connect Black to White)
			+ G is bipartite <=> G has only even cycles => degree of region>4
		+ spanning tree
			+ def: Given a graph G, remove some edges from it, so tG remain connected but has no cycles. This result in a tree, which we call a spinning tree of G
			+ Problem: Find the minimal spanning tree of G (i.e.,, the spanning tree for which the sum of the edge weight is the smallest possible)
			+ Algorithms1
				1. start with the smallest edge
				+ keep adding edges, each time choosing the smallest available if this avoids forming a cycle
				+ once you included all vertices, ends
			+ Algorithms2: prim's algorithm
				1. Choose a starting vertex Find the smallest edge from this vertex
				+ On each step, add the smallest edge which connect one of the vertices included in the tree to one of the verities not yet included
				+ when you reduced all the vertices, stop. 
		+ planar graph
			+ def: We say that the graph G is planar if it allows the plane picture 
		    + 反例： 五角星＋五边形
		    + 证明:		
				1. Let G be a planar graph, and let r be the number of region in its plane picture(counting the outside)
					+ __the deg R(Region) = # of edges we encounter travel through the region__
			+ __Theorem(Euler's Formular): for a planar graph p-q+r = 2__
			+ Kuratowski's theorem  
				+ if a graph contain $K_{5}$ or $K\_{3,3}$ it would be a non-planar graph
			+ __How to judge whether the graph is planar or not__
				1. Use Euler's formula to  calculate the region: r = 2-p+q
				2. calculate the smallest region's degree
				3. Use the two handshake lemma to verify whether they consist: 2q ?>= r*min(deg(r))
		
	+ regular solids(polyhedra)：(m,n) = (3,3);(3,4);(4,3)(3,5)(5,3)
		+ regular solid: n edges meeting at every vertex
		+ m edges founding every region(face)
			1. p-q+r=2(plannar graph)
			+  2q=pn(HL1)
			+ 2q = rm(HL2)
				1. 2q/n-q+2q/m=2
				+ 2qm-qnm+2qn=2nm>0
				+ q(2m+2n-nm)>0
				+ nm -2n -2m<0
				+ nm -2n-2m +3<4
				+ (n-2)(m-2)<=3
+ property: 
	+ handshake lemma: ∑deg = 2 q
		1. Sum of all verteces degrees is twice the number of edges. 
		+ In particular, the sum of degrees is always even. 
	+ handshake lemma2: 
		1. In a connected plane graph, 21 = sum of degrees of the regions.
	+ Kn is planar only if n≤4
	+ Kuratowski's theorem
		+ A graph is planar iff it does not contain a subdivision of K5 or K3,3

Traveling round a Graph
---
+ Hamilton graphs
	+ Definition
		1. A __hamiltonian cycle__ in a graph G is a cycle containing all the vertices of G
		2. A __hamiltonian graph__ is a graph containing a hamiltonian cycle
		+ A __grid code__ of order n is a cyclic arrangement of the $2^{n}$ binary sequences of length n such that any pair of adjacent sequences differ in only one place.
		+ Eulerian Graphs 
			+ An eulerian circuit is a closed trail which contains each edge of the graph. A graph which contains an eulerian trail is called an eulerian graph. 
			+ An eulerian trail is a trail which contains evert edge of the graph, but is not closed. A non-eulerian graph which contains an eulerian trail is called a semi-eulerian graph. 
	+ Theorem 
		1.  A bipartite graph with an odd number of vertices cannot be hamiltonian. 
			+ Kn is hamiltonian for all N≥3
			+ Km,n is hamiltonian iff m=n≥2
		+ Theorem 4.2(Dirac Theorem)
			+ If G is a simple graph with p vertices, each vertex having $degree \geq \frac{1}{2}p$, then G is hamiltonian. 
		+ Let G be a graph in which every vertex has even degree. then the edge set of G is an edge-disjoint inion of cycles. 
		+ 4.4: let G be connected graph. Then G is eulerian iff every vertex has even degree. 
		+ A connected graph G is semi-eulerian iff it contains precisely two vertices of odd degree. 
	+ Algorithm
		+ planarity algorithm for hamiltonian graph
			1. Draw the graph G with hamiltonian cycle H on the outside
			2. List the edges of G not in H:  $e_{1},e\_{2},...,e\_{r}$ 
			3. For a new graph K in which the vertices are labeled $e_{1},e\_{2},...,e\_{r}$, if crossed, the draw the edges of these two vertices
			4. Then G is planar if and only if K is bipartite
		+ TSP: Traveling Salesman problem 
			+ Find lower bond of TSP: Solution to TSP $\geq [sum\ of\ lengths\ of\ two\ shortest\ edges\ from\ v]+[MST\ of\ G-v]$. MST: minimal length of spanning tree(greedy, prism algorithm)
			+ Find the upper bound of the graph: 2 MST
		+ construct high level Gird code
			+ start from 0,1-> append reverse: 1,0 add 00,11 to the end: 00,10,11,01
				1. start from last level 	2. add the reverse oder of that. 3. append 0 to all original sequence, append 1 to reversed sequence. 
			
	
Partitions and Coloring
---
A partition of a set S is a collection of non-empty subsets $S_{1},...,S\_{r}$ of S which are pairwise disjoint and whose union is S.   

+ Definition 
	1. A partition of an n-element set consisting of $a_{i}$ subsets of size i, $1\leq i \leq n$, where $\sum\_{n}^{i=1} i\alpha\_{i} = n$, is called a partition of type $1^{\alpha\_{1}}2^{\alpha\_{2}}r^{\alpha\_{r}}$
	2. Let $S(n,k)$ denote the number of ways of partitioning an n-set into exactly k parts. Then $S(n,k)$ is called a __stirling number of the second kind__.
	3. The __chromatic number__ $\chi (G)$ of a graph G is the smallest value of k for which the vertex set of G can be partitioned into k independent subsets. 
		+ In other word, this is the smallest number of color that we need to color all vertices in G without adjacent vertices.
		+ Edge coloring is similar, where the term become chromatic index and denoted by $\chi '(G)$
+  Theorem 
	1. A set of mn objects can be partitioned into m sets of size n in $\frac{(mn)!}{(n!)^{m}m!}$
	2. The number of partitions of type $1^{\alpha\_{1}}2^{\alpha\_{2}}r^{\alpha\_{r}}$ of an n=element set is $\frac{n!}{\prod_{i=1}^{n}(i!)^{a\_{i}}a\_{i}!}$
	3. $S(n,1) = S(n,n)=1$
	4. $S(n,k)=S(n-1,k-1)+ kS(n-1,k)$ and $1<k<n$
	5. For all $n \geq 2, S(n,2)=2^{n-1}-1$
	6. Bell number $B(n) = \sum_{k=1}^{n}(n,k)$ for $n \geq 1$
	7. Accept B(0) =1 = S(0,0), we'll have $B(n)=\sum_{k=0}^{n-1}{n-1 \choose k}B(k)$
	8. For all $n \geq 1, B(n)= \sum_{k=0}^{n-1} {n-1 \choose k} B(k)$
	9. Let |X|=m,|Y|=n where $m,n \geq 1$. (a) The number of functions f: X->Y with image of size k is $S(m,k){n \choose k} k!$ (b) $n^{m}=\sum_{k=1}^{n}S(m,k){n \choose k}k!$
	10. (i) $\chi (K_{n})=n$ (ii) $\chi (C\_{n}) = 2$ if n is even, $\chi (C\_{n}) = 3$ if n is odd. 
	11. If G has maximum vertex degree $\Delta$, then the greedy algorithm will color the vertices of G using at most $\Delta +1$ colors, so that $\chi (G) \leq \Delta +1$ .
	12.  (i) $\chi '(K_{n})=n$ if n is odd. (ii) $\chi '(K\_{n})=n-1$ if n is even
	13.  If G is a simple graph has maximum vertex degree $\Delta$, then $\chi '(G)=\Delta$ or $\Delta +1$.
		+ $\chi '(G)=\Delta$ class 1
		+ $\chi '(G)=\Delta +1$ class 2
	14. $\chi '(G)=\Delta$ for all bipartite graphs(which means it's class 1)
	 
+ Algorithms
	+ The greedy algorithm for vertex coloring 
		1. List the vertices in some order: $v_{1},v\_{2},...,v\_{p}$
		2. Assign $C_{1}$z to $v\_{1}$. 
		3. At stage i+1, when $v\_{i}$ has just been assigned a color, assign to $v\_{i+1}$ the color $C\_{j}$ with j as small as possible which has not yet been used to color a vertex adjacent to $v\_{i+1}$
+ Examples
	+ How to calculate a stirling number. 
		+ s(7,4)=$1^{3}4^{1}+1^{2}2^{1}3^{1}+1^{1}2^{3}$

	
Inclusion and Exclusion principal 
---
+ One important theorem
	+ $N =\sum N(i) - \sum N(i,j)+ \sum N(i,j,k)-...+ (-1)^{r}\sum N(1,2,3...,r) $

Prime Numbers
---

- Definition
	- GCD: Greatest Common Divisor
		+ Denote by GCD(a,b): the largest common divisor between a and b. 
	- Relatively Prime
		- If GCD(a,b) =1, we say that a,b are relationally prime. 
	- Mod n arithmetic: Ring of integers modula
		- $Z\_{n} = { \bar{0} \bar{1}\bar{2}\bar{3}...\bar{n-1}}$
		- You can have either + - or * to apply to your system 
	- Given $n\geq 2$， denote by $\phi (n)$, the number of integers between 1 and n-1 which are relatively prime with n. 
		- e.g.: $\phi (12) = 4$
		- $Z\_{n}^{*} = (\bar{m}|gcd(m,n)=1)$
			- $Z\_{12}^{*} = (\bar{1},\bar{5},\bar{7},\bar{11})$
	- Inversion in a Ring
		- If gcd(m,n) = 1 am + bn =1 for some $a, b\in R$, in other words $\bar{a}*\bar{m} = \bar{1}$, so $\bar{a}$ is the inverse of $\bar{b}$
- Theorem 
	- If a, b are relatively prime, we say there must exist $xa+yb = 1$
	- We have infinite numbers of primes. 
		- To prove: list all prime number from p1 = 2 to pn, than N= p1+...+pn+1. 
	- If gcd(a,b)=1, we say that a.b are relatively prime. 
		- If a,b are relationally prime. 
	- Euclid: p = prime, p|ab. Then either p|a, or p|b, 
	- Euler's Phi
		- $|Z\_{n}|=\phi(n)$
		- $\phi(pq) = (p-1)*(q-1)$, where $p$ and $q$ are prime number. 
	- Fermat's little theorem: 
		- If p is prime, $\bar a\neq \bar 0$, then $\bar a^{p-1} \equiv 1 \pmod p$
	- 
- Algorithm
	- Prime Sieve
		- Given a positive integer n, this algorithm computes a list of the primes up to n 
		- [Initialize] Let X = [3;5; : : :] be the list of all odd integers between 3 and n. Let P = [2] be the list of primes found so far.
		- [Finished?] Let p be the rst element of X. If p $\geq p_{n}$, append each element of X to P and terminate. Otherwise append p to P.
		-  [Cross O] Set X equal to the sublist of elements in X that are not divisible by p. Go to Step 2.
	- Construct $xa + yb =1$
		- Assume we have $(a\_{2},a_{1})$ where $a\_{2}<a\_{1}$
		- First get $a\_{1}/a\_{2} = x\_{1}....a\_{3}$, where $a\_{3}$ is the module result and $x\_{1}$ is the quotient of the result. 
		- continue construct the sequence, $a\_{2}/a\_{3} = x\_{2}....a\_{4}$, $a\_{3}/a\_{4} = x\_{3}....a\_{5}$,..., until reaches $a\_{n-1}/a\_{n} = x\_{n-1}....a\_{n+1}$, where $a_{n+1} = 1$. 
		- Construct the result as $1 = a\_{n-1}-x\_{n-1} a\_{n} = a\_{n-1}-x\_{n-1}(a\_{n-2}-x\_{n-1}a\_{n-1})...$ until reaches $a\_{1}\ and\ a\_{2}$
	- Chinese reminder theorem  
		Theorem given relatively prime m and n, and a(0≤a<m) and b(0≤b<n), there exists $x\in Z$ such that $x \equiv a \pmod m$ and $x \equiv b \pmod n$. Moreover, if we also require 0≤x<mn, such an x is unique. 
		1. Since gcd(m,n)=1, we can find C & D such that 1 = Cm-Dn
		2. set y = cm($y \equiv 0 \pmod m$, $y \equiv 1 \pmod n$)
		3. Now x = a+(b-a)y, we get $x \equiv a \pmod m$, and $x \equiv b \pmod n$ as desired
- Examples
	- Quiz last: find $3^{21} \pmod 17$: construct a ring with length 17, in other word construct a $Z_{17}$, done all the calculations there.  
	
Public key encryption
---
- Public(private) key idea  
	1.  Generate 2 large primes, p & q
		2. Take n = pq
		3.  $\phi (n) = (p-1)*(q-1)$-> kept private
	2. trace $ e \nmid \phi (e)$, find $d = e^{-1}$ in $R_{\phi (n)}$
	3. transmit the public key (n,e) to the user, the private key is d
	4. user's message is  $x \in R_{n}$
	5. user computes $\bar y = \bar x ^{e}$ and transmits $\bar y$
	6. the bank computes $\bar y^{d}$
		- prove:1. $\bar y^{d} =  (\bar x^{e})^{d} = \bar x^{ed}$ 2. $de = 1 \pmod \phi (n)$ 3. $de = 1+r \phi (n)$ 4. $\bar x^{ed } =\bar x\* (\bar x^{\phi(n)})^{r} = x \pmod n$
- Fermat's attack  
	- works when p & q are close. q<p, p-q<5p^{1/2}
	- Using to factor n = pq(p q are prime)
	- To avoid the Fermat's attack, please use p  = 2q
	- Algorithm: 
		1. compute $t_{0} = (n^{\frac{1}{2}})$
		2. For $t = t\_{0}+1,  t\_{0}+2, t\_{0}+3, ..., t\_{0}+n$, calculate $s = (t^{2}-n)^{\frac{1}{2}}$
		3. Stop when you obtain $s \in R$(where the s is a integer)
		4. If you try for a while and does not get the result, please gave up
		
	
	
Reference
---
###[1] Class notes from [Dr. Alexander Dvorsky](https://sites.google.com/site/dvorsky/), [Class Twitter](https://twitter.com/mth309p)
###[2]  [A first Class in Discrete Mathematics](http://www.amazon.com/Course-Discrete-Mathematics-Springer-Undergraduate/dp/1852332360)
###[3]  [Elementary Number Theory: Primes, Congruences, and Secrets](http://wstein.org/ent/)
