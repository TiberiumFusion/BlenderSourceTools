## BlenderSourceTools+ for 2.79
Fork of the final BlenderSourceTools release for Blender 2.79 with some improvements and fixes.

## Notable additions

### Fuzzy VTA matching
Blender/BlenderSourceTools has some precision issues that become very problematic when importing SMD and DMX meshes with dense vertices. Specifically, the VTA format is slightly more precise than Blender's default floating point type, which causes high-detail flexes to become garbled when imported by official BlenderSourceTools. This fork "fixes" the issue by matching inequal, but very similar, flex vertices to the reference mesh at an epsilon of 0.0001 (default). This is the one degree higher than the level of precision used by Crowbar when decompiling models and should be suitable for almost all models. The epsilon can be set to any desired value, however, before SMD/VTA/DMX/QC import.

### QC eyeball bone generation
Adds an option when importing QCs to generate unweighted bones for all $eyeball commands, with or without automatic leaf bones. These dummy eye bones can be useful for developing 2D eye tracking techniques when the model is exported for use in other engines or 3D packages.

### Armature origin options
In addition to the default behavior of setting the armature origin from $origin, there is a new option to set the armature origin from the median point of the QC's $bbox. This is most useful when importing and arranging models that constitute a map, since, instead of defaulting to (0,0,0), Hammer uses the median point of each MDL's bounding box as its origin when no $origin is defined.

### Callback Operation on Import
Blender does not provide a way to wrap and await the completion of operators that are raised with INVOKE_DEFAULT and use the file browser (in other words, all file import operators). To work around this, the SMD/VTA/DMX/QC import operator now includes the option to specify an operator to run immediately after the file import finishes.
