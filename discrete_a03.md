Here are the step-by-step solutions to the problems in Assignment #3, designed using the concepts and methodologies from your Discrete Mathematics lecture slides on Recurrences (LS05) and Asymptotics (LS06).

---

### **Question 1**
**Explain briefly why each of the following can be ignored when determining the asymptotic bounds of $T(n)$:**

#### **a) Constant factors**
* **Justification:** Constant factors depend on machine-specific characteristics (such as compiler optimizations, processor clock speed, and instruction sets) rather than the intrinsic scalability of the algorithm. Asymptotic analysis focuses on how the running time scales as the input size $n$ approaches infinity. In Big-$O$ notation, constant scaling is absorbed by the constant $c$ in the definition $\exists c > 0, n_0 \in \mathbb{N} : T(n) \le c \cdot g(n)$, making the growth rate hardware-independent.

#### **b) Behavior for small values of $n$**
* **Justification:** Asymptotic bounds describe the limiting behavior of functions as $n \to \infty$. For small inputs, low-level overheads can dominate, which may make an asymptotically slower algorithm appear faster. The formal definitions of asymptotic notations (e.g., $O$, $\Omega$, $\Theta$) specify that the bounding relationship must hold only for all $n \ge n_0$. Thus, behavior below this threshold $n_0$ is ignored.

#### **c) Lower-order terms**
* **Justification:** By definition, a lower-order term $h(n)$ relative to a dominant term $f(n)$ satisfies $\lim_{n \to \infty} \frac{h(n)}{f(n)} = 0$ (i.e., $h(n) \in o(f(n))$). As $n$ grows arbitrarily large, the dominant term $f(n)$ grows so much faster that the contribution of $h(n)$ to the total value becomes mathematically negligible.

---

### **Question 2**
**Determine the tightest asymptotic relationship that holds between each pair of functions:**

#### **a) $f(n) = 2^n$ and $g(n) = n^{1200}$**
* **Justification:** We evaluate the limit of their ratio:
  $$\lim_{n \to \infty} \frac{2^n}{n^{1200}} = \infty$$
  Since exponential growth always dominates polynomial growth, $f(n)$ grows strictly faster than $g(n)$.
* **Relationship:** $f \in \omega(g)$

#### **b) $f(n) = (\log_2(n))^6$ and $g(n) = \sqrt[1200]{n} = n^{1/1200}$**
* **Justification:** Any positive power of $n$ (no matter how small) eventually grows faster than any polylogarithmic function of $n$:
  $$\lim_{n \to \infty} \frac{(\log_2 n)^6}{n^{1/1200}} = 0$$
* **Relationship:** $f \in o(g)$

#### **c) $f(n) = \log_6(n^{1200})$ and $g(n) = (\log_{1200}(n))^6$**
* **Justification:** We simplify both functions using logarithm rules:
  $$f(n) = 1200 \log_6(n) = \frac{1200}{\log_2 6} \log_2(n) = C_1 \log_2(n)$$
  $$g(n) = \left( \frac{\log_2 n}{\log_2 1200} \right)^6 = C_2 (\log_2 n)^6$$
  Evaluating their limit:
  $$\lim_{n \to \infty} \frac{C_1 \log_2(n)}{C_2 (\log_2 n)^6} = \lim_{n \to \infty} \frac{C_1 / C_2}{(\log_2 n)^5} = 0$$
* **Relationship:** $f \in o(g)$

#### **d) $f(n) = \log_2(n!)$ and $g(n) = n \log_2(n)$**
* **Justification:** Using Stirling's Approximation, $\log_2(n!) = n \log_2 n - n \log_2 e + O(\log n)$. Evaluating the limit of the ratio:
  $$\lim_{n \to \infty} \frac{\log_2(n!)}{n \log_2(n)} = \lim_{n \to \infty} \frac{n \log_2 n - n \log_2 e + O(\log n)}{n \log_2 n} = 1$$
  Since the limit of the ratio is exactly $1$, the functions are asymptotically equivalent.
* **Relationship:** $f \sim g$

#### **e) $f(n) = 2^{|\log_2(n)|}$ and $g(n) = 2^{|\log_3(n)|}$**
* **Justification:** 
  Simplifying both functions for $n \ge 1$:
  $$f(n) = 2^{\log_2(n)} = n$$
  $$g(n) = 2^{\log_3(n)} = 2^{\frac{\log_2(n)}{\log_2(3)}} = n^{\log_3(2)} \approx n^{0.631}$$
  
  Evaluating the limit of their ratio:
  $$\lim_{n \to \infty} \frac{f(n)}{g(n)} = \lim_{n \to \infty} \frac{n}{n^{\log_3(2)}} = \lim_{n \to \infty} n^{1 - \log_3(2)} = \infty$$
  Since the limit is $\infty$, $f(n)$ grows strictly faster than $g(n)$.
* **Relationship:** $f \in \omega(g)$

---

