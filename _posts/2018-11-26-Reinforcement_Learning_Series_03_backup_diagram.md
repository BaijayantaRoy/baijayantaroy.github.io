---
layout: post
title: Reinforcement Learning Series - 03 (Backup Diagram)
published: true
---

_**This is a part of series of Blogs on Reinforcement Learning (RL), you may want to go through earlier Blogs [Reinforcement Learning Series - 01](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_01/)
[02](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_02/)
before this blog.**_

In first two posts I covered basic concepts, building blocks of reinforcement learning and briefly covered MDP, Bellman equations and Dynamic programming.

In this post I will go in details about backup diagram. As we know a picture is worth a thousand words; backup diagram gives a visual representation of different algorithm and models in Reinforcement Learning.

Backup process (Update operation) is the graphical representation of algorithm by representing state, action, state transition, reward etc.. Value function (state or state-action) is **transferred back** to a state (or a state-action) from its successor state or state-action.

In a backup diagram state value is represented by a hollow circle while a state-action value or action value is represented by a solid circle. Action is represented by a arrow starting from a state. Reward is conventionally shown after the action value. Action that result in maximum action value is shown as a arc starting from a state. Refer to below diagrams for standard representation of state value, action value, action, maximum action value, state transition.

![Backup Diagram Notation](/images/backup1.png "Backup Diagram Notation")
## **State Value function under a stochastic policy π**

Now I will go through how a state value can be shown using backup diagrams.

![Backup Diagram State Value](/images/backup2.png "Backup Diagram State value")

  1. s is the starting state and it is the root node
  2. from state s there can be three action as shown by arrow and agent take action as per policy π
  3. state action value or action is shown by solid circle (it is the convention that action is taken from a state and reward is received after the action is taken ).
  4. Once action is taken the agent can end up in different state if it is a stochastic environment with certain state transition probability (in a deterministic environment agent end-up in a specific state for a specific action). I have shown 3 possible states that agent can land into after the right most action is taken. 3 transitions are shown in blue arrow with transition probability p. Reward obtained is r which also depends on transition dynamics and the action taken. Agent transition to a new state s'.

## **State-Action Value function under a stochastic policy π**
Similar to State value function we can create backup diagram for action value function or state-action value function. In this case root node is solid circle as its a specific action from a specific state.

![Backup Diagram Action Value](/images/backup3.png "Backup Diagram Action value")

In below backup diagram I show how each components are linked for a better intuition. This gives a better understanding of MDP as we can expand this diagram to entire state space.

![Backup Diagram Complete](/images/backup4.png "Backup Diagram Complete")

  1. Value of the state is v<sub>π</sub>(s) at state s
  2. From state s, agent can take 3 actions (a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>)
  3. Action value is q<sub>π</sub>(a,s) for the action taken where a = {a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>}
  4. Here agent has taken action a<sub>3</sub>. It can land in state s'<sub>1</sub>, s'<sub>2</sub> or s'<sub>3</sub> with transition probability p<sub>1</sub>, p<sub>2</sub> or p<sub>3</sub> respectively (note similarly there would be different states should agent choose action a<sub>2</sub> or a<sub>3</sub> and corresponding transition probability would be applicable.
  5. Reward collected is shown as r<sub>1</sub>, r<sub>2</sub> or r<sub>3</sub> based on state it lands.

## **Optimal State Value and Optimal Action Value**
Below diagram shows Bellman Optimality Equation for State value for a specific state s and Bellman Optimality equation for State Action value for action a taken from state s. Its the max action (action that yields maximum state value in successor state) from the state that ensures optimality as per the Bellman Optimality equation.

![Backup Diagram Optimal](/images/backup5.png "Backup Diagram Optimal")

Backup diagram can be used to show graphical representation of RL algorithm those use value function in the equation. Below are few more well known algorithm (I will cover them in future blogs) those can be easily understood when we refer the backup diagram.
## **Monte Carlo State Value**
![Backup Diagram MC State Value](/images/backup6.png "Backup Diagram MC State Value")
## **Monte Carlo State Action Value**
![Backup Diagram MC State Action Value](/images/backup7.png "Backup Diagram MC State Action Value")
## **Temporal Difference TD(0)**
![Backup Diagram TD(0)](/images/backup8.png "Backup Diagram TD")
## **SARSA**
![Backup Diagram SARSA](/images/backup9.png "Backup Diagram for SARSA")
That's all for this blog, happy learning.
