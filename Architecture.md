Contents

1 Introduction
    1.1 Visualization tool for browser
    1.2 Research questions
    1.3 Limitations
    1.4 Structure of report
2 Related Work
    2.1 An optimal solution for implementing a specific 3D web application
    2.2 Ambient Occlusion for Dynamic Objects and Procedural Environments
    2.3 Photorealistic Texturing for Modern Video Games
    2.4 IKEA - Home planner
    2.5 Three.js - Physically accurate incandescent bulb
    2.6 Babylon.js - Physical based rendering
    2.7 Xeogl.js - Importing and loading a more complex model and using different
    materials
3 Background
    3.1 HTML
    3.2 Javascript and Libraries
    3.3 WebGL
    3.4 Lightings
    3.5 Ray-tracing
    3.6 PBR - Physically Based Rendering
    3.7 3D-models, maps and textures
4 Method
    4.1 PBR
    4.2 Libraries
    4.3 Lighting
    4.4 Mapping and textures
    4.5 Web-survey
    4.6 Camera and movement in the scene
5 Implementation
    5.1 Localhost server - Node.js
    5.2 Creating the scene
    5.3 Lighting
    5.4 Baseboards
    5.5 PBR
    5.6 Mapping and textures
    5.7 GUI
    5.8 Shadows
6 Result and discussion
    6.1 Prototype
    6.2 Web-survey results
    6.3 Survey evaluation
    6.4 Discussion
7 Conclusions and future work 30
    7.1 Conclusions
    7.2 Future work




1.1 Visualization tool for browser

As the web continues to grow, new techniques and tools to visualize arises. A good visu-
alization is vital in most areas such as the game industry, video industry, web-shopping,
architectural and medical industry. This is often needed to promote and market the product
to a wider audience or present important data. In order to create a good and realistic visual-
ization a number of fields have to be explored: Lightings, Textures, Maps, Materials, Models,

Shadows, Renderer, Camera.
It can be hard to get a good understanding of a product from a web-shop using only
images. Furthermore a time-consuming task to take good looking images for multiple prod-
ucts for a web-shop. A visualization tool can be used to visualize a product in 3D and to
quickly get photos on the product using a single 3D-model. Many benefits comes with a 3D-
visualization tool, such as seeing how it looks in the scene, being able to rotate it and get a
sense of scale on the product. As well as being able to modify the product in real time, this
could for example be changing the material of the model or the lighting in the scene using
different controls. When developing a visualization tool for the browser it is important to
both think about the user and the implementation process. The tool needs to be user-friendly
and the implementation can be simplified by choosing appropriate tools and libraries that
fits the desired requirements of the visualization. To simplify the coding experience a lot of
JavaScript libraries are built upon WebGL to make it more intuitive for developers.
This Master Thesis was proposed by Valbo Trä in Gävle. The goal of this Master Thesis is
to develop a prototype for an interactive visualization tool for baseboards in the web browser,
to help the user see how the baseboard can look in a scene and get a better sense of the prod-
uct. Also the tool will be more effective in that it only needs one 3D-model per baseboard
instead of using multiple images. Another aim of the thesis is to answer the research ques-
tions in the next section. The tool is supposed to be able to visualize different baseboards in
an appealing way for the user to view in 3D. The focus will be on making the visualization
look good and try to resemble the real world as close as possible. This will be achieved by
looking at different lighting sources, mapping methods, and comparing libraries and tools to
be used. Furthermore the prototype is supposed to work for different baseboards so a more
generalized solution is needed.



2.5 Three.js - Physically accurate incandescent bulb
This is an example on how to make use of the Three.js library to make a physically accurate
incandescent bulb. The example shows a good, yet simple visualization on a scene. The
scene have a few models loaded with some textures. A lighting source in form a a bulb and a
floor with wood texture. The user can choose to toggle on and off shadows and increase the
power of the bulb or decrease it, as well as changing the exposure and hemisphere radiance,
through a GUI. The light sources used in the scene is one point light for the bulb, and a
hemisphere light for the scene.

