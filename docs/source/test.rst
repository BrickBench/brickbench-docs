Testing
********

BrickBench supports a set of features tailored to testing and exploring maps.

.. _testing:
Running your project
----------------------

The recommended way of testing your project is to run a test instance, done with 
*File->Test Project*. This will create a new game copy, copy your project into the copy, 
and run it. This is preferred over exporting as it allows you to not have to manage a 
modded copy of the game. It also prevents issues like .pak files not getting removed.

.. note:: BrickBench will create a copy of the game next to your clean copy. This copy
   will take up **NO** extra space on your computer (other than the space used by your
   project files). BrickBench should delete this copy once you close your game, but if
   it fails to do so it is safe to delete it manually.

.. warning:: BrickBench uses *hard links* to create the test copy of the game. Therefore,
   **DO NOT** manually edit the test copy the game makes, as those changes will be reflected
   in your clean copy. If you would like to change files in your test copy, add them as 
   resources as explained :ref:`here <resources>`. This is both safer and allows your changes
   to travel with your project.
    
   Deleting files does not count as editing, so that is safe to do.


Runtime hook
-------------

BrickBench supports a runtime hook to allow viewing and editing of certain game properties
while the game is running. 

To open a hook, open the Runtime Hook tool and click the Start Hook button while the game
is running. This will open a connection to the game and allow BrickBench to read memory
from the game.

Once the hook opens, you should be able to see player 1 and 2 as blue and green rectangles
respectively, and any other characters as yellow rectangles. You can use the `T` key to
teleport player 1 to the current camera position, and `Ctrl+T` to teleport player 2.

In addition, BrickBench allows you to quickly teleport to any map in the game. To do so,
select the map in the dropdown in the Runtime Hook tool and click *Load Map*. This will
reload the map when you return focus to the game. 

.. note:: If the dropdown isn't sending you to the right level, you can also manually set
   the map ID to load.

Hook options
=============

The runtime hook has the following options: 
* Autoload map from current hooked game: When this option is enabled, BrickBench will 
  automatically load the map the player is in.

* Reset map on load: This option resets the map state when a map is loaded. 

* Reset door on load: This option resets the door that the player will enter through when
  entering a map directly.

* Enable global hotkeys: This enables the teleport hotkeys while not in BrickBench.
