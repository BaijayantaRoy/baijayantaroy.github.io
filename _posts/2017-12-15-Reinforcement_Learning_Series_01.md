---
layout: post
title: Reinforcement Learning Series - 01
published: true
comments: true

---

_**Reinforcement Learning (RL) is one of the most happening field of Machine Learning (ML) and Artificial Intelligence (AI).Though RL existed for many decades, only recently the giant has awaken after explosion in Neural Network based Deep Learning. This blog is an attempt to explain basic concepts of Reinforcement Learning using simple example and explanation that anyone with elementary English knowledge would be able to understand. I am not a native English speaker, thus if you find any error or sentences not conveying right meaning, please drop me a mail and I will try to correct or rewrite .I am a self-learner of RL and ML assisted by numerous books, videos and blogs/writings and i am indebted to those scholars and writers. I have borrowed many ideas from them for this writing. Wish you a happy learning. **_


### Reinforcement Learning
Reinforcement learning is learning by interacting with an environment. An RL agent learns from the consequences of its actions, rather than from being explicitly taught and it selects its actions on basis of its past experiences (exploitation) and also by new choices (exploration), which are essentially, trial and error learning just like a child learns. The reinforcement signal that the RL-agent receives is a numerical reward, which encodes the success of an action's outcome, and the agent seeks to learn to select actions that maximize the accumulated reward over time. 

For learning anything new, understanding basic terminology is very important. To understand RL, reader has to get familiar with below terminology, their meaning and above all how these terms are linked to each other, but before that let’s see one example to understand what Reinforcement Learning means.

In this example we have a multistory building with rooms as shown in below diagram. Here Robot is the RL Agent for this RL problem. Each room is depicted by a square that can be considered as a State for the problem (all States are marked as S01, S02 etc. for easy reference, later we will have notation for each terminology). Agent can perform 3 action (move up , left and right). As Agent move along, it collects rewards gem(s) at each state. Agent can move only once from a room or state and cannot come back. The goal for the Agent for this problem is to obtain maximum number of Gem and reach the top level room marked as S13 and exit from there. Agent needs to start from S01 state and then it can move to different rooms. As you can see, it’s the long term cumulative rewards that matters and not the early rewards. Some states are like dead end, even though those have higher rewards (S03,S09) as those don’t have any further ways to move towards exit state. In this problem Agent interacts with the environment, take action and collect reward but Agent is not explicitly told what patch of movement it should take or what the maximum possible reward in a long run is. RL algorithm assist Robot to find optimal way of taking action in each step and maximize its long term goal within the conditions set in the environment.

![RL Example](/images/RL_example.png "Reinforcement Learning Example")

Now let's understand each terminology and then we will get back to this problem.

**Agent:** Anything that sense its environment using some kind of sensor and able to generate action in the environment is called Agent. Agent executes action, receive observation and reward. Example, a robot vacuum cleaner, a software program that plays Chess or Go, self-driving car etc. In our example RL problem, Robot is the agent.

**Environment:** Environment is the overall representation with which Agent interacts. Agent is not considered part of the environment. Environment receives action, emits observation and reward. In above diagram everything other than Agent is part of environment.

**State:** State describes the current situation and state determines what happens next. For example for a Robot that is learning to walk, the state is the position of its two legs. For a Chess program, the state is the positions of all the pieces on the board. In our example every room is a state that Robot needs to move. In above example States are marked by S01 to S13.

**Reward:** When an agent takes an action in a state, it receives a reward. Here the term “reward” is an abstract concept that describes feedback from the environment. A reward can be positive or negative. When the reward is positive, it is corresponding to our normal meaning of reward. When the reward is negative, it is corresponding to what we usually call “punishment.”. Reward is the feedback the agent gets from the environment at every time step. It can then use this reward signal (can be positive for a good action or negative for a bad action) to draw conclusions about how to behave in a state. The goal, in general, is to solve a given task with the maximum reward possible. That is why many algorithms have a very small negative reward for each action the agent takes to animate him to solve the task as fast as possible. Reward is a design decision that is critical in RL as this would encourage the RL agent to optimize the behavior. For example winning the chess game at less time or drive the car at average speed but without any collision (car can speed up in empty high-way while drive slowly in crowded road). Reward tells what is good in an immediate sense. For example in Atari game every time step agent gets points or loose points. In our example all green Gem(s) are reward at each State.

**Value:** Value of is the total amount of reward an agent can expect to accumulate over the period starting from that state. Unlike Reward signal, value function specifies what is good in the _long run_. Since Value is total amount of return from a state, for state S12, value would be 6 gems. We will discuss Value (State Value and Action Value) in subsequent blog.

**Action:** Action is what an agent can do in each state. In above example Robot it can take action like move up or left or right. Given the state, or positions of its two legs, a robot can take steps within a certain distance. There are typically finite (or a fixed range of) actions an agent can take. For example, a robot stride can only be, say, 0.01 meter to 1 meter. The Go program can only put down its piece in one of 19 x 19 (that is 361) positions. 

![Action that Robot can take](/images/Action.png "Action that Robot can take")

**Policy:** Policy is the agent’s action selection from a state. It’s a mapping of action in a state with probability for each possible action. In many RL solution goals would be to find optimal policy, meaning find the best action in that state that will maximize the long term reward. It dictates what action to take given a particular state. A policy is a function which can be either deterministic or stochastic. Refer to below sample policy diagram in which each state has the mapping of action.

![Policy](/images/policy.png "policy")


**Model of the Environment:** Model is mimics of environment. It has the knowledge of transition from state to state and a high level understanding of the Environment.

Now let's get back to the problem. There are many possible ways Robot can move and reach exit. In RL, one complete cycle from start to end is called an Episode for finite problem like this. It can take many paths to reach as shown in diagram by arrow path. In this problem the Robot cannot return to previous state thus states like S03 are dead-end without any possible solution and Robot will be stuck there forever.

![Possible Episodes](/images/PossibleEpisodes.png "Possible Episodes")

Once we calculate total accumulated rewards then the path followed right is the best path as it accumulates the most number of gems even though it would take longer time to reach exit. Agent could have taken the left diagram path but it would means less total reward.

![Problem Solution](/images/Optimal_move.png "Problem Solution")

In many RL problem Agent is given small negative reward in each state and a positive reward at terminal or exit state (like Go or Chess game playing Agent only get reward at the end of the game when it has won or lost). RL Agent interacts with Environment and learns slowly over the period by trial and error. Value function and Policy plays a major role in all RL algorithm and we will explore those in subsequent blogs. There are many variations of RL algorithm like Policy based, Value based, Policy-Value combined (Actor Critic Method), Model Free, Model Based, Function Approximation Methods etc. Real life problems has millions of state, thus function approximation is used extensively to solve real life problem. All real life problems requires application of many diverse knowledge areas of AI/ML technique to achieve the intended goal (like Alpha Go Zero uses Convolutional Neural Network (CNN), Monte Carlo Tree Search and RL methods to achieve the superhuman skill in the Go game).
