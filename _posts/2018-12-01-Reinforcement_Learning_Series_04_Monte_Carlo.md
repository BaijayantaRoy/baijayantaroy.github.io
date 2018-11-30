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

Consider a real life analogy; Monte Carlo learning is like annual examination where student completes its episode at the end of the year. Here result of annual exam is like return obtained by the student. Now if the goal of the problem is to find how students score during a calendar year (which is a episode here) for a class, we can take sample result of some student and then calculate mean result to find score for a class (don't take the analogy point by point but on a holistic level I think you can get the essence of MC learning). Similarly we have TD learning  or temporal difference learning that we will cover in future blog, can be thought like a weekly or monthly examination (student can adjust their performance based on this score (reward received) after every small interval and final score is accumulation of the all weekly tests (total rewards)).

Recall,

Value function = Expected **Return**

Also we can write return as below for T time steps :

**Return(sampled)** = **reward** from time step 1 +
             (discount factor ) times **reward** from time step 2 +
             (discount factor )<sup>2</sup> times **reward** from time step 3 +
             (discount factor )<sup>3</sup> times **reward** from time step 4 +
             (discount factor )<sup>4</sup> times **reward** from time step 5 +
             .
             .
             .
             (discount factor )<sup>T-1</sup> times **reward** from time step T

## **Monte Carlo State Value**
![Backup Diagram MC State Value](/images/backup6.png "Backup Diagram MC State Value")

There are two types of MC learning policy evaluation (prediction) methods:

1. first-visit
2. Every-visit
