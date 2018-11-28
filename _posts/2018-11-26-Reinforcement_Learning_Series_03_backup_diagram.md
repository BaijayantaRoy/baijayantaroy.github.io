---
layout: post
title: Reinforcement Learning Series - 03 (Backup Diagram)
published: true
---

_**This is a part of series of Blogs on Reinforcement Learning (RL), you may want to go through earlier Blogs [Reinforcement Learning Series - 01](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_01/)
[02](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_02/)
before this blog.**_

In first two post I covered basic concepts, LEGO blocks of reinforcement learning and briefly covered fundamental concept of MDP, Bellman equations and Dynamic programming.

In this post I will go in details about backup diagram. As we know picture tells a thousand story, backup diagram gives a visual representation of different algorithm and models. 

Backup process (Update operation) is the graphical representation of algorithm by representing state, action, reward etc.. Value function is **transferred back** to a state (or a state-action) from its successor state.

In a back-up diagram State value is represented by a hollow circle while a state-action value or action value is represented by a solid circle. Action is represented by a arrow starting from a state. Reward is conventionally shown after the action value. Action that result in maximum action value is shown as a arc surrounding a state. Refer to below diagrams for standard depiction of different representation

![Backup Diagram Notation](/images/backup1.png "Backup Diagram Notation")

**Backup diagram of State Value function under a stochastic policy π**

Now first I will go through how a state value can be shown using backup diagrams.
![Backup Diagram State Value](/images/backup2.png "Backup Diagram State value")
As shown in above diagram:
  1. [ ] s is the starting state and it is the root node
  2. [ ] from state s there can be three action as shown by green arrow and agent take action as per policy π
  3. [ ] state action value or action is shown by solid circle (it is the convention that action is taken from a state and reward is received after the action is taken ).
  4. [ ] Once action is taken the agent can end up in different state if it is a stochastic environment (in a deterministic environment agent end-up in a specific state). I have shown 3 possible state that agent can land into after the right most action is taken. 3 transitions are shown in blue arrow with transition probability p. Reward obtained is r which also depends on transition dynamics and the action taken.

**Backup diagram of State-Action Value function under a stochastic policy π**
Similar to State value function we can create backup diagram for action value function or state-action value function. In this case root node is solid circle.
![Backup Diagram Action Value](/images/backup4.png "Backup Diagram Action value")

In below backup diagram I show how each components can be seen for a better intuition.

![Backup Diagram Complete](/images/backup3.png "Backup Diagram Complete")

  1) Value of the state is v~π~(s) at state s
  2) From state s, agent can take 3 actions (a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>)
  3) Action value is q<sub>π</sub>(a,s) for the action taken wheren a = {a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>}
  4) After the action a<sub>3</sub> is taken agent can land in state s'<sub>1</sub>, s'<sub>2</sub> or s'<sub>3</sub> and transition probability is p<sub>1</sub>, p<sub>2</sub> or p<sub>3</sub> respectively (note similary there would be state should agent choose action a<sub>2</sub> or a<sub>3</sub> and corresponding transition probability would be there
  5) Reward collected is shown as r<sub>1</sub>, r<sub>2</sub> or r<sub>3</sub> based on state it landed.
  
a^b^
a~1~
