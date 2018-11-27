---
layout: post
title: Reinforcement Learning Series - 03
published: true
---

_**This is a part of series of Blogs on Reinforcement Learning (RL), you may want to go through earlier Blogs [Reinforcement Learning Series - 01](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_01/)
[02](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_02/)
before this blog.**_

In first two post I covered basic concepts, LEGO blocks of reinforcement learning and briefly covered fundamental concept of MDP, Bellman equations and Dynamic programming.

In this post I will go in details about back-up diagram. As picture tells a thousand story, its important to understand back-up diagram. Backup process (Update operation) is the graphical representation of algorithm by representing state, action, reward etc.. Value function is transferred back to a state (or a state-action) from its successor state.

In a back-up diagram State value is represented by a hollow circle while a state-action value or action value is represented by a solid circle. Action is represented by a arrow. Reward is conventionally shown after the action value. Action that result in maximum action value is shown here as Argmax. Refer to below diagrams for standard depiction of different representation

![Backup Diagram Notation](/images/backup1.png "Backup Diagram Notation")

**Backup diagram of State Value function under a stochastic policy π**

Now first I will go through how a state value can be shown using backup diagrams.
![Backup Diagram State Value](/images/backup2.png "Backup Diagram State value")

As shown in above diagram.
  - [ ] s is the starting state and it is the root node
  - [ ] from state s there can be three action as shown by arrow and agent take action as per policy π
  - [ ] state action value or action is shown by solid circle (it is the convention that action is taken from a state and reward is received after the action is taken ).
  - [ ] Once action is taken the agent can end up in different state if it is a stochastic environment. I have shown 3 possible state that agent can land into after the right most action is taken. 3 transitions are shown in blue arrow with transition probability reward obtained is r which also depends on transition dynamics.

**Backup diagram of State-Action Value function under a stochastic policy π**