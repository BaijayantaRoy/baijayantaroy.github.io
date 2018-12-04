---
layout: post
title: Reinforcement Learning Series - 05 (Temporal-Difference learning )
published: true
---

_**This is a part of series of Blogs on Reinforcement Learning (RL), you may want to go through pervious Blogs [Reinforcement Learning Series](https://baijayantaroy.github.io/)**_

In this blog I will cover Temporal-Difference Learning methods. Temporal-Difference(TD) method is a blend of Monte Carlo (MC) method and Dynamic Programming (DP) method.

Below are key characteristics of Monte Carlo (MC) method:

1. There is no model (agent does not know state MDP transitions)
2. agent **learn** from **sampled** experience (Similar to MC)
3.  Like DP, TD methods update estimates based in part on other **learned estimates**, without waiting for a final outcome (they **bootstrap** like DP).
4. It can learn from **incomplete episode** thus this method can be used in continuous problems as well
5. TD updates a guess towards a guess and revise the guess based on real experience

Consider a real life analogy; if Monte Carlo learning is like annual examination where student completes its episode at the end of the year. Similarly we have TD learning , can be thought like a weekly or monthly examination (student can adjust their performance based on this score (reward received) after every small interval and final score is accumulation of the all weekly tests (total rewards)).


### **TD(0)**

![TD(0)](/images/TD03.png "TD(0)")

### **SARSA**

![SARSA](/images/TD04.png "SARSA")

### **Q-Learning**

![TD(0)](/images/TD02.png "TD(0)")

### **Expected SARSA**

![Expected SARSA](/images/TD05.png "Expected SARSA")

TD Methods have below advantages :

- TD can learn in every step online or offline
- TD can learn from incomplete sequence
- TD can work in non-terminating environments (continuing)
- TD has lower variance compared to MC as depends on one random action, transition , reward
- Usually more efficient than MC
- TD exploits Markov property and thus more effective in Markov environments

But it has below limitations as well:

- TD is a biased estimation
- TD is more sensitive to initial value
-

That's all for this blog, happy learning.