3.1 HTML
HyperText Markup Language (HTML5) is a standard for developing in the web that includes
many functionalities, and was fully developed in October 2014. The new features of HTML5
makes the web more dynamic and provides faster connections between servers and clients.
Rendering graphics in 3D to the web became much easier by HTML5, because of the canvas
tag. Web sockets is another part that is included in the HTML5 standard and allows full
duplex communication between a server and a browser, which makes the web faster.

3.2 Javascript and Libraries
JavaScript is a interpreted scripting language which makes it very flexible. Besides HTML
and CSS it is one of the core languages for programming to the web. There exist dozens
of different JavaScript libraries and frameworks, many of which use WebGL(Web Graphics
Library), such as: Three.js, Babylon.js, Xeogl.js, Pixy.js, Unity and A-frame.

Three.js
Three.js is one of the most popular JavaScript library, with exceptional documentation and
examples provided. Most importantly, it got plenty of contributors and an active community.
Three.js simplifies WebGL to the developer in a lot of ways with different objects, methods
and features. Some of the features of the Three.js library used in the implementation of 3D
graphics are presented below:
1. Renderers: WebGL, <canvas>, <svg>
2. Scenes: Addition and removal of objects
3. Cameras: Orthographic and perspective along with various controllers
4. Lights: Ambient, direction, spot and hemisphere lights
5. Materials: Basic, Lambert, Phong, MeshStandardMaterial and more along with textures
6. Geometry: Plane, cube, sphere, torus, and tube.
7. Objects: Meshes, particles, sprites, lines
8. Loaders: For different formats, such as obj, json, gltf, glb
The scene node map of Three.js can be seen in Figure 3.1, from. It describes what kind
of 3D-object elements are added to the scene to render. The renders job is to render all the
elements together and display it to the screen accordingly.

3.3 WebGL

WebGL is a JavaScript API for rendering interactive 2D and 3D graphics within any com-
patible web browser without the use of plug-ins. WebGL is fully integrated with other
web standards, allowing GPU-accelerated usage of physics and image processing and effects
as part of the web page canvas element from HTML5. All major browsers support WebGL,
both for desktop and mobile devices. According to 97 percent of all users can use WebGL.
See Figure 3.2 below for more information on what browsers are supported. WebGL runs on
the GPU and is a low-level programming language, meaning it is harder for developers to
understand. As mentioned before a lot of JavaScript libraries have been made to simplify the
coding experience but still being able to take advantage of working at the GPU.

Scene, Renderer and Camera

A 3D-scene contains all the objects that should be sent to the renderer. It consists of a three
dimensional area where the different objects is positioned in a coordinate system (x,y,z). The
scene handles the interaction between the different objects like camera, lights and 3D objects.
The renderer in WebGL renders the scene object and takes in some parameters. Cameras are
essential when building and rendering a scene. They determines how the objects should be
presented to the user and by moving the cameras the view of the scene changes. This is done
by a transformation matrix which changes the values in the vertexBuffer and will move the
scene. There are two different types of cameras: Perspective and Orthographic.
The difference between a perspective and an orthographic camera can be seen in figure 3.4
below, from. Both cameras are used for their different projections in different situations.
A perspective camera gives a better depth, while a orthographic camera have the quality
that objects in the projection have the same dimensions, regardless of the distance from the
observer.

In all visualizations lightings can make a huge difference on the visual appearance. There are
plenty of different lightings to choose from and all have there unique strengths and weak-
nesses. A lot of times a combination of lights are used to make realistic and stunning lighting.

However it can be really hard to know what lighting one should use to create an appealing
or realistic scene.
Below are some common lighting in WebGL and more specifically the ones in Three.js
described. Most 3D-visualization libraries use the same lighting sources even though the
name can be of slight variance.

