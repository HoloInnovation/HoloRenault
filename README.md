# HoloRenault

- [Introduction](#introduction)
- [Functionalities](#functionalities)
  - [Mapping the environment](#mapping-the-environment)
  - [Displaying an asset in Unity Store](#displaying-an-asset-in-Unity)
  - [Unity Store](#unity-Store)
  - [Independent movement of objects](#independent-movement-of-objects])
  - [Object scaling](#object-scaling)
  - [Creating an object from a menu](#creating-an-object-from-a-menu)
- [Encountered difficulties](#encountered-difficulties)
  - [Room complexity](#room-complexity)
  - [New technology](#new-technology)
- [Limitations of the headset](#limitations-of-the-headset)
  - [Assets limits](#assets-limits)
  - [Difficulties to display complex assets](#difficulties-to-display-complex-assets)
  - [Field of view](#field-of-view)
- [Possible improvements](#possible-improvements)
  - [Assemble multiple assets](#assemble-multiple-assets)
  - [Have a modified asset](#have-a-modified-asset)

## Introduction

The Microsoft Hololens. The new mixed reality headset developed by Microsoft was brought in 2016 to the developers scene to offer a new platform for innovation.
As our 4th year engineering project, we decided to take that road to work with Actimage, a digital transformation expert group and work on a new technology that marries the virtual to the real world.

*Mixed reality (MR), sometimes referred to as hybrid reality, is the merging of real and virtual worlds to produce new environments and visualizations where physical and digital objects co-exist and interact in real time.
Mixed reality takes place not only in the physical world or the virtual world, but is a mix of reality and virtual reality, encompassing both augmented reality and augmented virtuality via immersive technology.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Mixed_reality)*

Focused on innovation, we contacted several companies to show how mixed reality could benefit workers working on an industrial level.
We focused our research on the automobile industry and got a contact: with the Quality Roadmap Team Leader at Renault who was interested in this new technology.
We met at the Microsoft Experiences ’17 in Paris and outlined the needs of the company.
We came to conclusion that it would greatly benefit Renault to have a way to virtually visit a factory to not only train the workers but also record the environment and be able to share it to other workers in other factories.
Today companies are faced with a real problem. Assembly lines need to be optimized to guarantee security, and productivity.
That means that our idea could be deployed for other companies in the automobile industry as well as other companies in different domains.
For safety procedures, it would first greatly reduce the time for safety inspections.
A proper placement of the machines is essential.
To fulfill the demand, we developed an application to enable us to modify in real time, the placement of the machines and visualize them while they are running.
We used and applied our engineering knowledge to build our team and the work around the project. Since this technology is still very new to the scene, a good part of our work  consisted in applying the principles of science and problem solving to move forward.
Today, after a year of research we are sharing our experience with the community providing a solid base of information to future developers.


## Functionalities
### Mapping the environment

To start, our application need to map the environment around the HoloLens. It's an existing functionality that we only have to implement in our application. During the utilization of the normal device's app, the mapping is continuous so we had to do the same in our program.
Scan the environment is a normal script, we had to use, called "SpatialMapping". It also allows you to see the mesh draw on the the different elements of the room your in.
Later it will also gives you the possibility to place different elements.


### Displaying an asset in Unity Store


### Unity Store


### Independent movement of objects


### Object scaling


### Creating an object from a menu


## Encountered difficulties
### Room complexity


### New technology


## Limitations of the headset
### Assets limits
Let's start with a quick rundown of the specs.
The headset is packing a custom Microsoft Holographic Processing Unit (HPU 1.0) with an Intel 32-bit architecture CPU.
It is equipped with 2GB of RAM and 64GB of flash storage.
It has a hard limit of 900MB for memory allocation.

It is very important to keep applications light enough to maintain 60 frames per second and ensure a comfortable experience.
It is as important to minimize eye-strain and to do that, assets need to be placed in what we call the comfort-zone.
In fact, Microsoft Windows Mixed Reality Academy recommends to change the value of the Near Clip Plane field from the default 0.3 to 0.85, which equates to 0.85 meters.
This is to reduce discomfort experienced when having a hologram too close to the user.

![Hologram Placement](img/hololens-hologram-placement.png "Hologram Placement")


### Difficulties to display complex assets
During our project we used assets with great complexity with over 8 million polygons.
These type of assets are too large for the headset to compute.
Ideally, we found assets need to be 100'000 polygons or lower to properly be handle by the headset.

In tis case,a good software would be Simplygon:

*Simplygon is a 3D computer graphics software for automatic 3D optimization, based on proprietary methods for creating level of detail (LODs) through Polygon mesh reduction and other optimization techniques.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Simplygon)*

However, a simplification from 8M to 100k is a lot to ask, results were not satisfying as polygons were very irregular.
A better way to do this is to first manually simplify the model by deleting unnecessary details invisible from the exterior.
This would greatly improve the simplification process by the software.

### Field of view


## Possible improvements
### Assemble multiple assets


### Have a modified asset
