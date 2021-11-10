Glossary
#########

Object types
=============
Scene objects (.gsc)
--------------------
* Splines: 3D lines in space that can be used for various things:

  * Camera splines: Splines that are used to define camera movement (configured in the .txt file).
  * Spawn splines: Splines used to define spawn points for characters, often named entry.
  * Door splines: splines that define a door's bounds in addition to a spawn spline for when that door is entered
 
* Mesh: A piece of a 3D model with a fixed vertex format.

* Material: Defines a shader configuration and shader parameters to render a mesh. 

* Model: A complete 3D model, combining a set of meshes with their corresponding materials.

* Model instance: An instance of a model placed in the map.

* Display list: A list of model instances, plus other render parameters.

* Special Object: A model instance that can be moved and/or animated. This is often the base for all interactable objects ingame.

Terrain objects (.ter)
-----------------------
* Terrain Group: A mesh consisting of lists of quads with optional surface properties, used for collision.

* Terrain Platform: A terrain group attached to a SpecialObject, used for moveable terrain.

* Infinite Wall: a list of points defining the borders of a 2d vertically infinite wall.

AI (.ai2)
---------
* Creature Spawn: A location at which an AI character may spawn when the map is loaded. The
  character type and active script are defined in the creature spawn.

* Locator: A location that can be used by AI in scripts as a marker or destination.

Gizmos (.giz)
---------------
* Lever: Pullable levers.

* Panel: Panels that only allow certain character types (or characters disguised as those character types) to interact with them.

* HatMachine: Objects that allow most characters to get a specific set of headwear, often for use with Panels.

* ZipUp: Objects that blaster characters can zip/swing around with.

* PushBlock: Pushable blocks, often for use in puzzles.

* Gameplay Graph (.git file): Defines connections that allow gizmos (and other objects) to cause changes in the game world.

  * An example would be a lever causing an obstacle to move.