• Ambient light, is the light that globally illuminates all other objects in the scene equally.
It is a non-directional meaning it cant cast shadow.
• Hemisphere light, is a source positioned directly above the scene, with color fading
from the sky color to the ground color. This light cannot be used to cast shadows.
• Directional light, is light that is emitted from a specific direction. This is light that is
coming from so far away that every photon is moving parallel to every other photon.
For example, sunlight is considered a directional light source. It can cast shadows.
• Point light, is a light that is being emitted from a point, radiating in all directions. This
is how many real-world light sources usually work. A light bulb emits light in all direc-
tions. A point light can cast shadows.
• Spot light, this light gets emitted from a single point in one direction, along a cone that
increases in size the further from the light it gets. There is actually 2 cones, an outer
cone and an inner cone. Between the inner cone and the outer cone the light fades from
full intensity to zero. This light can cast shadow.
• Rectangular Area Light, is the last type of lights in Three.js which represents exactly
what it sounds like, a rectangular area of light like a long fluorescent light. This light
only works with physical based materials.

Image Based Lighting

Image based lighting (IBL) evolved from the reflection-mapping technique and is the process
of illuminating scenes and object with images of light from the real world. According to
the basic steps in IBL are: "1. Capturing real-world illumination as an omnidirectional, high
dynamic range image; 2. mapping the illumination onto a representation of the environment;
3. placing the 3D object inside the environment; and 4. simulating the light from the environ-
ment illuminating the computer graphics object." Worth noting is that the images should be
omnidirectional and in high dynamic range (HDR) for best result.


5.1 Localhost server - Node.js

The first thing to be made was to create a local environment to test the models. Due to security
reasons in the browser to view and load in models a local server is needed. This was created
and set-up using the JavaScript library Node.js. A JSON file was created called package as well
as a JavaScript file called index.js. The index file was used to set up a local port that could be
reached by specifying the port in the browser after running the node package manager in the
console using the command npm start.
5.2 Creating the scene
When the localhost server was up and running, Three.js was imported locally. Thereafter
3D-models could be loaded in and viewed in the browser using different loaders in Three.js
for different file-formats. The base scenery was created using a 3D-model that built up the
floor and the two walls, henceforth called base model. This was made so that it was one file
but three different objects. The models were made separately from each other to being able
to tweak each element separately and position them easier. The baseboard was then added
to the scene with a position depending on what type of baseboard it was. All models were
created using the 3D-software from Autodesk called 3ds Max.
Implementing a working 3D-view in Three.js was easy and straight forward, due to plenty
of examples on how to set-up a 3D-view already exists for different scenes. It is mainly about
declaring a scene object through a constructor, adding and specifying the camera that should
be used and the renderer to use in the scene. As well as assigning appropriate values in the
constructors that suits the needs of the visualization. Furthermore a lot of variables regarding
the renderer and camera exists that can manually be set in the code. An implementation to
rescale the camera based on the user resizing the window was implemented early on.

Skybox
The scene looked pretty boring whilst only loading in the base model and some baseboards,

and a black background. To fix this a skybox was added and implemented using the cube-
mapping technique described in section 3.7. It was easy to make the cube-map in Three.js by

setting the corresponding images to the sides of the cube.
Movement
A script was found in the Three.js library called OrbitControls.js. By including and utilizing
this script, the user can traverse the scene in different ways. The movement options includes
zooming, panning and rotating the scene which are done with different mouse options, for
example zooming in the scene is done using the scroll wheel.
Tracking performance
To track the fps and memory usage during runtime of the visualization tool a script called
stats.js was found and implemented. This script was easily utilized by declaring a variable
and calling the constructor and then running a code in the update function. This would come
in handy to see that the prototype was running smooth without any noticeable frame drops
or memory issues.



5.3 Lighting

The implementation of lights started with just adding a ambient lighting to the scene. How-
ever this became quite dull and was further developed to include other light sources as de-
scribed in 3.4. Using Three.js it was easy to try and add different lights to the scene, by defin-
ing different positions and starting intensity values. Another great thing with adding lights

