# RL Course by David Silver - Lecture 2: Markov Decision Processes

## 1. The Markov Property

### **Definition**

A state $S_t$ is **Markov** if and only if the probability of the next state depends only on the current state and not the history:
$$P[S_{t+1} | S_t] = P[S_{t+1} | S_1, ..., S_t]$$

### **Explanation**

- The **Markov Property** means the "future is independent of the past, given the present".
- You only need to store the current state $S_t$; once you have it, you can throw away the rest of the history because it doesn't give you more information about the future.
- The state is a **sufficient statistic** of the future.

### **Relatable Example**

- **A Car’s Movement**: If you know a car’s **current position** and **velocity** (the Markov state), you can predict where it will be in one second. You don't need to know if the car started its journey two days ago; that history doesn't change the physics of what happens in the next moment.

---

## 2. Markov Processes (or Markov Chains)

### **Definition**

A Markov Process is a memoryless random process—a sequence of random states $S_1, S_2, ...$ with the Markov property. It is defined by a set of states $\mathcal{S}$ and a **State Transition Matrix** $\mathcal{P}$.

### **Explanation**

- This is the simplest version of the framework.
- It describes a system that moves between states automatically based on fixed probabilities.
- There are no actions and no rewards yet; you are just observing the system unfold.

### **Relatable Example**

- **The Weather**: If it is "Sunny" today, there is a fixed 70% chance it will be "Sunny" tomorrow and a 30% chance it will be "Rainy." You aren't "doing" anything to change it; you are just watching the sequence of states.

---

## 3. Markov Reward Process (MRP)

### **Definition**

An MRP is a Markov process that adds **Reward** values and a **Discount Factor**. It is defined as a tuple $\langle \mathcal{S}, \mathcal{P}, \mathcal{R}, \gamma \rangle$.

### **Explanation**

- **Reward ($R_t$)**: A scalar feedback signal indicating how well the agent is doing at time step $t$.
- **Return ($G_t$)**: The total discounted reward from time $t$ into the future.
- **Discount Factor ($\gamma$)**: A value between 0 and 1 that makes immediate rewards worth more than later rewards.

### **Relatable Example**

- **A "To-Do List" with Points**:
  - **State**: "Completed Assignment."
  - **Reward**: +10 points.
  - **Discounting**: Getting points _today_ is better than getting them next year because you can use them to buy something now.

---

## 4. The Bellman Equation for MRPs

### **Definition**

The value function $v(s)$ can be broken into two parts: the immediate reward and the discounted value of the next state:
$$v(s) = \mathbb{E}[R_{t+1} + \gamma v(S_{t+1}) | S_t = s]$$

### **Explanation**

- This is a recursive relationship: the value of your current situation depends on the immediate reward plus the value of where you land next.
- It allows us to calculate how "good" a state is by looking just one step ahead.

### **Relatable Example**

- **University Degree**: The "Value" of being in your 3rd year is the reward of learning this year PLUS the discounted "Value" of being a 4th-year student next year.

---

## 5. Markov Decision Process (MDP)

### **Definition**

An MDP is an MRP with **Actions**. It is a tuple $\langle \mathcal{S}, \mathcal{A}, \mathcal{P}, \mathcal{R}, \gamma \rangle$.

### **Explanation**

- This is the full framework for RL.
- Transitions and rewards now depend on the **Action** ($A_t$) the agent chooses.
- The agent actively influences the environment to maximize reward.

### **Relatable Example**

- **Driving a Car**:
  - **State**: An intersection.
  - **Action**: Turn Left or Turn Right.
  - **Transition**: Turning left puts you on a new street (New State).
  - **Reward**: Reaching your destination faster gives a positive reward.

---

## 6. Policies and Value Functions in MDPs

### **Definitions**

- **Policy ($\pi$)**: A map from state to action; it defines the agent's behavior.
- **State-Value Function ($v_{\pi}(s)$)**: Expected return starting from state $s$ following policy $\pi$.
- **Action-Value Function ($q_{\pi}(s, a)$)**: Expected return starting from state $s$, taking action $a$, and then following policy $\pi$.

### **Explanation**

- The goal is to find the **Optimal Policy** ($\pi_{*}$), which achieves the maximum possible reward in every state.
- RL "solves" the MDP by finding this best behavior.

### **Relatable Example**

- **Tic-Tac-Toe**:
  - **$q(s, a)$**: "If I put my 'X' in the corner (Action) while the board looks like this (State), what is my predicted chance of winning?"
  - **Optimal Policy**: The specific set of moves that ensures you never lose.

---

## 7. The Bellman Optimality Equation

### **Definition**

The optimal value of a state is the value achieved by the **best possible action** in that state:
$$v_*(s) = \max_a q_*(s, a)$$

### **Explanation**

- If you know the value of every action ($q_*$), you don't need to overthink; you just pick the action with the maximum value.
- This "greedy" choice leads to the optimal long-term result.

### **Relatable Example**

- **Choosing a Restaurant**: You have three choices (Actions): Pizza, Sushi, or Burgers. If you know exactly how much you will enjoy each one (their $q_*$ values), you simply pick the highest one to have the "optimal" dinner.
