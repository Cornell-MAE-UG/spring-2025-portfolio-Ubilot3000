---
layout: project
title: "Heat Transfer Homework"
subtitle: "Still figuring out what enthalpy is..."
date: 2025-3-9
image: assets/images/how-the-coolant-circulates.png
tags: [fluids, modelling, groupwork]
file: /assets/files/HW5.pdf
---

Thermal management is something I find directly relevant to engineering as a profession; most things we design release more heat than can be passively dissipated, so the systems we build to handle that matter a lot. In this homework, we started by analyzing the effectiveness and efficiency of a single cooling fin and how temperature varies across it, giving us a detailed look at one small component of a larger system. We then compared different models to evaluate whether lower-fidelity approximations were appropriate, before expanding to a fin array that also accounted for heat released at the base and a heat source on the back side. This showed how critical fins are to temperature management. In the second problem, we looked at heat generation itself through current running through a wire, and saw how our model changes depending on whether we're analyzing transient or steady-state behavior.

This assignment felt especially useful because thermal management is something I already think about on my project team. We build an RC-scale aircraft each year and run 100A through a motor surrounded by PLA plastic, with an ESC tucked inside a CFRP fuselage. As the motor ramps up, there's a transient effect of wire resistance releasing heat that gets funneled backwards by the airflow. ESCs of this size also come with fins and require careful placement on the outside of the fuselage where forced convection can keep them cool. These effects are something that clicked a lot more after working through this assignment.

<iframe src="{{ page.file | relative_url }}" width="100%" height="800px" style="border:none;">
        This browser does not support PDFs. Please download the PDF to view it: <a href="{{ page.file | relative_url }}">Download PDF</a>
</iframe>
