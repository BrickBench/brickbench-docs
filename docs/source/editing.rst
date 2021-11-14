.. _edit-start:
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
   If you cannot find the Inspector tab, it may be closed by accident. You can open closed 
   tools by selecting them in *File->Tools*.

Tools
------

* **Inspector**: The primary tool for editing. It allows you to edit object properties for all objects.

* **Project Structure**: Allows you to view and edit the project structure.

* **Objects**: Shows you the standard (non-asset) entities belonging to the current map. 
  You can also toggle visibility of map objects by clicking on the column below the eye icon.

* **Materials**: Displays the materials belonging to the currently open map.

* **Textures**: Displays the textures belonging to the currently open map.

* **Paint Terrain**: Allows you to apply custom properties to the terrain mesh.

* **Runtime Hook**: Allows debugging and manipulation of an active game instance.

Editing in the Inspector tab
=============================

The Inspector tab is the main workspace for viewing and editing object. It lists object
properties, some of which are editable. Common properties are:

* Name: The name of the selected object. In most cases this name should be unique within the
  given object type (eg. You can have multiple objects named `Object1`, but not multiple gizmos).

* Position: The position of the object in the game world. One common point of confusion is that
  the engine that TT Games uses a coordinate system that reverses the X coordinate. BrickBench
  will try to adjust for that when doing things like model importing, but it may be confusing in
  some cases.

* Rotation: The rotation of the object in degrees, either in one dimension or in all three.
  Due to how rotation works internally, some objects may act weirdly when rotated 180°. 
  The reason for this is explained in the :ref:`advanced <internals>` section of this page.

Editing terrain properties
==========================

To paint terrain, open the Paint Terrain tool and select the surface property you want.
Once you select the property you want, click the painbrush icon in the toolbar on the top of the 
window. You can then click on terrain meshes to paint them with your selected property. 

To finish editing terrain, click the pan/select buttons.

.. note:: Some surface properties may behave differently on different maps, as the game can
   redefine how a property behaves depending on the map.

Adding objects
===============

Adding objects is done through the Objects tab. To add a new object, click the + button
on the top right, and then select the object you want to add. For most standard objects, this
will place your new object onto the current camera location. 

Certain, more complex objects (such as models) will select a new object that can be used 
to tune object properties before adding the object to the map.

.. _assets-import:
Importing assets
===================

Project assets are imported through *Import -> Import Asset*. If you would like to add a
new project asset, details are available :ref:`here <assets>`.

Importing textures
--------------------

.. note:: The TT Games engine primarily supports only DDS files (there is basic PNG support). 
   Therefore, BrickBench expects any textures that are added to be in a .dds format. If
   you do not have your textures in .dds, please convert them before using them either alone
   or as part of a model.

To import a texture, select the texture in the Textures list in the Import menu and click Next.
You will then be able to select if you would like to import the texture as a new texture 
or to replace one or multiple textures. you can select multiple textures to quickly replace a
set of textures with your asset.

Importing models
-------------------

To import a model, select your model in the Models list in the Import menu and click Next.
You will then be able to select the following options:

* Reverse winding: This should be used if your model appears inverted and the terrain colors
  seem inverted (often times seen as upward-facing surfaces being purple) after importing.

* Mirror on X axis. As noted above, TT Games's engine has an inverted X axis from many editors.
  If BrickBench does not properly compensate for this, you can force a mirror with this option.

* Generate with normal shading: This enables lighting on your imported model. This should be selected
  if you would like lights to apply to your model. Note that this option requires your model to have
  proper normals exported from your 3D editor.

The import process may take some time. After importing, you will be able to see your imported model
in the Objects tree. You can then add your model into the map like any other object.

.. warning::
   Model importing is a very complex process internally with many moving parts. In addition,
   there is no way currently to undo an import operation. Please **BACK UP** your project
   before doing any model importing.

Advanced
========

.. _direct-editing:
Editing files directly
-----------------------
If you would like to edit a map file directly (either in a hex editor or a text editor), select
the map the file is in in the Project Structure tab. Then, in the Inspector, double click the 
file you would like to edit. This will open the file in your editor of choice.

Once you are done, be sure to save your work for that file BEFORE you save the project.

.. _internals:
Internals
---------

Since most file formats aren't completely understood, BrickBench immediately applies any user
changes onto the file that is being edited and reloads the file. This allows for great 
flexibility when editing almost completely unknown file formats, but causes editing to be
slow (especially on operations with multiple steps). 
In addition, this causes certain operations to be confusing 
(eg. if you rotate something by 180°, it can be ambiguous how that
rotation was done so BrickBench chooses a different rotation than what you gave it)
