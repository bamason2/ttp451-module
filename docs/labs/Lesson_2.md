---
layout: page
mathjax: true
parent: Computer Labs
---

# Lab 2: Design of Experiments
{: .no_toc }

<details close markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Topics
{: .no_toc }

- Aims and Objectives
- Background Information
- Exercise 2-1: Cam Timing Design (Two Inputs)
- Exercise 2-2: JLR Example (Eight Inputs)

## Learning Outcomes
{: .no_toc }

By the end of this lesson, you will be able to:

- Generate Full Factorial, Space Filling and V-Optimal experimental designs
- Test design proposals and augment them for application
- Analyse the effects of design variations on model predictions

## Aims and Objectives

The aim of this exercise is to develop an understanding of the experimental design aspects of the calibration task, this will include the creation of several DoE proposals. Introductions will be given to constraints and evaluating model fits for particular designs.

The calibration task focuses on mapping the engine fuel consumption across a range of intake and exhaust cam settings. In order to do this effectively an experimental design is required to minimise the amount of testing required whilst covering as much of the operating space to accurately map fuel consumption. One possible approach before physical testing is to determine the DOE using a target function. We will generate several DOE proposals for this case study. The relationship between fuel consumption and intake/exhaust cam timing for a particular engine can be expressed as:

$$ f_{bsfc}(x_{EVC}, y_{IVC}) = (((x_{EVC}-32)/4)^2 + ((y_{IVC}-58)/3.8)^2)+2*y_{IVC}+112$$

Input variable limits;

$$0<=x_{EVC}<=60$$

$$0<=y_{IVC}<=60$$

Design of experiments process flowchart;

![image](figs/lab2/fig_1_DOE_flowchart.png)

## Background Information

### Introduction to DOE

The MBC toolbox design browser can be used to design experiments (DOE) for collecting data (i.e engine performance responses like emission, torque output and fuel consumption). The design browser is a powerful tool which can be used to create complex experimental designs. Experimental design is important because it creates test sequences comprising of input variable values in the most efficient manner.

The progress flow chart for designing an experiment and testing is shown in the figure below. Three different designs  will be used for comparison purposes. The designs will be compared by testing each one in a “DOE testing kit” script. The outcome can be observed and changes/observations recorded.

![image](figs/lab2/fig_2_MBC_DOE_process.png)

The figure below shows the process of generating DOE using model browser:

![image](figs/lab2/fig_3_generation_of_experimental_designs.png)

### Introduction to Cam Timing Design Exercise

An engine is fitted with Variable Cam Timing (VCT) for both exhaust and intake cams. Each of the cams changes with engine speed and load. For a particular engine speed and load, the changes of cam timing will affect the engine fuel consumption. The figure below shows a valve lift diagram for intake and exhaust. Advancing or retarding a cam will affect intake reversion, scavenging or exhaust backpressure. These changes are influenced by the amount of overlap and the degree where the intake/exhaust valve closes which in turn affects the fuel consumption.

![image](figs/lab2/fig_4_Intake_exhaust_vallve_lift_diagram.png)

Recall that a calibration task was given to map the engine fuel consumption across a range of intake and exhaust cam settings. An experimental design is required to do this in the most efficient method, which is, running with the least experimental points and covering as much area in the operating range while be able to accurately map the fuel consumption. It was decided that before going into actual testing, the DOE design needs to be determined first using a target function. We will generate several DOE designs for this case study.

The relationship between fuel consumption and intake/exhaust cam timing for a particular engine can be expressed as:

Target function:

$$ f_{bsfc}(x_{EVC}, y_{IVC}) = (((x_{EVC}-32)/4)^2 + ((y_{IVC}-58)/3.8)^2)+2*y_{IVC}+112 $$

Input variable limits;

$$0<=x_{EVC}<=60, 0<=y_{IVC}<=60$$

To determine how well the DOE able to give best response surface predictions, we will compare it against the same target function but mapped in high resolution. 

![image](figs/lab2/fig_5_graphical_representation_of_map.png)

---

### Exercise 2-1: Cam Timing Design

There are four distinct tasks in this exercise, which are listed below:

- Generate several DoE proposals
- DoE Testing and evaluation
- Constrained Designs
- Optional Exercise