#### **f) $f(n) = 2^{|\log_2(n)|} - n + 1$ and $g(n) = 3^{|\log_3(n)|} - n + 1$**
* **Justification:** 
  Simplifying both functions for $n \ge 1$:
  $$f(n) = 2^{\log_2(n)} - n + 1 = n - n + 1 = 1$$
  $$g(n) = 3^{\log_3(n)} - n + 1 = n - n + 1 = 1$$

  Evaluating the limit of their ratio:
  $$\lim_{n \to \infty} \frac{f(n)}{g(n)} = \lim_{n \to \infty} \frac{1}{1} = 1$$
  Since the limit is exactly $1$, the functions are asymptotically equivalent.
* **Relationship:** $f \sim g$

#### **g) $f(n) = n$ and $g(n) = n^{\cos(\log_2(n))}$**
* **Justification:** Since $\cos(\log_2 n) \le 1$ for all $n$, we have $n^{\cos(\log_2 n)} \le n^1$. Thus, $f(n) \ge g(n)$ holds for all $n \ge 1$.
  By choosing $c = 1$ and $n_0 = 1$, we satisfy the Big-$\Omega$ definition: $f(n) \ge c \cdot g(n)$. 
  No tighter relationship (such as $\Theta$ or $\omega$) holds because when $\cos(\log_2 n) = 1$, $f(n)/g(n) = 1$, and when $\cos(\log_2 n) = -1$, $f(n)/g(n) = n^2 \to \infty$.
* **Relationship:** $f \in \Omega(g)$

---

### **Question 3**
**Using mathematical induction, prove that $T(n) = n \log_2(n) - n + 1$ when $n = 2^k$ (where $k \ge 0$).**

Let $P(k)$ be the proposition that for $n = 2^k$, the recurrence $T(2^k) = k \cdot 2^k - 2^k + 1$ holds.

#### **Base Case ($k = 0$):**
For $k = 0$, $n = 2^0 = 1$.
* From the recurrence: $T(1) = 0$.
* From the formula: $T(2^0) = 0 \cdot 2^0 - 2^0 + 1 = 0 - 1 + 1 = 0$.
* Since $0 = 0$, $P(0)$ is true.

#### **Inductive Hypothesis:**
Assume $P(m)$ is true for some integer $m \ge 0$. That is:
$$T(2^m) = m \cdot 2^m - 2^m + 1$$

#### **Inductive Step:**
We must show that $P(m+1)$ is true, i.e., $T(2^{m+1}) = (m+1) 2^{m+1} - 2^{m+1} + 1$.

Using the recurrence relation for $n = 2^{m+1} \ge 2$:
$$T(2^{m+1}) = 2 T\left(\frac{2^{m+1}}{2}\right) + 2^{m+1} - 1$$
$$T(2^{m+1}) = 2 T(2^m) + 2^{m+1} - 1$$

Substitute the Inductive Hypothesis for $T(2^m)$:
$$T(2^{m+1}) = 2 \left( m \cdot 2^m - 2^m + 1 \right) + 2^{m+1} - 1$$
$$T(2^{m+1}) = m \cdot 2^{m+1} - 2^{m+1} + 2 + 2^{m+1} - 1$$

Simplify by canceling $-2^{m+1}$ and $+2^{m+1}$:
$$T(2^{m+1}) = m \cdot 2^{m+1} + 1$$

Now we expand the target expression for $P(m+1)$:
$$(m+1)2^{m+1} - 2^{m+1} + 1 = m \cdot 2^{m+1} + 2^{m+1} - 2^{m+1} + 1 = m \cdot 2^{m+1} + 1$$

Since both expressions are identical, $P(m+1)$ is true. 

By the principle of mathematical induction, the proposition holds for all $k \ge 0$. Substituting $k = \log_2(n)$ yields:
$$T(n) = n \log_2(n) - n + 1 \quad \text{for } n = 2^k$$

---

### **Question 4**
**Verify the derivation $T(n) \in \Theta(n^{\log_2 3})$ using the Master Theorem.**

The recurrence relation is:
$$T(n) = 3T\left(\lceil n/2 \rceil\right) + 10n$$

This fits the standard form of the Master Theorem:
$$T(n) = a T(n/b) + f(n)$$
where $a = 3$, $b = 2$, and $f(n) = 10n$.

1. **Calculate $n^{\log_b a}$:**
   $$n^{\log_b a} = n^{\log_2 3} \approx n^{1.585}$$

2. **Compare $f(n)$ with $n^{\log_b a}$:**
   We check if **Case 1** of the Master Theorem applies. Case 1 requires:
   $$f(n) = O\left(n^{\log_b(a) - \epsilon}\right) \quad \text{for some constant } \epsilon > 0$$

   Let $\epsilon = 0.5$. Then:
   $$\log_2 3 - \epsilon \approx 1.585 - 0.5 = 1.085$$
   
   Since $f(n) = 10n = O\left(n^{1.085}\right)$, the condition for Case 1 is satisfied.

3. **Conclusion:**
   By Case 1 of the Master Theorem, the asymptotic bound is:
   $$T(n) \in \Theta\left(n^{\log_b a}\right) = \Theta\left(n^{\log_2 3}\right)$$

This verifies the derivation.
---
