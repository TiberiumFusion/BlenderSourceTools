## BlenderSourceTools+ for 2.79
Fork of the final BlenderSourceTools release for Blender 2.79 with some improvements and fixes.

## Notable additions

### Fuzzy VTA matching
Blender/BlenderSourceTools has some precision issues that become very problematic when importing SMD and DMX meshes with dense vertices. Specifically, the VTA format is slightly more precise than Blender's default floating point type, which causes high-detail flexes to become garbled when imported by official BlenderSourceTools. This fork "fixes" the issue by matching inequal, but very similar, flex vertices to the reference mesh at an epsilon of 0.0001 (default). This is the one degree higher than the level of precision used by Crowbar when decompiling models and should be suitable for almost all models. The epsilon can be set to any desired value, however, before QC/SMD import.

### QC eyeball bone generation
Adds an option when importing QCs to generate unweighted bones for all `eyeball` commands. These dummy eye bones can be useful for developing 2D eye tracking techniques when the model is exported for use in other engines or 3D packages.
