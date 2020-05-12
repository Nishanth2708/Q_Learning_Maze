# Q_Learning_Maze
Maze solving using reinforcement learning
Abstract:
Machine learning is very important in several fields ranging from data mining to biological sciences. This project implements the Q -learning algorithm for abstract graph models with maze solving. Here, the maze matrix is converted into Q learning reward matrix taking the states and action into consideration. This implementation is on higher level abstraction, so other representation such as deep q learning, neural networks can also be used. In this project, the agent is fixed in the top left corner and the goal is defined based on the user inputs.
Introduction:

Everyone in their lives, have played a very common and obvious Maze game once in their lives. I’ve come up a similar interesting problem where the agent trains itself to reach the goal position in a discrete action space using the famous Q learning algorithm.
Reinforcement learning is one of the several machine learning techniques of artificial intelligence. The main system components that are involved in this project include states, action and reward system. Agent makes an action and it is rewarded and based on this reward it is possible to model any maze problem of similar configuration using reinforcement learning technique.

 
The system that is trained through this method will learn the optimal method of making decisions by performing interaction with its environment and receiving feedback.
The motivation is developed mainly from the definition of reinforcement learning. With the concept of reinforcement learning, there is no need of modelling the dynamic systems and this method can be implemented for path planning of mobile robots in a constrained environment. 
Approach:

I’ve created an own environment to train the maze in a different grid space of 4X4, 5X5 and 10x10. In this environment the maze is hindered with the obstacles namely walls and pits. The goal is defined based on a user defined position and the aim is to find the optimal path to the end of the mazegame.
 In this game, the states are defined as the position of the agent in the environment and the agent is assumed to traverse along the four directions which UP, down, left and right.  So, when the agent is in process of reaching a goal, it perhaps collides with the walls and pits. Whenever, the agent gets into obstacles we reward based on the performance of the action.
1.	Taking actions:
The action that agent takes in a Q learning is done in two possible ways. They are, Exploring and Exploiting.
Exploiting: With the Q table as reference, the agent tries to make a move in all possible actions.  The agent then selects the action in a way where it can maximize the reward.
Exploring: During this action, the agent explores all the states randomly by taking a random action. This makes the agent to discover the new states, where it isn’t possible during exploiting.
We choose a single set of action from exploiting and exploring by selecting the epsilon decay and tuning it based on the observed outcomes. In our case, the epsilon greedy is assumed as 0.9.
 
2.	Q Learning:
Based on the actions, we generate a new action and new state for every state. Firstly, we fix the q table to zeros. Then after each action a new state, corresponding reward for the action is also generated. Then, Q table gets update based on the Bellman’s equation  
Cell	Reward
Goal	+50
Pits	-10
Walls	-1
Free cells	0






This Q learning follows an off-policy temporal difference control algorithm. Since it is an off-policy algorithm, it does not follow the policy; instead, it directly approximates the optimal state-action value. It starts in a state-action pair (S, A) and ends up in a new state S’. Instead of using epsilon-greedy policy, it directly chooses the best possible state-action value for state S’ by just doing a max. Next, it updates the state-action value Q (S, A) by applying Bellman update. . Then, it calculate the TD error by subtracting old estimated value Q(S, A) from the TD target, which is Next, it applies the Bellman update to the old estimated Q (S, A) by multiplying TD error and the learning rate and add it to the old estimated Q (S, A). After applying the Bellman update, it updates the current state S to the next state S’ and the current action A to a new action chosen using epsilon-greedy policy on the state-action values for S’. And then, it goes into the next iteration and do the bellman update iteratively. Finally, the state-action value Q will converge to the optimal policy.
3.	Implementation of the Q learning algorithm:

The pseudo code for the Q learning algorithm is depicted below, the code is fully developed and available in python3.
1.	Initialize Q to zeros
2.	For each episode select a random state then select an action based on the state using the epsilon greedy approach.
3.	Travel to the next state and obtain the new state space and optimal action for the corresponding state.
4.	Check for the states if it is already in the Q table else append the new state
5.	Update the Q table based on the bellman’s equation by calculating the error between the Q predict and Q estimate.
6.	Make the initial state as the new state and loop for ‘N’ desired episodes
Choose the parameters for the algorithm appropriately so that, the agent tries to converge as fast as possible in the most optimal path.

![](Screenshot(89).png)
