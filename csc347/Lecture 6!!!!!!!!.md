##### Weird Quirks
**Connectness in a directed graph :**
- **Weak connected:** Edges that connect any two vertices
- **Strong connected:** (assumed in Djkra Algo) 
**Negative Weights**
What is the situation when some weights are negative? 
- We take minimums in the algorithm, negatives break this.
- ![[Pasted image 20241009131951.png]]
- We can try this, but it fails!!!!
	- ![[Pasted image 20241009132134.png]]
![[Pasted image 20241009132700.png]]
**A flow must**:
1. $f(u,v) \leq c(u,v)$ for all u,v in $v^2$
2. At amy vertex, flow in is flow out.
![[Pasted image 20241009133145.png]]
Let us now consider another example:
Can we do better then this? Let us attempt.
![[Pasted image 20241009134821.png]]
#### Ford Fulktson Algorithm
`Input: (G,s,t,c)` [ a flow network info]
```
def algo(G,s,t,c):
Initialize f as a the function from V x V -> R^{>0}
While (there exists an augmenting path in the residual network induced by f):
	Augment the flow along p
return f(what the hell does this mean?)
```
In the example the following in the residual network induced by g in G
- ![[Pasted image 20241009135741.png]]
- By augmenting, we basically remove some paths or don't even consider them at all because they aren't worth even considering.
The entire idea is __improvement__ as we start with the trivial and move our way up(?)
**Residual Network:**
- This is just the graph with same vertices and edges induced by f
-$$
c_{f}(u,v) = \begin{cases}
c(u,v)-f(u,v) & \text{ if (u,v) in E}\\ \\
(u,v) & \text{ if (v,u) in E}\\ \\
0 & \text{ else}\\
\end{cases}
$$

