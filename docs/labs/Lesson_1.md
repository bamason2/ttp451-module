---
layout: page
mathjax: true
---

# Lab 1: Optimisation

## Topics

- Aims and Objectives
- Overview and Exercise
- Background Information
- Exercise 1: Optimisation

## Learning Outcomes

By the end of this lesson, you will be able to:

- Evaluate and visualise a cost function.
- Use different solvers in MATLAB&copy; to solve optimisation problems.
- Solve real world optimisation problems relating to engines.

## Aims and Objectives

The aim of this exercise is to gain an understanding of basic optimisation approaches, this will be evaluated in the setting of mathematics and engine operation.

## Overview of Exercise

The optimisation problem can be considered as an abstraction of the problem of making the best possible choices from a set of candidate choices. This includes the representation of the choice made, the constraints (specifications or limits) and the objective function (representing the cost of making a specific choice). The solution of the optimisation problem corresponds to a choice that has the minimum cost among the choices that meet the requirements.

## Background Information

The MATLAB&copy; Optimisation Toolbox provides functions for finding parameters that minimize or maximize objectives while satisfying constraints. The toolbox includes solvers for linear programming, mixed-integer linear programming, quadratic programming, nonlinear optimisation and nonlinear least squares. You can use these solvers to find optimal solutions to continuous and discrete problems, perform trade-off analyses and incorporate optimisation methods into algorithms and applications. We will use the optimisation GUI as well as code.

---

### Exercise 1: Optimisation

In the exercise folder find the “Optimization lab” folder or download it from LEARN  and unzip it, it contains several important files for this exercise.

---

#### Task 1-1: Basics of Optimisation

The file "J1.m" implements the following “nicely shaped” cost function:

$$J_1(p)=p^2_1+e^{p_2}+e^{-p_2}+p_1p_2+p_2$$

in MATLAB&copy;.

- Evaluate $$J_1$$ for a number of points and try to get a feeling for it, you can use a simple call with two arguments such as J1(1,2).
- Visualise this function. The "ez" plot functions are convenient to do this, such as ``<ezsurf(J1)>`` or ``<ezcontour(@J1)>``. Which kind of plot is most suitable?
- Use ``<fminsearch>`` to find the minimum: ``<fminsearch(@J1vect,[0 0])>``, ``<fminsearch>`` expects a function with a single vector argument therefore the version defined in J1vect.m has to be used. Try different starting points.
- How many evaluations are required by ``<fminsearch>``?

---

#### Task 1-2: Optimtool GUI

The same exercise can be achieved using the graphical interface it presents more information about the optimisation process.

- Execute the command ``<optimtool>`` to start the graphical user interface “Optimization Tool”.
- Select the solver fminsearch.
- Enter the objective function ``<@J1vect>``.
- Enter the starting point [0 0].
- Click [Start]. How long does it take and how many iterations are required?
- Under Plot functions enable the options [Function count] and [Function value]. It shows how the function value decreases during the optimisation.
- Try the same with the solver ``<fminunc>``. You should select the algorithm [Medium scale] (large scale is not applicable without a derivative of the cost function). What is the main difference of this solver?
- The function ``<J1grad>`` provides both the cost function and the gradient use this together with ``<fminunc>`` by selecting Derivatives: Gradient supplied. How does this improve the optimisation?

$$\frac{\partial J_1}{\partial p_1} = 2p_1+p_2$$

$$\frac{\partial J)_1}{\partial p_2} = e^{p_2} + -e^{-p_2}+p_1+1$$

- Try a constraint minimisation using the solver ``<fmincon>``. You have to supply bounds for $$p$$ such as Lower: $$[-10 -10]$$ and Upper: $$[10 10]$$. What happens if you only allow positive values?

---

#### Task 1-3: Optimal Engine Calibration

The model_V8NA_V2 is a simple engine model of a naturally aspirated spark ignition V8 engine at a fixed engine speed. It takes a single vector argument with three values: the relative load (0 to 100), the spark advance angle (0 to 35), and the normalised air fuel ratio (0.8 to 1.1). The output is a vector of 6 measurements: BMEP (in bar), SD of BMEP (in bar), exhaust mass flow (in kg/h), exhaust temperature (in C), fuel consumption (in kg/h) and BSFC (in g/kWh).

- For a relative load of 50 and an air fuel ratio of 1 find the best BSFC. You can use unconstrained optimisation with ``<fminsearch>`` or constraint optimisation using ``<X = fmincon(FUN,X0,A,B)>`` for this. You will need to write your own cost function that calls the model function.
- When an electronic throttle control is used the throttle setting does not correspond completely to the torque request. A better formulation of this problem is to find the best BSFC for a given BMEP say 6 bar. You can either use a separate function to solve the model for a given BMEP using ``<fsolve>`` or you can use another variation of constrained optimisation: ``<X = fmincon(FUN,X0,A,B,Aeq,Beq,LB,UB,NONLCON)>`` where ``<NONLCON>`` is a function returning the BMEP deviation as an equality constraint.
- Repeat this optimisation for a number of steps from 1 bar to 10 bar BMEP. This will result in an optimal calibration but is it realistic? Which requirements have been ignored? How could you include them?

---

#### Task 1-4: Multicriteria Optimisation (optional)

Consider the following variation of the multicriteria cost function used in Section 6. It distinguishes between two stretches driven with different speeds $$p_1$$ and $$p_2$$;

$$J_4(p) = \alpha \frac{50}{p_1} + \alpha \frac{50}{p_2} + 5\frac{p_1}{60}^2 + 4\frac{p_2}{60}^2$$

- Plot the function above. Is it convex?
- Find the optimum for a set of hourly costs. You have to edit the function J4.m to change $$\alpha$$. (If you are more advanced in MATLAB&copy; programming you can also automate this process.)
- How can the results be visualized? Create a diagram with the key relationships.

---
