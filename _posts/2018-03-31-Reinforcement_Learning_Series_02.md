---
layout: post
title: Reinforcement Learning Series - 02
published: true
---

_**Reinforcement Learning (RL) is one of the most happening field of Machine Learning (ML) and Artificial Intelligence (AI). Though RL existed for many decades, only recently the giant has awaken after explosion in Neural Network based Deep Learning. This blog is an attempt to explain basic concepts of Reinforcement Learning using simple example and explanation that anyone with elementary English knowledge would be able to understand. I am not a native English speaker, thus if you find any error or sentences not conveying right meaning, please drop me a mail and I will try to correct or rewrite. This is a series of Blogs on RL, you may want to go through post 1 before starting this blog.**_

In the first part (link) of the blog I have covered basic terminology needed to understand RL. In this blog I will cover RL problem description using Markov Decision Process (MDP), Bellman equation and solving MDP using Dynamic Programming. 
I briefly mentioned Exploitation and Exploration in first post. This concept is inherently linked to human nature where we as human prefer known compared to unknown. For an example going to Restaurant, you can choose to go to your favourite restaurant since you already like the food there but unless and until you try another restaurant you won’t know if there exist a better restaurant. Exploitation is thus going or doing the same action which gives best value from a state (it is often called Greedy action), while Exploration is to try out new action which may give a better return in long run even though immediate reward may not be encouraging. 

**Markov Decision Processes:** Markov Decision Process (MDP) is a mathematical representation of a complex decision-making process. (MDP) formally describe an environment for Reinforcement Learning. Environment is fully observable and stationary (meaning rules do not change with time). Almost all RL problems can be formalized using MDP.MDP is defined by:

    •	A state S, which represents every state that one could be in, within a defined world. Only the present matters; which means that the transition function only depends on the current state S and not any of the previous states.
    •	A model or transition function T; which is a function of the current state, the action taken and the state where we end up. This transition produces a certain probability of ending up in state S’, starting from the state S and taking the action A.
    •	Actions are things I can do in a particular state.
    •	A reward is a scaler value for being in a state. It tells us the usefulness of entering the state.
    
The final goal of the MDP is to find a policy that can tell us, for any state, which action to take (remember, mapping of states to actions is our policy). The optimal policy is the one that maximizes the long-term expected reward. Once optimal policy is found, RL problem is solved.

**Bellman Equation:** The value of a certain state is equal to the reward in the current state, plus the discount from all the rewards I get from that point on, transitioning from the current state to a future state.

The “discount” () mentioned above is a value between zero and one, and it allows us to treat an infinite sequence with finite value, otherwise the value in an infinite time horizon will always be the same, of an infinite magnitude (it is also mathematically more reasonable to use. Reward received in future is not as valuable as received immediately. Thus, discount factor is used to determine present value of future reward (similar to present value of future money discounted due to factors like inflation). The value of receiving reward R after k + 1 time-steps is γ<sup>k</sup>R.  

**Dynamic Programming:** Dynamic programming is a well-known technique to solve many problems by using past knowledge to solve future problem. It breaks down a complex problem into a collection of sub problem. Then solves this subproblem and store them to refer again to solve the main problem, it's a divide and conquer strategy. DP can be used to solve RL problem when a perfect model of environment as a MDP is available. Its limitation is, in real life most of the environment cannot be modeled as a perfect MDP and computation expense in DP is too high. But still DP plays an important role to understand how RL problem can be solved.
We will discuss two well-known DP algorithm for RL, Value Iteration and Policy Iteration. First, we consider how to compute the state-value function (V) for an arbitrary policy (Pi). This is called **policy evaluation** in the DP literature (also referred as the **prediction** problem). The process of making a new policy that improves on an original policy, by making it greedy with respect to the value function of the original policy, is called **policy improvement**.

**Generalized Policy Iteration:** Generalized policy iteration (GPI) refer to the general idea of letting policy evaluation and policy improvement processes interact, independent of the granularity and other details of the two processes. It’s like Messi and Ronaldo playing in the same team for a football match. They pass the football every time but compete with each other for personal goal score but they also assist each other to win the match for the team. Similarly, GPI is like a football (Soccer) game where ultimate aim is to find optimal policy and alternately policy evaluation and policy improvement happens.

**Value Iteration:** To solve the Bellman equation we normally start with arbitrary values for all states and then update them based on the neighbors (which are all the states that it can reach from the current state I am in). Finally, we repeat that until convergence. This process is called “value iteration”.
Value Iteration is a combination of one (or more than one) sweep of policy evaluation and then perform another sweep of policy improvement. Repeat the process still convergence happens.
Value iteration includes: **finding optimal value function** + one **policy extraction**. There is no repeat of the two because once the value function is optimal, then the policy out of it should also be optimal (i.e. converged). **Finding optimal value function** can also be seen as a combination of policy improvement (due to max) and truncated policy evaluation (the reassignment of V(s) after just one sweep of all states regardless of convergence).

**Policy Iteration:** This is a GPI process in which policy is improved by performing monotonically improving policies and value functions: by repeating policy evaluation and then performing a policy improvement. Each policy is guaranteed to be a strict improvement over the previous one (unless it is already optimal). Because a finite MDP has only a finite number of policies, this process must converge to an optimal policy and optimal value function in a finite number of iterations. This way of finding an optimal policy is called policy iteration.

Policy iteration includes: **policy evaluation** + **policy improvement**, and the two are repeated iteratively until policy converges
