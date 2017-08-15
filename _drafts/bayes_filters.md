---
layout: post
title: Bayes filters. A summary
use_math: true
excerpt: A quick summary about Bayes filters from the book "Probabilistic Robotics".
---


## Probabilistic Generative Laws

In probabilistic robotics, the dynamics of the robot and its environment are characterized by 2 probabilistic laws:
* the state transition distribution characterizes how state changes over time, possibly as an effects of robot controls: 

$$p(x_t | x_{0:t-1}, z_{1:t-1}, u_{1:t})$$

* the measurement distribution characterizes how measurements are governed by states: 

$$p(z_t | x_{0:t}, z_{1:t-1}, u_{1:t})$$

A state \`x_t\` will be called _complete_ if it is the best predictor of the future, i.e. knowledge of past states, measurements and contrals carry no additional that would help us predict the future more accurately.

When the state is complete, we have the following equalities:

$$p(x_t | x_{0:t-1}, z_{1:t-1}, u_{1:t}) = p(x_t | x_{t-1}, u_t)$$

$$p(z_t | x_{0:t}, z_{1:t-1}, u_{1:t}) = p(z_t | x_t)$$

## Belief Distributions

The belief of a robot is the posterior distribution over the state of the environment (including the robot state) given all past sensor measurements and all past controls:

$$bel(x_t) = p(x_t | z_{1:t}, u_{1:t})$$

Occasionally, it will prove useful to calculate a posterior _before_ incorparating \`z_t\`, just after executing the control \`u_t\`. Such a posterior will be denoted as follows:

$$\overline{bel}(x_t) = p(x_t | z_{1:t-1}, u_{1:t})$$

## Bayes Filters

The most general algorithm for calculating belief is given by the _Bayes filter_ algorithm, a recursive algorithm that calculates the belief \`bel(x_t)\` from the previous belief \`bel(x_{t-1})\` and the last measurement and control data:

__Algorithm Bayes_filter__(\`bel(x_{t-1}), u_t, z_t\`):
* for all \`x_t\` do
	* \`\overline{bel}(x_t) = \int p(x_t|x_{t-1}, u_t) bel(x_{t-1}) dx_{t-1}\`
	* \`bel(x_t) = \eta p(z_t|x_t) \overline{bel}(x_t)\`
* endfor
* return \`bel(x_t)\`

The first step in the loop is the control update or _prediction_. The second step is called the _measurement update_.

To compute the posterior belief recursively, the algorithm requires an initial belief \`bel(x_0)\` at time \`t = 0\` as a boundary condition.

The algorithm can only be used in this form for the most simple estimation problem. It also assume that the state is _complete_. However in practice, Bayes filters have been found to be surprisingly robust to such violations.

There are different ways to implement Bayes filters. Each such technique relies on different assumptions regarding the measurement and state transition probabilities and the initial belief. These assumptions then give rise to different types of posterior distributions, and the algorithms for computing them have different computational characteristics.

