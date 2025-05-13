---
layout: project
title: Speaker CAD Rendering
description: Advanced CAD Project
technologies: [Autodesk Fusion]
image: /assets/images/Speaker.png
---

For a class, we were asked to CAD a complex object. This design was meant to illustate our advanced CAD modelling tenchniques and to explore the rendering capabilities in Autodesk's Fusion 360. We got to choose a fun, interesting, and challenging object to model and render - something we already had in our rooms. As part of the requirement, this object would have to contain 4 seperate pieces which could be assigned different materials. We would also have to have a sweep, loft, patterned feature, rib, emboss, or variable radius fillet.

![Photo of old radio]({{ "/assets/images/SpeakerAssembly_1.png" | relative_url }}){: .inline-image-l}

I was inspired by a Marshall Speaker I had recieved for christmas my senior year in high school. As an engineer, I was always interested in the ways sounds could be modulated in order to produce certain sensations or feelings. How simple frequencies and amplitudes could have so much meaning. Therefore, significant effort went into planning just how I would approach my CAD.

My strategy was to break up the speaker into multiple smaller, more manageable components. I decided on four different component types: the control knobs, handle, handle knobs, and main speaker body. In the final assembly, there are three volume knobs. CADding the main speaker body, I created a prism using three of my main geometric dimensions, which I later filleted significantly. Where I expected the control knobs to go, I added 2mm deep divots. The frame of the speaker I made of rubber, but the actual sound producing part I had to separate produce from a different material. Perhaps sub optimally, I cut the middle of the speaker out, and then extruded back the same space, this time creating a new body.  Unaware of how to construct the mesh design present on the speaker, I opted to create a similar effect using a rectangular pattern implemented on circular cuts with 45 degree fillets. A lighter plastic was used than in the actual model so that this mesh could be seen on the rendering. A single M was also included rather than the Marshall writing, as for an unknown reason it interfered with the rectangular pattern when extruding.  

The control knob was made through a revolve. The outdents surrounding it were created by embossing a sketch on the outer surface, after which I completed a circular pattern. The handle knobs were also revolves. The handle (made from leather because a closer material could not be found) was made by sketch and extrusion, after which the side holes were cut. The edges were filleted for a smoother appearance. Next time, there would be a different texture used for the inside and outside of the handle. 


![Photo of old radio]({{ "/assets/images/SpeakerAssembly_2.png" | relative_url }}){: .inline-image-l}


