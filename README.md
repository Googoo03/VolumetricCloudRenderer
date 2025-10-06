# **Volumetric Cloud Renderer**

Below are the results of the volumetric cloud renderer that I have worked on for the past month. Below I have also included the process by which the clouds are generated and any and all inspiration for the design process.

## **Why Volumetric Clouds**

For those familiar with my development journey, I am incredibly intrigued by the idea of Procedural Content Generation; the idea that large scale products and content can be generated through simple rules and procedures. Other projects of mine include procedural landmass generation, procedural mesh generation, and this time around, procedural volumetrics.

### Inspirations

Several AAA titles have begun to use volumetric clouds in their games and engines, making me believe it'll be a great starter project to boost both my resume and my skills. In addition to this, content creators have begun to give their own takes on the design process, allowing me to built off their attempts and mistakes and ultimately become better at the process.

## **Design Process**

The overall design process is incredibly simple in theory, however in practice it can become difficult to optimize.

Given an AABB (Axis aligned bounding box) we need to find the two intersections where a ray enters and exits our box. Between these two points we take a set number of subsequent steps, sampling a 3D Worley Noise and Perlin Noise texture
at the world space coordinates of our ray intersections.

At each of these samplings, we mark out an extra ray from our intersection to the scene light (the sun in this case), and repeat the process. This time when sampling our noise textures, the density of the sampling
decrease the amount of light reaching the point respectively.

We continue this process for each of the intersections, and apply a phase function at the end. This is due to clouds exhibiting for of a forward-scatter behavior. This is why clouds are not uniformly lit even though they
are not solid, they reflect much of their light back towards the light, leaving their shadows much darker than usual.

Additional parameters were added to make results more appealing, for example a fog was added for the demo scene, and an ambient light was added into the calculations so dark sides of clouds are not completely black.
In the future, I will be incorporating this into my larger projects, and will be optimizing its algorithm so it can achieve 60fps at full resolution.

## **Results**

<img width="1456" height="453" alt="Clouds_After" src="https://github.com/user-attachments/assets/5fac4f6b-733c-489b-b6e7-6b1ea1acdf72" />
<img width="1512" height="846" alt="Clouds_Demo_Mountain" src="https://github.com/user-attachments/assets/f6fba5b1-a527-4e86-8aa8-a56435c22779" />
<img width="1511" height="840" alt="Clouds_Demo_BackScatter" src="https://github.com/user-attachments/assets/eb948dbe-e518-4bea-b718-27928c56ce91" />

