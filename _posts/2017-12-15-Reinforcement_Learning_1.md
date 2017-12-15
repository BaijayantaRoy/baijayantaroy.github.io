---
layout: post
title: Reinforcement Learning Series - 01
published: true
---

_Reinforcement Learning ( will be referred as RL as well here) is one of the most exciting field of Artificial Intelligence (AI) which has shown huge progress in last few years. Though RL existed for many decades, after explosion of Neural network based deep learning, this field too exploded with innovation and  excitement. There are numerous books, videos and articles/papers which are written by experts in the field (refer to reference section).This blog is an attempt to explain basic concepts of Reinforcement Learning using simple example and explanation that anyone with a basic english knowledge. I am not a native english speaker and a self learner of Machine Learning/RL with aid from all the books, videos and blogs/writings from where I borrowed most of the content. If you find any error or sentences not conveying right meaning, please drop me a mail and I will try to correct or rewrite the section._


### Reinforcement Learning
Reinforcement learning is learning by interacting with an environment. An RL agent learns from the consequences of its actions, rather than from being explicitly taught and it selects its actions on basis of its past experiences (exploitation) and also by new choices (exploration), which is essentially trial and error learning just like a child learn. The reinforcement signal that the RL-agent receives is a numerical reward, which encodes the success of an action's outcome, and the agent seeks to learn to select actions that maximize the accumulated reward over time. 

For Learning anything new, understanding basic terminology is very important. To understand RL, reader has to get familiar with below terminology, their meaning and above all how these terms are linked to each other, but before that lets see one example to understand what Reinforcement Learning means.

We have an multistory building with rooms as show in below diagram. Here Robotis the RL Agentfor this RL problem. Each room is depicted by a square that can be considered as a state for the problem (all are marked as S01, S02 etc for easy refence,later we will have notation for each terminology). Agent can perform 3 action (move up , left and right). As Agent move along, it collects rewards as gem(s) at each state. Agent can move only once from a room or state and can not come back. The goal for the Agent for this problem will is to obtain maximum number of Gem and reach the top level room marked as S13. Agent need to start from S01 state and then it can move to different rooms. As you can see, it’s the long term cumulative rewards that matters and not the early rewards. Some states are like dead end, even throuh those have higher rewards (S03,S09) as those don’t have any further ways to move towards exit state. This is an iteresting problem.

![RL Example 01.png]({{site.baseurl}}/_posts/RL Example 01.png)

                              Figure - 01 ( Reinforcement Learning Example)

Now let's understand each terminology and then we will get back to this problem.

**Agent:** Anything that sense its environment using some kind of sensor and able to generate action in the enviroment is called Agent. Agent execute action, receive observation and reward. Example, a robot vacum cleaner,  a software program that plays chess or Go, self driving car etc. In Figure-01, Robot is the agent.

**Environment:** Environment is the overall representation with which Agent interacts. Agent is not considered part of the environment. Environment receives action , emits observation and reward.In figure-01 everything other than Agent is part of environment.

**State:** State describe the current situation and state determine what happens next . For example in  For a robot that is learning to walk, the state is the position of its two legs. For a Chess program, the state is the positions of all the pieces on the board. In our example every room is a state that Robot need to move. In above Figure-01, all rooms are state as marked by S01 to S13.

**Reward:** When an agent takes an action in a state, it receives a reward. Here the term “reward” is an abstract concept that describes feedback from the environment. A reward can be positive or negative. When the reward is positive, it is corresponding to our normal meaning of reward. When the reward is negative, it is corresponding to what we usually call “punishment.”. Reward is the feedback the agent gets from the environment at every time step. It can then use this reward signal (can be positive for a good action or negative for a bad action) to draw conclusions about how to behave in a state. The goal, in general, is to solve a given task with the maximum reward possible. That is why many algorithms have a very small negative reward for each action the agent takes to animate him to solve the task as fast as possible. Reward is a design decision that is critical in RL as this would encourage the RL agent to optimise the behaviour . For example winning the chess game at less time or drive the car at average speed but without any collision (car can speed up in empty high-way while drive slowly in crowded road). Reward tells what is good in an immediate sense. For example in Atari game every time step agent gets points or loose points. In Figure-01 all green gems are reward at each State.

**Value:** Value of is the total amout of reward an agent can expect to accumulate over the period starting from that state. Unlike Reward signal, value function specifis what is good in the _long run_. Since Value is total amount of return from a state, for state s12, value would be 6 gems.

**Action:** Action is what an  agent can do in each state. In above example Robot it can take action like move up or left or right. Given the state, or positions of its two legs, a robot can take steps within a certain distance. There are typically finite (or a fixed range of) actions an agent can take. For example, a robot stride can only be, say, 0.01 meter to 1 meter. The Go program can only put down its piece in one of 19 x 19 (that is 361) positions. In the above example problem , Robot can take 3 action like moving up or right or left. 
![Action.png]({{site.baseurl}}/_posts/Action.png)

                                Figure-02 (Action)

**Policy:** Policy is the agent’s action selection from a state. It’s a mapping of action in a state with probability for each possible action. In many RL solution goal would be to find optimal policy meaning find the best action in that state that will maximize the long term reward. It dictates what action to take given a particular state. A policy is a function can be either deterministic or stochastic.below could be policy diagram for each state which is the mapping of action in each state.

![RL Example Policy.png]({{site.baseurl}}/_posts/RL Example Policy.png)

                                Figure-03 (Policy)

**Model of the Environment:**  Model is mimics of environment.

Now let's get back to the problem.There are many possible ways Robot can move and reach exit. In RL, one complete cycle from start to end is called for Episode for finite problem like this. It can take many path to reach. In this problem the Robot can not return to previous state thus states like S03 are dead end without any possible solution and Robot will be stuck there for ever.

![PossibleEpisodes.png]({{site.baseurl}}/_posts/PossibleEpisodes.png)

Once we calculate total accumulated rewards then the path followed right is the best path as it accumulates the most number of gems even though it would take longer time to reach exit. 

![ProblemSolution.png]({{site.baseurl}}/_posts/ProblemSolution.png)

