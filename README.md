Description
---------------------

WebCraft is Minecraft Clone written in JavaScript (WebGL)

File structure
---------------------

+ *js/* - Zawiera wszystkie pliki odpowiadajace za funkcjonalnosc WebCrafta.
+ *media/* - Zawiera pliki graficzne
+ *style/* - Zqwiera czcionki oraz pliki CSS
+ *singleplayer.html* - Klient dla desktopu
+ *mobile.html* - Klient dla urzadzen mobilnych (głownie smartfony z FirefoxOS)

Init code
---------------------
```javascript
			var renderCanvas = document.getElementById("renderSurface");
			
			var world = new World( 60,60, 100, 80, 2, 0.1 ); //create new world
			world.createWorld(); //generate map
			
			var render = new Renderer( "renderSurface" ); //create new render
			render.setWorld( world, 16 ); //set world for the render
			render.setPerspective( 80, 0.01, 210 ); //set perspective
			
			// Fizyka
			//var physics = new Physics();
			//physics.setWorld( world );
			
			var player = new Player(); //create new player
			player.setWorld( world ); //set's player world
			player.setInputCanvas( "renderSurface", 1 ); //1 for desktop version, 2 for mobile version
					
			requestAnimationFrame( function loop(){
				//var time = new Date().getTime() / 1000.0;
				
				//physics.simulate();
				
				player.update(); //update player
				
				render.buildChunks( 20 ); //build chunks
				
				render.setCamera( player.getEyePos().toArray(), player.angles ); //set camera
				render.draw(); //draw the world !
                
				requestAnimationFrame(loop, renderCanvas);
			}, renderCanvas );
```

Pull requests
---------------------
Use
```javascript
function myFunction(var1, var2) {
    [...]
}
```
not
```javascript
function myFunction(var1, var2)
{
    [...]
}
```