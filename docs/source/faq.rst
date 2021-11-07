FAQ
####


Troubleshooting
================

Model importing
----------------
*BrickBench says that my model has too many vertices*

TT Games uses a model format that only supports 65,000 vertices per mesh. If your model exceeds
this, there are two options:

* Simplify the model, removing unneeded vertices

* Split the model into multiple parts, each of which has less than 65,000 vertices.

*BrickBench says that my model is not supported on the current map*

Certain maps do not have the correct buffer sizes for the BrickBench model format. We plan
on changing this in a future release.

*BrickBench says that my model contains non-DDS images*

TT Games's engine, and BrickBench by extension, only support DDS images. BrickBench will convert
the filenames if your material has a texture with a .png extension but the same texture with .dds
exists, but it cannot actually convert the file type.

*But why can it not just automatically convert my images?*

The DDS format has different internal formats (DXT1, DXT3, DXT5), each of which has different 
features. BrickBench cannot know which features you would like on your texture, and therefore
cannot automatically convert them.

Exported maps
--------------

*I added a bunch of X gizmo, but they don't show up*

Gizmos have a specific maximum that is set in the maps' .txt file. If you want to add more gizmos of
a certain type than that limit, you need to increase that maximum in the .txt. Editing map files
directly can be done as explained (here (LINK))

*I added a creature spawn to my map with a certain creature type, and it won't show up*

If you are adding a creature to a map, its area needs to have that character as resident. That
process is explained (here (LINK))

*None of my AI changes are taking effect*

If you are exporting your changes to a new directory, be sure to delete the ai.pak file in the
maps you export into. That file contains a copy of all AI data, and not removing it will make
the game use the unmodified AI data instead of your modded copy.

*My custom music isn't playing*

If you have custom music, be sure that it is in .ogg format and the bitrate/frequency is the same
as other songs in the *Audio/_MUSIC* folder.
