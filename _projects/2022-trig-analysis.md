---
layout: project
title: Propeller Configuration Optimization
description: Class project with Graphs
technologies: [eCalc, Python, Java]
image: /assets/images/Code_Flow.jpg
---


Pre-covid Design Build Fly's end-of-semester reports contained analyses of code written to interact with and operate eCalc, the current preferred method of predicting propulsion component performance. The existing Propulsion subteam was unaware of this, and the capabilities and knowledge to do so were lost from the decade prior. Accordingly, an effort was made to investigate past reports regarding eCalc automation to create a new programming allowing quick iterations across a wide spectrum of component options. Ultimately, the goal was to procedurally identify the best propulsion combination given a set of parameters.


An original version of the eCalc Automator program exists in Java. Written by Kyle Wadell, a 2017 ORIE Sophomore, the report and accompanying code takes a different approach to the optimization process. While this report focused on first selecting the proper battery configuration, then finding the optimum motor, Wadell’s process optimizes the battery for the motor. Although a valid approach, access to this code has been mostly loss. Not all applicable code was included in the report, and current versions of the packages make the code outdated. Over the summer, Wadell’s program was rewritten and expanded with Python, which is the current language. In Python, three major packages are used: Selenium, Matplotlib, and Pandas. These programs are both used to effectively read, manage, and display all data collected in the program. Luckily enough, they also have great documentation and ChatGPT knows them very well. Selenium creates a popup browser window through which all functions of the webpage (HTML, CSS, the Console) are accessible. Essentially, the an eCalc iterator program pretends to be the user, plugging in eCalc numbers quickly. Pandas is the key to managing data within the program. The basic components of Pandas are table-like structures called dataframes, which are 2D tables. Matplotlib has been happily used by generations of engineering students in PHYS 1110. Whereas Pandas organizes your data, Matplotlib presents it with graphs.

![capacity plot]({{ "/assets/images/C_mAh_Relation.png" | relative_url }}){: .inline-image-l}

The eCalc Automator program can be configured to multiple use cases. In Prop Sizing, it is primarily a method to narrow down the best few motors. Given a specific battery, the program will attempt to go through each workable motor configuration and optimize its accompanying propeller. These results are
then ranked in a final, exported, table. Its additional purpose to quickly analyze the effects of propeller diameters and pitches on a certain motor-battery combination. The resultant static thrusts and flight times are displayed on a graph. Overall, it can be used to illustrate the relationships between different components, such as battery capacity, motor power, and static thrust. These concepts will be elaborated on further in the report; however, as a greater knowledge of the program’s code is achieved, it can be modified to serve a greater variety of purposes. As the program is currently designed, the code’s flow of information and processes is illustrated.

![capacity plot]({{ "/assets/images/mAh_c_plot.png" | relative_url }}){: .inline-image-l}

The development of this program allowed for the analysis of the relationship between several battery, propeller, and motor properties. As an example, the effect of a battery's capacity and C-rating can be seen on the max current in outputs, which then affects its flight time. Similarily, this plays a role in motor function, and increases its max power consumption.