in Three.js is that you can define helper functions for specific lights. These helper functions
shows how the light is interacting with the scene, i.e where it starts and what it target.
In Three.js there is a setting on the WebGLRenderer called physicallyCorrectLights. Which
if set to true it effect how the light falls off as distance from light like in the real world. This
option however only affects the point light and spot light. Physically realistic light values in
terms of power and falloff was tested this way but was hard to get right as also described by
Brent Burley. It became apparent that it would be good to have the user manually being
able to change the power/intensity values of the different lights during runtime. This also
made the lighting more generalized in the sense that the user could tweak the lighting to his
or her liking. This was achievable by adding a corresponding parameter for the different light
source to the GUI.



5.4 Baseboards

The implementation of the baseboards begun using small baseboards and placing them ac-
cordingly on the screen to not overlap and a function was written to space them correctly.

However later on this was improved by changing the baseboard size in 3ds Max and then
just scale if needed in Three.js for any given axis. This way it became less code and better
performance since less models were needed to be drawn.
The baseboard were imported to 3ds Max, then given a physical material from the Arnold
renderer, unpacked UVW and a texture was added. An issue occurred due to Arnold utilizing
the Specular-Glossiness workflow, while the MeshStandardMaterial in Three.js utilizes the
Metalness-Roughness workflow. Furthermore 3ds Max does not support saving files in .glb
format by default. This was solved by installing and utilizing a plug-in called Babylon.js to
export the baseboard model to .glb format and to the Metalness-Roughness workflow. This
was done to preserve the physical materials and being able to use a corresponding .glb loader
in Three.js later on.

5.5 PBR

Three.js supports physical based materials called MeshStandardMaterial and MeshPhysical-
Material. The former is used in this prototype since it was deemed good enough and is

slightly faster than the latter. The biggest difference between the two is that MeshPhysical-
Material is an extension to MeshStandardMaterial and therefore has a clear coat value, that

allows for greater control of the reflectivity. Many different materials were tested, and the
physical ones described looked much better than the non-physical ones.
A Metallic-Roughness workflow was implemented into sliders in the GUI to control the

parameters on the Base-scene and baseboards separately from each other. This was achiev-
able by making group object and adding the corresponding children to each node in the

group. Then it was just a matter of traversing the scene with the group name and assigning

the value when the user changed the value in the update function. This way one slider con-
trolled the roughness of the material, and another slider controlled the metalness that could

be changed during runtime.
The technical details and approach to PBR in Three.js is based on the paper made by Brent
Burley. The MeshStandardMaterial got plenty of properties to set. Amongst the properties
are different maps such as the ones that were discussed in chapter 4. The next section will go
into how the mapping was implemented for the prototype.


5.6 Mapping and textures

As previously mentioned in section 4.4, the maps that would be implemented were the fol-
lowing: Environment map, Light map, AO map and Normal map. The environment map

in Three.js takes in a texture cube which had to be created. An option was then made to
be able to change the environment map during runtime on the baseboards. This was only
implemented on the environment map but could be made for all the maps. Moreover the
intensity of the different maps could be increased or decreased during runtime and this was
implemented for all maps.
The light map and AO map was implemented using a single texture. However in Three.js

these maps requires a second set of UVWs to work properly, which is explained in the docu-
mentation. Once the UVWs were added and assigned to the correct object, a texture could be
added and a starting intensity value assigned.

The normal map was tested on a baseboard by adding a texture. In Three.js the nor-
mal map works by letting RGB values affect the surface normal for each pixel fragment and
change the way the color is lit. An unexplained bug appeared while testing the normal map
and artefacts appeared on the side of the baseboard, as can be seen in figure 5.1. These arte-
facts most likely appear because of how the baseboard model is made, and because of how
the normals are aligned on the model. Although this is not confirmed, since the map was
only tested for this one baseboard at the time.
The main texture for the baseboard, floor and wallpaper was given by Valbo Trä, however
later on a free texture for the floor was found and used. The different maps did unfortunately
not have the appropriate textures that fit the scenery in a good way. Instead textures was
used to just show the effect that the different maps could accomplish. This is something that
could be improved on for the future.
