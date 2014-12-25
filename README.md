Opis
---------------------

This project is intended to become a Minecraft Classic clone using HTML 5 technologies, most notably WebGL and WebSockets. No third-party libraries are used, with the exception of glmatrix and socket.io. People who have written similar demos used libraries such as *three.js*, but it is
both foolish and inefficient to use a 3D engine for rendering large amount of blocks.

Credits
---------------------
+ @Overv - stworzenie podstawy dla tej wspanialej gry
+ @artur9010 - prace nad rozwojem wersji desktop
+ @joda17 - prace nad rozwojem wersji mobilnej i naprawa błędów po tym nupie ↑↑↑

=======
Struktura plikow
---------------------

+ *js/* - Zawiera wszystkie pliki odpowiadajace za funkcjonalnosc WebCrafta.
+ *media/* - Zawiera pliki graficzne
+ *style/* - Zqwiera czcionki oraz pliki CSS
+ *singleplayer.html* - Klient singleplayer
+ *mobile.html* - Klient dla urzadzen mobilnych (głownie smartfony z FirefoxOS)

Moduły
---------------------

The two front-ends invoke the available modules to deliver the components necessary for the gameplay and graphics of either the singleplayer or multiplayer experience. The available modules are listed below.

**Blocks.js**

This is the most *moddable* module, as it contains the structure with the available block materials and their respective properties. It also contains functions invoked by the render class for proper shading and lighting of blocks.

**World.js**

This is the base class, which all other modules depend on. Although it is a very important module, it is also the most passive module. It contains the block structure of the world and exposes functions for manipulating it.

**Physics.js**

This module has strong roots in the world class and simulates the flow of fluid blocks and the gravity of falling blocks at regular intervals. It has no specific parameters and is simply invoked in the game loop to update the world.

**Render.js**

This is the module that takes care of visualizing the block structure in the world class. When a world is assigned to it, it sets up a structure of chunks that are updated when a block changes. These chunks are mostly just fancy Vertex Buffer Objects. As this module takes care of the rendering, it also houses the code that deals with *picking* (getting a block from an x, y position on the screen).

**Player.js**

Finally there is also the module that handles everything related to the player of the game. Surprising, perhaps, is that it also deals with the physics and collision of the player. Less surprising is that it manages the material selector and input and responds to it in an update function, just like the physics module.

**Network.js**

This module makes it easy to synchronize a world between a server and connected clients. It comes with both a *Client* and *Server* class to facilitate all of your networking needs.
