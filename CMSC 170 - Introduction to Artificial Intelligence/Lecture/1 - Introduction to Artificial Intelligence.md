---
Type:
  - Lecture
---
# What is AI?
**Artificial Intelligence**
- **Computational model** of *human behavior*
    - Models that can be translated into computer programs that behave (externally) like humans.
- **Computational model** of *human thought processes*
    - Programs that operate (internally) the way humans do.
- **Computational systems** that *behave intelligently*
    - Programs that act and think intelligently.
- **Computational systems** that *behave rationally*
    - Being able to do good, or better, or best.
## Applications of AI

- Monitor trading in stock exchange
- Detect fraud (e.g. email fraud, phishing activity)
- Schedule classes (e.g. take classes in the same building)
- Automatic ventilator regulator in medical patients
# What is an AI Agent?
**AI Agent**
- A computer program that gathers information about the environment and takes action based on the information gathered.
    - This is an agent-environment dichotomy.
- Acts in behalf of humans (e.g. robot, web shopping program, traffic control system)
## World Model

**Action Space** $(A)$
- Contains all possible actions that the agent can do
- Could be continuous or high-dimensional

**Percept Space** $(P)$
- Contains all possible things that the agent can perceive in the world
- Could be continuous

**The Environment** $(E)$
- Maps strings of actions into percepts $E: A*\to P$
- Some new action that the agent does to the environment generates a percept
    - If you do something to an environment, the result can be perceived by the agent.

**Internal State** $(S)$
- The environment $(E)$ might have internal state $(S)$ that is not visible to an agent
- $E$ may be described using two functions:
    - **Perception Function** $S\to P$
        - What percepts the agent will receive as a function of the current state of the environment?
        - The environment produces a percept (or possibly a set of percepts) based on its internal state.
    - **World Dynamics** $S\times A\to S$
        - What the next state will be, given the previous state and the action of the agent.
        - The environment updates its state when an agent acts on it.

![[Pasted image 20250817145620.png]]

**Utility Function** $(U)$
- Mapping from states of the world (or sequences of states) to real values $(S\to\mathbb R\text{ or }S*\to\mathbb R)$
- It is meant to tell the agents how valuable the states of the world are from your perspective, indirectly telling the agent what you want to do.

---

Our problem as AI designers is to build an agent (or software) in such a way as to get a lot of utility. Basically an optimization problem.

**The Agent Design Problem**
- Find a mapping of sequences of percepts to action that maximizes the utility of the resulting sequence of states $(P*\to A)$.

# Rationality

**Rational Agent**
- Takes actions it believes will achieve its goals.

**Rationality Example**
- **Action:** Bring Umbrella
- **Belief:** It will rain according to forecast
- **Goal:** To not get wet

**Rationality is not omniscience**
- Assume that the most recent forecast is "it will rain" but I did not hear about it, so I did not bring my umbrella. That is rational since I did not know about the forecast.

**Rationality is not success**
- Suppose that the most recent forecast is "it will not rain", but I still brought my umbrella and used it to defend myself an attack. That is not rational since I brought my umbrella for the wrong reason even though I was successful.

**The problem with this definition of rationality**
- This definition of rationality is still not a good enough notion to decide what should go in the head of our agent. The agent might not be able to compute the best action subject to its beliefs and goals.

**Limited Rationality**
- Acting the best way you can subject to the computational constraints that you have.
- Same topic in Philosophy: Humans are bad at doing a variety of tasks, we just can't compute the optimal response in certain circumstances.
- We need to program the agent's head that's going to last for the agent's whole range of things it has to do and life it has to live.

**The Agent Design Problem (v2)**
- Find a mapping of sequences of percepts to action that maximizes the utility of the resulting sequence of states $(P*\to A)$ subject to our computational constraints.

# Issues

**How could we possibly specify completely the domain the agent is going to work in?**
- If you expect a problem to be solved, you have to say what the problem is.
- Specification is usually iterative: Build agent, test, modify specification.

**Why isn't this "just" software engineering?**
- There is a huge gap between specification and the program.

**Isn't this automatic programming?**
- It could be, but AP is so hard most people have given up.
- We're not going to construct programs automatically. We're going to map classes of environments and utilities to structures of programs that solve that class of problem.

---

**Thinking**
- If we can enumerate all mappings $S\to P$, then we have a table of state and the corresponding percept, but even if the environment does not change, the table is too big. 
- There are too many states and consequences of percepts. There is no way a programmer could, offline, anticipate them.
- With some AI practitioners, the required reaction table can be specified compactly in a program. These are the domains that are the target of the "embodied AI" approach.
- In our approach, we'll take advantage of the fact that most things that could happend don't.
    - E.g. there is no reason to pre-compute reactions to a whale flying inside your home or pre-computing your reaction to your crush when they do not know that you exist.

**Learning**
- If you don't know much about the environment when you start or if it changes, then you need to learn.
    - E.g. sending a robot to other planets but we don't know the coefficient of friction of the dust on the other planet's surface.
- Part of the agent's job is to use sequences of percepts to estimate the missing details in the world dynamics.

# Classes of Environment

**Accessible (vs Inaccessible)**
- Can you see the state of the world directly?

**Deterministic (vs Non-deterministic)**
- Does an action map one state into a single other state?

**Static (vs Dynamic)**
- Can the world change while you are thinking?

**Discrete (vs Continuous)**
- Are the percepts and actions discrete or continuous?

---

**Example: A robot jeepney driver along the Calamba-College route.**

- **Accessible or inaccessible:** Can the robot driver see everything along the route?
    - **Inaccessible**, the robot driver cannot see everything, especially depending on how it senses the world (using sensors and/or cameras).

- **Deterministic or non-deterministic:** Does the action of the robot driver result into only one event?
    - **Deterministic**, the agent's actions should only result in one event, e.g., if it wants to stop, the jeepney will stop, not speed up or change lanes.

- **Static or dynamic:** Does the route status change while the robot driver is deciding?
    - **Dynamic**, the route status can change under other influences outside the robot driver's control.

- **Discrete or continuous:** Does the robot see continuous action?
    - **Continuous**, depending on the input, but 60 fps machine vision may be classified as continuous.

