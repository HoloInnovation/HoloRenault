# HoloRenault

- [Introduction](#introduction)
- [Requirements](#requirements)
  - [Get your computer ready](#get-your-computer-ready)
  - [Tools](#tools)
- [Functionalities](#functionalities)
  - [Mapping the environment](#mapping-the-environment)
  - [Displaying an asset from Unity Store](#displaying-an-asset-from-unity-store)
  - [Independent movement of objects](#independent-movement-of-objects)
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
- [Optimal conditions](#optimal-conditions)
- [License](#license)

## Introduction

The Microsoft Hololens.  
The new mixed reality headset developed by Microsoft was brought to the developer scene in 2016 to offer a new platform for innovation.
As our 4th year engineering project we decided to work with [Actimage](https://www.actimage.com/fr/), a digital transformation expert group, on a new technology that marries the virtual to the real world.

*Mixed reality (MR), sometimes referred to as hybrid reality, is the merging of real and virtual worlds to produce new environments and visualizations where physical and digital objects co-exist and interact in real time.
Mixed reality takes place not only in the physical world or the virtual world, but is a mix of reality and virtual reality, encompassing both augmented reality and augmented virtuality via immersive technology.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Mixed_reality)*

Focused on innovation, we contacted several companies to show how mixed reality could benefit workers working on an industrial level.
We focused our research on the automobile industry and got a contact: with the Quality Roadmap Team Leader at Renault who was interested in this new technology.
We met at the *Microsoft Experiences ’17* in Paris and outlined the needs of the company.
We came to conclusion that it would greatly benefit Renault to have a way to virtually visit a factory to not only train the workers but also record the environment and be able to share it to other workers in other factories.

Today companies are faced with a real problem.  
Assembly lines need to be optimized to guarantee security, and productivity.
That means that our idea could be deployed to other companies in the automobile industry as well as companies working in different sectors.
For safety procedures, it would greatly reduce the time of safety inspections.
A proper placement of the machines is essential.
To fulfill the demand, we developed an application to enable us to modify in real time, the placement of the machines and visualize them while they are running.

We used and applied our engineering knowledge to build our team and the work around the project.
Since this technology is still very new to the scene, a good part of our work  consisted in applying the principles of science and problem solving to move forward.
Today, after a year of research we are sharing our experience with the community providing a solid base of information to future developers.

## Requirements
### Get your computer ready

- Windows 10 Pro, Entreprise or Education is required for full support. More info [here](https://docs.microsoft.com/en-us/windows/mixed-reality/install-the-tools).

### Tools

- [Microsoft Hololens headset](https://www.microsoft.com/en-us/hololens)
- [Unity](https://unity3d.com/)
- [HoloToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)
- [Microsoft Visual Studio Community](https://www.visualstudio.com/downloads/)

:warning: **Check HoloToolkit on GitHub for Unity version compatibility.**

*You will find tutorials at the [Windows Mixed Reality Academy](https://docs.microsoft.com/en-us/windows/mixed-reality/academy) to get you started.*

## Functionalities
### Mapping the environment

*Spatial mapping provides a detailed representation of real-world surfaces in the environment around the HoloLens, allowing developers to create a convincing mixed reality experience.*

*- [Microsoft](https://docs.microsoft.com/en-us/windows/mixed-reality/spatial-mapping)*

![Spatial Mapping](img/spatial-mapping.png "Spatial Mapping")

Most if not every application developed for Hololens will require ```SpatialMapping```.
It is an existing functionality that we only need to add to our application.
When opening the app the headset will make a first mapping of the environment.
In our application, tapping an asset to move it reveals the drawn mesh showing the user where the asset can be placed.

With the latest versions of the [HololToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity), it is possible to tweak the precision of the mesh by adjusting the numbers of triangles of the spatial mapping: ```TrianglesPerCubicMeter```. By default the number is fixed at 500 triangles but can go up to 1200.

As explained in [Hologram 230](https://docs.microsoft.com/en-us/windows/mixed-reality/holograms-230) triangles can be added or removed from the mesh.

### Displaying an asset from Unity Store
It is possible to import assets from the [Asset Store](https://assetstore.unity.com/) as we did for testings.
The platform is a hub where you will find creations from Unity Technologies or members of the community, easily accessible from ``Window > Asset Store`` in the main menu.
An import aspect in Unity is Asset Packages.
Packages are collections of files and data from Unity projects just like .zip files, that you can import into your project or on the other hand export from your project to share.  
For instance, to import a custom package such as the HoloToolkit to your project, go to ``Assets > Import Package > Custom Package`` and select the package from your Windows explorer.

### Independent movement of objects
The main goal of the project was the set up of Renault's machines in a factory.
One of the key feature of the app was the option to select a hologram and to place it wherever the user desired. 
To achieve this, we used the script ``TapToPlace`` provided in the HololToolkit. 
In order to utilize this script, we require in the Unity scene the use of ``Gaze Manager``, ``Gesture Manager`` and ``Spatial mapping``, all provided in the HoloToolKit.
This script allows us to select an asset or hologram and to palce it where mapping is detected.

### Object scaling
Object scaling is an essential feature.
When there is no need of simulation, for example during a presentation, it is most useful to have a smaller model to move around.

In Microsoft Visual Studio to scale an object you need to create a ``Vector3`` as we are working in 3 dimensions.
It takes three float arguments.
To keep accurate information using fractal number, simply add (float) to the variable.

```sh
Vector3 scale = new Vector3((float) 1,(float)1,(float)1);
```

### Creating an object from a menu
In order to set up the factory, our application should have the possibility to instanciate new assets on the scene. 
We added a button *Add Asset* in a menu which allows the user to create a new hologram in front of him whenever he is air tapping the button. 
This hologram is defined in the component panel of the button.
[Here](https://www.youtube.com/watch?v=J7vCS75DC6w) is a demonstration of our app using simple assets.

## Encountered difficulties
### Room complexity
During the development of our application, we tested the Hololens in different environments from a small classroom, to an open space, to an even bigger, factory.
Observations show that mapping varies a lot depending on the spatial variable as well as the materials in the surroundings.
The headset struggles in small rooms as our options with a reduced spatial mapping are limited.
Having furnitures play a role as well.
Different elevations create differences in the mapping and the Hololens is not immune to errors.
Dark objects or walls reflect less light and therefore have a tendency to mess with the spatial mapping.
The results of these errors create discontinuities in the mesh.
Some holes may appear in the mapping and affect object placement as the environment is not recognized.

### New technology
We encountered different types of problems that we tried to solve. 
We couldn't find all the answers on the web as the technology is so recent. 
So a big part of our work was to understand how the device works and try to find the answers on our own.

The community behind the technology is getting bigger. We found some answers to our problems on the [Microsoft Community](https://developer.microsoft.com/en-us/windows/mixed-reality/community) and [Stack Overflow](https://stackoverflow.com/questions/tagged/hololens).  

:bulb: **Use the [Unity Forums](https://forum.unity.com/) & try different keywords in your searches**

## Limitations of the headset
### Assets limits
Let's start with a quick rundown of the specs.
The headset is packing:
 - A custom Microsoft Holographic Processing Unit (HPU 1.0)
 - An Intel 32-bit architecture CPU
 - 2GB of RAM and 64GB of flash storage
 - 900MB hard limit for memory allocation

It is very important to keep applications light enough to maintain 60 frames per second and ensure a comfortable experience.
It is as important to minimize eye-strain and to do that, assets need to be placed in what we call the comfort-zone.
In fact, Microsoft recommends to change the value of the ``Near Clip Plane`` field from the default 0.3 to 0.85, which equates to 0.85 meters.
This is to reduce discomfort experienced when having a hologram too close to the user.

![Hologram Placement](img/hololens-hologram-placement.png "Hologram Placement")

### Difficulties to display complex assets
During our project we used assets of great complexity with over 8 million polygons.
These type of assets are too large for the headset to compute.
Ideally, we found assets need to be 100'000 polygons or lower to be properly handled by the headset.

In this case, a good software for asset simplification would be [Simplygon](https://www.simplygon.com/):

*Simplygon is a 3D computer graphics software for automatic 3D optimization, based on proprietary methods for creating level of detail (LODs) through Polygon mesh reduction and other optimization techniques.*

*- [Wikipedia](https://en.wikipedia.org/wiki/Simplygon)*

However, a simplification from 8M to 100k is a lot to ask, results were not satisfying as polygons were very irregular.
A better way to do this is to first manually simplify the model by deleting unnecessary details invisible from the exterior.
This would greatly improve the simplification process by the software.

### Field of view
Microsoft says the headset covers 35% of the field of view of the user which greatly impacts ease to move around the environment.
It forces the user to move his head more often and results in the appearance of neck pain more quickly.
Placing one hologram rapidly fills the field of view and limits the capabilities of the application.
The biggest drawback is when using large assets of 3 or 4 meters wide.
Already limited by the performance of the headset; the experience is less immersive as the user finds himself inside the asset. (More info under [Assemble multiple assets](#assemble-multiple-assets)).

## Possible improvements
### Assemble multiple assets
Models provided by Renault were too large for a One to One scale.
Testing in a small room caused the user to improperly move around the asset.  
For instance, in a smaller room while the user moves forward in reality, the position in the virtual world did not change and sometimes led to experience a feeling of moving against the direction wanted.
This is explained by the imposing size of the asset.
Being larger than 5 meters wide, the headset struggles to relay the feeling of reality to the user.

An easy fix would be to re-dimension the asset to make it around 4 meters wide, but that would compromise the purpose of using mixed reality as it would mess with the true dimensions and ultimately stripping away the 'reality' variable.  
Another solution would be to cut through the model.
Now as it may work on some machines, it would denaturalize the model once again impacting the immersive experience.

A better solution to minimize the impact on the user experience while enhancing the benefits of the technology would be to rebuild the machine with the headset.  
Let's take an employee in the automobile industry.
By adding parts of the machine to the environment, he would with every addition, contribute to the final assembly.
It is an opportunity to interact individually with each part and learn about their functionalities in the process.

## Optimal conditions
Here is our rundown of ideal conditions for a successful spatial mapping.

**Textures**  
*We recommend a flat bright surface*.  
:heavy_check_mark: Wooden floors  
:heavy_check_mark: Concrete  
:x: Carpet, especially dark toned  
:x: Gravel  

**Spatial variable**  
:heavy_check_mark: Room greater than 10m²  
:x: Round corners  
:x: Sharp 45° corners  

**Furnitures**  
:heavy_check_mark: Closed desks  
:x: Dark metal furnitures  

## License
This document is made available to the community for educational purposes only.  
This document contains intellectual proprety and is protected.  
The idea and application are protected.

Unauthorized use of intellectual proprety without consent of the creators is punishable.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/2.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/2.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/2.0/">CC BY-NC-SA 2.0 Generic License</a>.
