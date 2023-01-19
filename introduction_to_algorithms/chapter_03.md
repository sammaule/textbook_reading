*This was a more maths heavy chapter in the book so notes are a bit sparser here as a deep understanding of the underlying maths is not what I'm looking to get from this book.*

When looking at run times of an algorithm we mean their *asymptotic efficiency*. It is normally the case that the asympotically more efficient is the best choice for all but the smallest inputs.

#### 3.1 $O$-notation, $\Omega$-notation, and $\Theta$-notation

$O$-notation : characterises an **upper bound** on the asymptotic behaviour of a function.
$\Omega$-notation: characterises a **lower bound** on the asymptotic behaviour of a function.
$\Theta$-notation: characterises a **tight bound** on the asymptotic behaviour of a function.

If you can state that an algorithm runs in $O(n)$ and $\Omega(n)$ then it follows that it runs in $\Theta(n)$.

#### 3.2 Asymptotic notation: formal definitions

![[Pasted image 20230119095127.png]]

**$O$-notation** - asymptotic upper bound

Formal definition: a function $f(n)$ belongs to the set $O(g(n))$ if there exists a postive constant $c$ such that $f(n) \leq cg(n)$ for sufficiently large n.

The function f(n) must be asymptotically non-negative (this won't be an issue for the case of runtimes)

**$\Omega$-notation** - asymptotic lower bound

Formal definition: a function $f(n)$ belongs to the set $\Omega(g(n))$ if there exists a postive constant $c$ such that $0 \leq cg(n) \leq f(n)$ for sufficiently large n.

**$\Theta$-notation** - asymptotic upper bound

Formal definition: a function $f(n)$ belongs to the set $\Theta(g(n))$ if there exist postive constants $c_1, c_2$ such that $0 \leq c_1g(n) \leq f(n) \leq c_2g(n)$ for sufficiently large n.

You should use asymptotic notation as precisely as possible - often the notation is abused and people use big-O to describe lots of different actual run times.

The = sign in asymptotic notation really means set membership

**$o$-notation** - little o notation used to denote an upper bound that is not asymptotically "tight". The definition is as above but it holds for all values of c not just some values for c as with the big O notation.

$\omega$ -notation - this is the equivalent for $\Omega$-notation

The remainder of the chapter defines mathematical notation and concepts used in the remainder of the book - not worth noting anything additional down.