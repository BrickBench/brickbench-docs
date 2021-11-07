Editing
########

Editor basics
==============
.. warning::
   BrickBench is still experimental, and currently has **NO UNDO** feature! Please
   back up any projects you are using constantly, especially when doing non-reversible operations
   like model importing. You can backup projects by copying the project .brickbench file.


BrickBench editing operates on *entities*, which are objects that can be selected and manipulated on the editor.
Entities can belong to a map, in which case they can only be selected when their map is open, 
or they can belong to a project in which case they’re accessible whenever the project is open.

The currently selected object is visible in the Inspector tab, which is on the right by default.

.. note::
   If you cannot find the Inspector tab, it may be closed by accident. You can open closed tools by selecting them in *File->Tools*.

Tools
------

* **Inspector**: The primary tool for editing. It allows you to edit object properties for all objects.

* **Project Structure**: Allows you to view and edit the project structure.

* **Objects**: Shows you the standard (non-asset) entities belonging to the current map.

* **Materials**: Displays the materials belonging to the currently open map.

* **Textures**: Displays the textures belonging to the currently open map.

* **Paint Terrain**: Allows you to edit terrain properties visually with a painting-like format.

* **Runtime Hook**: Allows debugging and manipulation of an active game instance.

Editing in the Inspector tab
=============================

The Inspector tab is the main workspace for viewing and editing object. It lists object *properties*,
some of which are editable. Common properties are:

* Name: The name of the selected object. In most cases this name should be unique within the
  given object type (eg. You can have multiple objects named `Object1`, but not multiple gizmos).

* Position: The position of the object in the game world. One common point of confusion is that
  the engine that TT Games uses a coordinate system that reverses the X coordinate. BrickBench
  will try to adjust for that when doing things like model importing, but it may be confusing in
  some cases.

* Rotation: The rotation of the object in degrees, either in one dimension or in all three.
  Due to how rotation works internally, some objects may act weirdly when rotated 180°. 
  The reason for this is explained in the advanced (PUT LINK HERE) section of this page.



Advanced
========

Internals
---------

To allow editing of file formats that are not fully understood, BrickBench editing works by 
immediately applying any changes the user applies onto the file it is editing and then reloading
the file. This allows for great flexibility with editing file formats that may be almost completely 
unknown, but causes editing to be slow (especially on operations that require multiple steps)
and causes certain operations to be confusing (eg. if you rotate something by 180°, it can be 
ambiguous how that rotation was done so BrickBench chooses a different rotation than what you gave
it).
