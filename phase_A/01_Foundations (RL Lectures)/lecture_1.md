## **1. The Reinforcement Learning Problem**

### **The Core Definition**

Reinforcement Learning (RL) is the science of decision-making. It sits at the intersection of many fields like Computer Science (Machine Learning), Engineering (Optimal Control), Neuroscience (Dopamine system), and Economics (Game Theory).

* **The Reward Hypothesis**: All goals can be described by the maximization of expected cumulative reward.


* **The Agent-Environment Loop**: At each time step $t$, the agent takes an action $A_t$, and the environment returns an observation $O_t$ and a reward $R_t$.


* **Relatable Example**: Think of **parenting**. The parent (Agent) takes an action (giving a "timeout"). The child (Environment) provides an observation (crying or silence) and a reward (long-term good behavior or short-term peace).

![agent_environment_loop](./images/agent_environment_loop.jpeg)

---

## **2. State: What determines what happens next?**

### **The History $H_t$**

History is the entire sequence of observations, actions, and rewards up to time t.

### **The Three Definitions of State**

1. **Environment State $S^e_t$**: The environment’s internal set of numbers used to pick the next observation/reward. It is usually invisible to the agent.


* **Relatable Example**: In a **Casino**, the "Environment State" is the exact position of every card in the dealer's deck and the internal mechanism of the slot machine. You can't see this.


2. **Agent State $S^a_t$**: The specific information the agent keeps to make decisions; it is a function of the history.


* **Relatable Example**: In **Poker**, your "Agent State" is your own hand, the cards on the table, and your memory of how your opponent bet in the last round.


3. **Information (Markov) State**: A state is Markov if the future is independent of the past, given the present. You can throw away the history if you have a Markov state.


* **Relatable Example**: A **Battery Level**. If your phone is at 5%, it doesn't matter if it was at 100% five minutes ago or five hours ago; the "future" (when it will die) depends only on the current 5% and your current usage.



---

## **3. Anatomy of an RL Agent**

An agent may have one or more of these components:

* **Policy $\pi$**: The agent's behavior function—a map from state to action.


* **Example**: A **Fire Drill Procedure**. "If the alarm sounds (State), walk to the nearest exit (Action)."


* **Value Function $V$**: A prediction of expected future reward. It helps you choose between states.


* **Example**: A **GPS Estimate**. It doesn't tell you how to drive (that's the policy), but it tells you how "good" your current route is by estimating the remaining time (future reward).


* **Model**: The agent’s internal representation of the environment. It predicts transitions (what happens next) and rewards.


* **Example**: A **Mental Map**. If you close your eyes and imagine walking to your kitchen, you are using a model to predict that "walking forward" will lead to "the fridge."


---

## **4. Categorizing RL Agents**

Agents are categorized by which components they contain:

* **Value-Based**: Has a value function, but the policy is implicit (just pick the highest value).


* **Policy-Based**: Has an explicit policy but no value function.


* **Actor-Critic**: Has both a policy and a value function.


* **Model-Free**: Does not try to understand the environment's dynamics.


* **Model-Based**: Builds a model of the environment first, then plans.



### **The Vacuum Robot Example**

* **Model-Free ("The Bump Bot")**: It has no map. It moves until it hits a wall (Action), receives a "bump" signal (Negative Reward), and learns to turn.


* **Model-Based ("The Lidar Bot")**: It uses Lidar to build a map (Model). It then calculates the best path (Planning) before it even moves, predicting where walls will be.



---

## **5. Learning vs. Planning**

### **Definition**

* **Learning**: The environment is unknown. The agent interacts with the world to figure out how it works.


* **Planning**: The environment is known (the agent has a perfect model/rules). The agent performs internal computations to improve its behavior without real-world interaction.



### **Relatable Example**

* **Learning**: Imagine playing a **New Board Game** where the instructions are missing. You have to move pieces, see if people get mad or happy, and "learn" the rules by playing.
* **Planning**: Imagine playing **Chess**. You know all the rules (the Model). You sit quietly for 5 minutes "planning" (thinking ahead: "If I move here, he moves there...") without actually touching a piece yet.



---

## **6. Prediction vs. Control**

### **Definition**

* **Prediction**: Evaluating the future. Given a specific policy, how much reward will I get? 


* **Control**: Optimizing the future. What is the *best* policy to get the *maximum* reward? 



### **Relatable Example**

* **Prediction**: You ask a weather app, "If I go for a run right now, will I get wet?" You aren't changing your behavior yet; you are just **predicting** the outcome of a fixed plan.
* **Control**: You ask, "What is the **best time** to go for a run today to stay dry?" You are looking for the **optimal action** to take.

---

## **7. Exploration vs. Exploitation**

### **Definition**

* **Exploration**: Trying new things to find more information about the environment.


* **Exploitation**: Using known information to maximize reward.



### **Relatable Example**

* **Exploitation**: Ordering the "Number 5" at your favorite cafe because you know it's delicious.


* **Exploration**: Ordering the "Chef's Special"—something you've never heard of—because it might be even better than the Number 5, even though it might be gross.