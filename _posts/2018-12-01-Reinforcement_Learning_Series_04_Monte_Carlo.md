---
layout: post
title: Reinforcement Learning Series - 04 (Monte Carlo learning)
published: true
---

_**This is a part of series of Blogs on Reinforcement Learning (RL), you may want to go through pervious Blogs [Reinforcement Learning Series](https://baijayantaroy.github.io/)**_

In this blog I will cover Monte Carlo Method of reinforcement learning. I have briefly covered Dynamic programming (Value Iteration and Policy Iteration) method in 2nd post. In Dynamic programming we need a model(agent knows the MDP transition and rewards) and agent does **planning** (once model is available agent need to plan its action in each state). There is no real learning by the agent in Dynamic programming method.

Monte Carlo method on the other hand is a very simple concept where agent learn about the states and reward when it interacts with the environment. In this method agent generate experienced samples and then based on average return, value is calculated for a state or state-action. Below are key characteristics of Monte Carlo (MC) method:

1. There is no model (agent does not know state MDP transitions)
2. agent **learn** from **sampled** experience
3. learn state value v<sub>π</sub>(s) under policy π by experiencing **average** return from all sampled episodes (value = average return)
4. only after a **complete episode**, values are updated (because of this algorithm convergence is slow and update happens after a episode is Complete)
5. There is no bootstrapping
6. Only can be used in **episodic problems**

Consider a real life analogy; Monte Carlo learning is like annual examination where student completes its episode at the end of the year. Here result of annual exam is like return obtained by the student. Now if the goal of the problem is to find how students score during a calendar year (which is a episode here) for a class, we can take sample result of some student and then calculate mean result to find score for a class (don't take the analogy point by point but on a holistic level I think you can get the essence of MC learning). Similarly we have TD learning  or temporal difference learning (TD learning is like updating value in every time step and does not require wait till end of episode to update the values) that we will cover in future blog, can be thought like a weekly or monthly examination (student can adjust their performance based on this score (reward received) after every small interval and final score is accumulation of the all weekly tests (total rewards)).

![MC analogy](/images/MC01.png "MC and TD analogy")

Value function = Expected **Return**

Expected return is equal to discounted sum of all rewards.

In Monte Carlo Method instead of expected return we use empirical return that agent has sampled based following the policy.

![Diagram MC State Value](/images/MC03.png "MC State Value")

If we go back to our very first example of gem collection, agent follows policy and complete an episode, along the way in each step it collects rewards in the form of gem. To get state value agent sum-up all the gems collected after each episode starting from that state. Refer to below diagram where 3 samples collected starting from State S<sub>05</sub>. Total reward collected (discount factor is considered as 1 for simplicity) in each episode as follows:

![Diagram MC State Value example](/images/MC04.png "MC State Value example")

Return(Sample 01) = 2 + 1 + 2 + 2 + 1 + 5 = 13 gems

Return(Sample 02) = 2 + 3 + 1 + 3 + 1 + 5 = 15 gems

Return(Sample 03) = 2 + 3 + 1 + 3 + 1 + 5 = 15 gems

Observed mean return (based on 3 samples) = (13 + 15 + 15)/3 = 14.33 gems

Thus state value as per Monte Carlo Method, v<sub>π</sub>(S<sub>05</sub>) is 14.33 gems based on 3 samples following policy π.

## **Monte Carlo Backup diagram**

Monte Carlo Backup diagram would look like below (refer to [3rd blog](https://baijayantaroy.github.io/baijayantaroy.github.io/Reinforcement_Learning_Series_03_backup_diagram/) post for more on backup diagram)
![Backup Diagram MC State Value](/images/MC02.png "Backup Diagram MC")

There are two types of MC learning policy evaluation (prediction) methods:

1. first-visit
2. Every-visit

### **First Visit Monte Carlo Method**
In this case in an episode first visit of the state is counted (even if agent comes-back to the same state multiple time in the episode, only first visit will be counted). Detailed step as below:

1. To evaluate state s, first we set number of visit, N(s) = 0, Total return TR(s) = 0 (these values are updated across episodes)
2. The **first** time-step t that state s is visited in an episode, increment counter N(s) = N(s) + 1
4. Increment total return TR(s) = TR(s) + G<sub>t</sub>
5. Value is estimated by mean return V(s) = TR(s)/N(s)
6. By law of large numbers, V(s) -> v<sub>π</sub>(s) (this is called true value under policy π) as N(s) approaches infinity

Refer to below diagram for better understanding of counter increment.

![MC First Visit](/images/MC05.png "MC First Visit")

### **Every Visit Monte Carlo Method**
In this case in an episode every visit of the state is counted. Detailed step as below:

1. To evaluate state s, first we set number of visit, N(s) = 0, Total return TR(s) = 0 (these values are updated across episodes)
2. **every** time-step t that state s is visited in an episode, increment counter N(s) = N(s) + 1
4. Increment total return TR(s) = TR(s) + G<sub>t</sub>
5. Value is estimated by mean return V(s) = TR(s)/N(s)
6. By law of large numbers, V(s) -> v<sub>π</sub>(s) (this is called true value under policy π) as N(s) approaches infinity

Refer to below diagram for better understanding of counter increment.

![MC Every Visit](/images/MC06.png "MC Every Visit")

Usually MC is updated incrementally after every episode (no need to store old episode values, it could be a running mean value for the state updated after every episode).

Update V(s) incrementally after episode S<sub>1</sub>, A<sub>2</sub>, R<sub>3</sub>,....,S<sub>T</sub>
For each state S<sub>t</sub> with return G<sub>t</sub>

N(S<sub>t</sub>) <--  N(S<sub>t</sub>) + 1

V(S<sub>t</sub>) <--- V(S<sub>t</sub>) + (1/N(S<sub>t</sub>))(G<sub>t</sub> - V(S<sub>t</sub>)

Usually in place of 1/N(S<sub>t</sub>) a constant learning rate (α) is used and above equation becomes :

V(S<sub>t</sub>) <--- V(S<sub>t</sub>) + (1/α)(G<sub>t</sub> - V(S<sub>t</sub>)

For Policy improvement, Generalized Policy Improvement concept is used to update policy using action value function of Monte Carlo Method.

Monte Carlo Methods have below advantages :
- zero bias
- Good convergence properties (even with function approximation)
- Not very sensitive to initial value
- Very simple to understand and use

But it has below limitations as well:

- MC must wait until end of episode before return is known
- MC has high variance
- MC can only learn from complete sequences
- MC only works for episodic (terminating) environments

That's all for this blog, happy learning.
