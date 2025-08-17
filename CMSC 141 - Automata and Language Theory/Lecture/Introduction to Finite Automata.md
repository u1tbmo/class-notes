# Key Ideas
**Automaton**
- A **theoretical machine** that **accepts or rejects input strings** or performs string processing
**Formal Language**
- A finite or infinite **set of strings**
# Automaton Example
![[Pasted image 20250817151307.png|332x202]]

$$
L=\{a,\ ab,\ aba,\ abab,\ ababa,\ \ldots\}\\
$$
- $L$ is a set of strings $x$ over the alphabet $\Sigma=\{a,\ b\}$, such that $x$ starts with an `a` and alternates with a `b`.
- Double-ringed states are **accepting/final states**. An automaton accepts a string if it ends in a final state.
- States $q_3$ and $q_4$ are **"trap states"**. Strings that pass through them **never get accepted**.
## Quick Exercises

1. What language or set of strings does this one-state automaton accept?
	**![[CMSC 141 - Automata and Language Theory/images/image.png|291x317]]
	Answer:** An empty string or any string that only contains characters from the alphabet $\Sigma = \{a,\ b\}$.

2. Do we really need two trap states in the previous example? Can we merge the two trap states?
	![[image 1.png|302x213]]
    **Answer:** The automaton can be simplified by having one trap state instead of two.

4. Is there an equivalent automaton for our example with only three states? Why or why not?
    **Answer:** There is no equivalent automaton with only three states for the example. A three-state automaton cannot distinguish all the necessary language components. We need four states:
    1. **Initial** ($q_0$): Represents the beginning of the string. Is non-final since empty strings are not accepted.
    2. **Accepting** ($q_1$): Represents strings that start with `a` and are valid.
    3. **Accepting** ($q_2$): Represents strings that continue the accepted pattern (alternating between `a` and `b`). The loops between states $q_1$ and $q_2$handle strings like `ab`, `aba`, `abab`, etc.
    4.  **Non-Accepting** ($q_3$): Represents strings that start with `b` or strings with the substring `aa` or `bb`.

5. Design a similar automaton that accepts all **alternating strings** over $\Sigma=\{a,\ b\}$ and can start with either `a` or `b`.
	![[image 2.png|291x317]]
	**Answer:** The previous example can be extended to the following automata that can handle alternating strings over $\Sigma=\{a,\ b\}$.
# Why we study automata and formal languages

1. They form the **foundations** in many areas of computer science.
2. These topics (like logic and many other branches of math) will forever be classics.
3. Working with abstract machines and languages train the mind. You will be better programmers and analysts after this course.
4. **Lots of applications** in language/compiler design, natural language translation, fractal graphics, bioinformatics, et cetera.

