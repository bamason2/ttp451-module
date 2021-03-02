# Lesson 1: Optimisation

## Topics

- Aims and Objectives
- Overview and Exercise
- Background Information
- Exercise 1: Optimisation

## Learning Outcomes

By the end of this lesson, you will be able to:

- Evaluate and visualise a cost function.
- Use different solvers in Matlab to solve optimisation problems.
- Solve real world optimisation problems relating to engines.

## Aims and Objectives

  The aim of this exercise is to gain an understanding of basic optimisation types.  This will be evaluated in the settings of mathematics and engine operation.

## Overview of Exercise

The optimisation problem can be considered as an abstraction of a problem of making the best possible choice from a set of candidate choices. This includes the representation of the choice made, the constraints (specifications or limits) and the objective value (representing the cost of making a specific choice). The solution of the optimisation problem corresponds to a choice that has the minimum cost, among the choices that meet the requirements.

## Background Information

The Matlab Optimization Toolbox provides functions for finding parameters that minimize or maximize objectives while satisfying constraints. The toolbox includes solvers for linear programming, mixed-integer linear programming, quadratic programming, nonlinear optimization, and nonlinear least squares. You can use these solvers to find optimal solutions to continuous and discrete problems, perform trade-off analyses, and incorporate optimization methods into algorithms and applications. We will use the optimisation GUI as well as code.

### Exercise 1: Optimisation

In exercise folder, find “1. Optimization lab” folder or download from the LEARN server and unzip it, it contains several important files for this exercise.

#### Exercise 1-1: Basics of Optimisation

The file J1.m implements the following “nicely shaped” cost function:

$$ J_1(p)=p_1^2+e^{p_2}+e^{-p_2}+p_1p_2+p_2 $$