Before you begin dowload the files required for this exercise from LEARN or [here](https://lunet-my.sharepoint.com/:u:/g/personal/ttbm2_lunet_lboro_ac_uk/EdY_zo2jZgZFnWikxFrXx9wBpgXgi9jIybiiGc8buIoOdw?e=UjmUY9)

---

#### Task 2-1.1: Generate several DoE proposals

- Start MBC Toolbox Interface

Double-click the MATLAB&copy; icon to start MATLAB&copy;. Once initialisation is complete, enter ``<mbcmodel>`` at the command prompt to start the MBC Toolbox. The Model Browser window appears.

![image](figs/lab2/fig_6_model_browser_gui.png)

Choose [File >> New Test Plan] in the menu. A test plan frame appears. Select [One-Stage Model]. Click [OK].

![image](figs/lab2/fig_7_new_test_plan.png)

- Specify the input factor names and ranges

Double-click the Local Model Inputs block in the diagram. Increase the number of factors to two. Change the symbols of the two input factors to IVC and EVC and enter the input factors range as shown in figure below.

![image](figs/lab2/fig_8_one_stage_plan.png)

![image](figs/lab2/fig_9_input_factor_setup.png)

- Creating classical design (full factorial option)

Right-click the local model in the diagram and choose set up model. Ensure the model class is set to linear model and then click ok (The type of model doesn’t matter at this stage). Next, right-click the local model in the diagram and choose design experiment.

![image](figs/lab2/fig_10_design_editor_setup.png)

![image](figs/lab2/fig_11_design_editor_window.png)

Choose [File >> New Design] or click New Design button in the toolbar. A new node called Linear Model Design appears. Click the new node, a 2D projection appears on the right. Rename the new node Linear Model Design to Classical_F by clicking the name and press F2 or right click mouse then select Rename Design from the menu.

![image](figs/lab2/fig_13_full_factorial_design.png)

Choose a classical design by clicking the [Classical Design] button in the toolbar, or choose [Design >> Classical >> Design Browser] then select [Full Factorial] from the [Design type] drop-down menu.

![image](figs/lab2/fig_14_design_editor.png)

Increase the number of levels for each factor from 2 to 6, keep the number of center points as 0. The total size of design is 36, you may view your design in different projections using the tabs (1-D, 2-D) under the display.

1-D: you may select a different factor to view each level of this factor. The frequency indicates the number of each level that appears among the all design test points (36). From the view of this design, we may see in full factorial design, the test points are evenly distributed among the factor space.

![image](figs/lab2/fig_15_design_projections_1.png)

![image](figs/lab2/fig_15_design_projections_2.png)

Click [OK] to close the Classical Design Browser and return to the Design Editor window. The Design Editor will show the Design Table which includes all the factor inputs combination as result of the design.

![image](figs/lab2/fig_16_design_table_1.png)

![image](figs/lab2/fig_16_design_table_2.png)

You may copy the data to other programs such as Excel by selecting [Edit >> Copy Design Data] from the menu or right click the mouse on any part of the Design Table and select Copy. For the case study, we need to export the design into a *.csv file. Save the design as “Classical_F.csv”.

![image](figs/lab2/fig_17_doe_export_1.png)

![image](figs/lab2/fig_17_doe_export_2.png)

- Creating Space Filling Design (Latin Hypercube option)

Create another design called Spacefilling_LH by clicking [File >> New design]. Select this design node, then open the Space Filling Design Browser by clicking [Design >> Space Filling >> Design Browser] from the menu or click the [Space Filling Design] button in the toolbar.
A dialog box asking about DOE points modification may appear, select [Replace the current points with new design].

![image](figs/lab2/fig_18_space_filling_design_browser_1.png)

![image](figs/lab2/fig_18_space_filling_design_browser_2.png)

![image](figs/lab2/fig_18_space_filling_design_browser_3.png)

In the Space Filling Design Browser window, select Latin Hypercube Sampling design type, and try different selection criteria to see its effect on the design points from the projection view. Set number of points to 36. Click [OK] when done.

![image](figs/lab2/fig_19_lh_hypercube_sampling_design.png)

Now, export the design into a *.csv file. Save the design as “Spacefilling_LH.csv”.

![image](figs/lab2/fig_20_export_doe_design.png)

- Creating Optimal Design

Create another new design called Optim_V. Select this new child node, then open the Optimal Design Browser by choosing Design>>Optimal from the menu or click the Optimal Design button in the toolbar.

![image](figs/lab2/fig_21_optimal_design_window_1.png)

![image](figs/lab2/fig_21_optimal_design_window_2.png)

In the Optimal Design setting window, set the optimal design parameters to the ones shown in the figures below. All are kept default except the Optimality criteria “V-Optimal” and total number of points “36”. Click the [OK] button to start optimizing the design. The optimization process would stop when the number of iterations without improvement reaches the pre-set value (here is 36) or number of iterations performed reach the pre-set value in Algorithm tab.

![image](figs/lab2/fig_22_optimal_design_window_1.png)

![image](figs/lab2/fig_22_optimal_design_window_2.png)

![image](figs/lab2/fig_22_optimal_design_window_3.png)

![image](figs/lab2/fig_22_optimal_design_window_4.png)

When the optimisation process ends, you may see the design table and projection view in the Design Editor window.

![image](figs/lab2/fig_23_projection_view_of_design.png)

Now, export the design into a *.csv file. Save the design as “Optim_V.csv”.

---

#### Task 2-1.2: DOE Testing and Evaluation

- Load DOE test kit

Change the MATLAB&copy; current folder to the current folder. In that folder, run the DOE_testkit_V11_R7.p in MATLAB&copy;, Right click and run the script. 

![image](figs/lab2/fig_24_tas_2015_folder.png)

It is easier to run the script with undocked command window.

![image](figs/lab2/fig_25_undock_command_window_1.png)

![image](figs/lab2/fig_25_undock_command_window_2.png)

- DOE testing kit overview

This testing kit helps to visualize the effects of a 2D DOE design to a response model. The model estimation capabilities depend partially on the quality of the DOE. Less DOE points are going to cause the model to miss some important characteristics of the system.

The testing kit is a universal program which can accept any type of DOE and equations as target functions. It can create custom DOE within the program itself, as well as add or remove existing DOE design loaded from a csv file. Finally, the user will be able to save the design together with the predicted output. The testing kit is still under development but is able achieve this workshop’s requirements. The figure below shows the interface of the testing kit.

![image](figs/lab2/fig_26_overview_of_doe_testing_script.png)

- Load DOE

Select option “2” in the program and press enter to load DOE. Select “DOE_poor_design.csv” which is located in the current folder and press enter. The program status will indicate a DOE has been loaded. A figure will appear which contains the subplot for the DOE points distribution along with its histogram.

![image](figs/lab2/fig_27_selection_option_1.png)

![image](figs/lab2/fig_27_selection_option_2.png)

![image](figs/lab2/fig_27_doe_scatter_subplot.png)

- Define target system response

Select option “5” to enter the BSFC response function from the problem statement. Enter the following function:

![image](figs/lab2/fig_28_bsfc_response_function_1.png)

![image](figs/lab2/fig_28_bsfc_response_function_2.png)

The function will be plotted on the DOE design.  The stem plot of subplot 2 shows the position of the DOE on the target surface response. Observe the position of the DOE points, the DOE only covers the outer part of the target response. It misses the center region of the response which may lead to poor modeling results. The key of designing a good experiment is the distribution of DOEs at critical locations on the target response. Since we already knew how the characteristic of the surface response is going to be, we predicted that the center region of the surface is going to under fit. Normally, for unknown systems, randomly positioned DOE points are important to scatter points in the operating boundary.

![image](figs/lab2/fig_29_bsfc_response_surface_function.png)

- Test the DOE points using the BSFC function

Select option “9” to enter test the DOE design. The DOE design sequences are used as input variables to the target function. The input variable are IVC and EVC.

It is expected that the model is going to fit poorly in the center region. Observed the boundary of the DOE design, the model managed to predict is pretty well. The plots shown below are the overlay of the expected response and response fit using the DOE design. The plot on the right is the contour plot of the differences between both surfaces. The differences are calculated by meshing both surface in high resolution and calculate the target BSFC output. The RMSE of both surfaces are relatively high, indicating high modeling error. 

![image](figs/lab2/fig_30_bsfc_response_result.png)

- Improving the modelling results
  
The error can be reduced by introducing more DOE points across the operating region. This extra points provides extra information of the curvature of the response model. By adding support points in the middle of the current DOE design, it will improve the model prediction.

![image](figs/lab2/fig_31_support_doe_points.png)

To add new DOE points go to option “7”. And enter the X and Y coordinates of the new support DOE points. Enter the following coordinates, the model will be automatically updated as new points are entered. Once done, type “exit” to go back to the main menu.

![image](figs/lab2/fig_32_x_and_y_coordinates.png)

Now, the model has improved with lesser modelling error. Take note of the center region of the response surface. The response model built using the DOE with support points has significantly improved with very low RMSE.

![image](figs/lab2/fig_33_improved_modelling_results.png)

- Save the design and results

The current DOE design along with the results and screenshot of the figure can be saved by entering option “10”. The files will be saved in the current MATLAB&copy; folder.

- Repeat the step 3 to 7 for the other saved DOE designs

Repeat step 3 to 7 as above for each of the saved DOE designs listed below (generated earlier using MBC model browser in Task 1). For each of the designs, try removing some DOE points and observe the changes to the histogram. Then, observe the effect of removing the DOE points to the response surface and RMSE.

---

#### Task 2-1.3: Constrained Designs

The previous design was found to exceed some important engine performance limits. The design required constraints to be implemented in order to control the input variables from causing damage to the engine or exceeding crucial engine limits.  Apply constraints for the following DOE designs:

- Full factorial design (6 levels for each variables)
- Space filling design (Latin Hypercube Sampling)
- V-optimal design
  
Follow the steps shown below on how to constrain a design. You will need to recreate a new tree along with the DOE design because a constraint can only be applied to the most recent design. Create new design tree for each design. For this task, regenerate all designs, starting with optimal design.

![image](figs/lab2/fig_34_doe_design_tree.png)

Designs can have any number of geometric constraints placed upon them. Each constraint can be one of four types: an ellipsoid, a hyper-plane (or linear), a 1-D lookup table, or a 2-D lookup table. Click [File >> New Design]. Rename the new node Optim_V_C. Choose [Edit >> Constraints] from the Design Editor menus. The Constraints Manager dialog appears. Click [Add].

![image](figs/lab2/fig_35_constraint_manager.png)

The Constraint Editor dialog with available constraints appears. The default 1D Table is selected in the Constraint Type drop-down menu. Select X factor IVC and Y factor EVC. Move the large dots (click and drag them) to define a boundary. The boundaries are as showed below.

![image](figs/lab2/fig_36_upper_boundary.png)

![image](figs/lab2/fig_37_lower_boundary.png)

Click OK. Your new constraint appears in the Constraint Manager list box.

- Generate optimal design within constraint boundary

Select this new child node, then open the Optimal Design Browser by choosing [Design >> Optimal] from the menu or click the Optimal Design button in the toolbar.

![image](figs/lab2/fig_39_optimal_design_window_1.png)

![image](figs/lab2/fig_39_optimal_design_window_2.png)

In the Optimal Design setting window, set the optimal design parameters as before. All are kept default except the Optimality criteria “V-Optimal” and total number of points “36”. Click the [OK] button to start optimizing the design. The optimizing process would stop when the number of iterations without improvement reaches the pre-set value (here its 36) or the number of iterations performed reaches the pre-set value in Algorithm tab.

![image](figs/lab2/fig_40_projection_of_constrained_optimal_design.png)

When finished save this design in the MATLAB&copy; current folder.

- Generate constrained designs for all other DOE types.
  
Repeat creating constraints for the other DOE designs. The constrained DOE designs should look like figures shown below:

![image](figs/lab2/fig_41_projection_of_lhs_design.png)

![image](figs/lab2/fig_42_projection_of_fullfactorial_design.png)

Load and retest each DOE designs in the script. Save the results after fitting the model.

![image](figs/lab2/fig_43_modelling_results_constrained_optimal_design.png)

---

#### Task 2-1.4: Optional

- Try generating your own DOE design using option “3” in the DOE testing script.
- Also try
  - Space filling design (Stratified Latin Hypercube Sampling)
    ![image](figs/lab2/fig_44_stratified_lhs_design.png)
  - Space filling design (SOBOL Sequence)

### Exercise 2-2: Cam Timing Design

This part of the exercise consists of an experiment design followed by virtual engine testing that forms the first part of modelling a V8 spark ignition engine. You will use a single stage model and create a space filling design. You will then use the Design of Experiments (DOE) points generated and test it using a virtual engine Simulink&copy; model. The Simulink&copy; model will provide you with the experimental test results (datasets) which will be used for creating V8 engine model during calibration optimization lab. The results generated from this lab task will be used for the modelling lab. Please save the generated result in the active folder (or your current MATLAB&copy; folder).

The following figure shows the flowchart for the second lesson in the Design of Experiments Workshop

![image](figs/lab2/fig_45_design_of_experiments_flowchart.png)

---

#### Task 2-2.1

- Start model browser by typing ``<mbcmodel>`` in command window. Create one stage test plan by right click on the [Untitled] project node and click [New Test Plan]. Select [One stage plan]. Click [OK] to make selection.

![image](figs/lab2/fig_46_one_stage_plan.png)

- Double click the “Input” diagram, set “Number of factors” to 8 and enter the following data as shown below for “min”, “max” and “signal” columns in the setup window.

![image](figs/lab2/fig_47_input_factor_set_up.png)

---

#### Task 2-2.2

- Right click on model icon in “Test Plan” pane, and select “Design Experiment”. The “Design Editor” window will appear. This where the DoE points can be created and constraints can be applied for known systems.

![image](figs/lab2/fig_48_test_plan_pane.png)

- Create new test design by clicking on the toolbar [File >> New Design]. An empty design will be created in the “Design Tree” pane. The design table will list down all the created test points. If the 3D projection doesn’t appear, click on the toolbar, [View >> Split View >> 3D Design Projection]. The 3D design projection view will be shown.

![image](figs/lab2/fig_49_design_editor_design_tree.png)

- Now create a Sobol design by clicking [Design >> Space Filling >> Sobol Sequence]

![image](figs/lab2/fig_50_space_filling_sobol_sequence.png)

- Set the number of design sequences to 350 and click [OK] to start generating Sobol sequences.

![image](figs/lab2/fig_51_design_sequence.png)

- Once the DoE points have been generated, the “Design Editor” will load the DoE points in the “Design Table” and “3D Design projection”. If the 3D projection doesn’t appear, click on the toolbar, [View >> Split View >> 3D Design Projection]. The 3D design projection will show the points that have been created. Now, export the design, so that it can be used for engine testing at the test bench. To export the design, click the toolbar [File >> Export Design]. Save as *.CSV format and name it to “V8NA_TestBed_DoE.csv”. The csv file might be located in Matlab root folder by default, change the save file location for easier file retrieval. Now, close the design editor.
  
![image](figs/lab2/fig_52_design_view_1.png)

![image](figs/lab2/fig_52_design_view_2.png)

For this exercise, the DoE test points were designed for an unknown system (No knowledge of the engine limits). For that reason, no constraints will be used for this exercise. Applying practice knowledge, constraints may come from engine modelling or early tests of an engine prototype.

---

#### Task 2-2.3

- Make sure you have downloaded the “TAS 2015” folder from learn. The files in “TAS 2015>>2. DOE lab ” folder are required to run the virtual engine test. The files required are shown in figure below. Set the Matlab directory path to the “TAS 2015” folder or whichever folder you have saved the contents of TAS 2015 folder. Copy the “V8NA_TestBed_DoE.csv” into the current Matlab folder so that the script will be able to find the design file.

![image](figs/lab2/fig_53_data_selection.png)

- The virtual engine test requires initialization. The initialization will automatically load the saved DOE points (“V8NA_TestBed_DoE.csv”) into the workspace and apply a time stamp to the design for it to be used in the virtual engine test &copy; block. Open “V8NA_TestBedData_400_Mdl_init.m” within the Matlab environment and execute the script. Once the execution has completed, a new variable is loaded into the Matlab workspace.

![image](figs/lab2/fig_54_init_script.png)

- The DOE points are automatically loaded into the Matlab workspace, it is important to check if the DOE points are in the correct form. Open the “V8NA_TestBed_DoE” variable in Matlab’s workspace by double clicking on it and check the values in the “Variable Editor”. Take note that the 1st column is the time stamp which will be used when running the Simulink&copy; block.

![image](figs/lab2/fig_55_variable_editor.png)

- Open “V8NA_TestBed_400.slx” in Simulink&copy;. Run the simulation by pressing [Start Simulation] button. The simulation time is set at 350 seconds. After the simulation has completed, the test results (“V8NA_TestBed_Data”) will be saved in the Matlab workspace.
- Use the “Save_Test_Result.m” script to convert the test result matrix into a csv format. The test will be saved as “V8NA_TestBed_Data.csv”. We will use the test result obtained for the modelling exercise during the modelling lab.
- Now, close the Simulink&copy; model. Save the workspace items as “V8NA_testplan.mat” by clicking [File >> Save Project As]. The saved test plan will be used for the following lab classes.

---
