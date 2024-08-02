Unreal Engine 5.3+ Object-Aligned Master Material

To use this asset, simply drag and drop the "ObjectAligned_MM" Folder directly into the "Content" folder of your project. Try to avoid changing the file structure within the folder.

SUMMARY:
  This folder contains a Master Material which performs Tri-Planar mapping which is anchored to the object's coordinates and orientation rather than world coordinates.
  This means the texture mapping will stick to the object rather than slide around as it would with traditional tri-planar mapping.
    - It is similar to Blender's "Object Mapping" method with the object coordinates plugged into a Box-projected texture.
  This material supports Albedo/Color, Metallic, Specular, Roughness, Normal, and Emission textures.

There are also useful material functions provided in the "MaterialFunctions" folder which are used in the Master Material and within each other.
  - MF_3DMappedTexture: Takes 3D coordinates, a Texture Object, Location Offset, and Rotation Offset to box-project a 2D Texture onto the 3D coordinates.
  - MF_3DMappedNormal: Same as the MF_3DMappedTexture Material function but adjusts the Normal map to account for the object's rotation and rotation settings.
  - MF_NormalMapMasking: Creates a mask that separates planes facing all the different axis'. It also creates a parameter under '1_TEXTURE COORDINATES' for the sharpness of this separation.
  - MF_NormalMapRotator: Helps adjust the normal map so that it will properly reflect lighting data regardless of the texture or the object's orientation.
  - MF_ObjectCoordinates: This creates the 3D coordinates that stick to the object for the rest of the Master Material and Material Functions to reference.

The Master Material has many controls designed to minimize or eliminate the need to touch the material graph. It has the following controls for its Material Instances:
  - Slots for all used textures under '0_TEXTURES' group
  - "Use Object's Scale" Toggle to determine whether the texture will stretch with the object if it's scale changes under '1_TEXTURE COORDINATES' group
  - Toggle for whether to use Object Mapping or UV Mapping under '1_TEXTURE COORDINATES' group
  - Tiling settings (tiling mulltiplier, tiling scale offsets, position offsets, rotation offsets) under '1_TEXTURE COORDINATES' group
    - Works for both Object Mapping and UV Mapping
  - Albedo texture/solid-color toggle, brightness, contrast, saturation, and tint
  - Metallic texture/solid toggle, brightness, contrast
  - Roughness texture/solid toggle, brightness, contrast
  - Specular texture/solid toggle, brightness, contrast
  - Normal map toggle and strength adjustment
  - Emission toggle, brightness, contrast, saturation, and tint


This Master Material folder also has a default Material Instance called 'MI_OADefault', as well as default textures to test it out. It is ready-to-use with any texture set or settings.
If you enable a "USE _____ TEXTURE" and haven't chosen a texture for that channel in the '0_TEXTURES' group (displays 'None'), then the material won't render correctly.
A common issue with texturing in Unreal Engine 5 and especially tri-planar mapping of any kind is the normal maps and their interaction with lighting when their mapping is manipulated. These normal map issues are all taken care of; if it does not look correct, remember to verify that the normal map is using NormalDX and not OpenGL. If it is using OpenGL, just go into the texture asset and under 'Advanced', check "Flip Green Channel".

I have not found any resources that help achieve this effect or even show how to, And it is far from straightforward. To make texturing easier in Unreal Engine 5, I decided to try and implement it myself. Now that this tool exists, texturing assets in Unreal Engine 5 is made a lot easier and more flexible, as it does not rely on objects being UV-Mapped. Any 3D model, regardless of UV mapping, can quickly have a texture applied to it with far more control and consistency than other texturing methods. It does not replace traditional texturing and UV-mapping, but it is a necessary tool to speed up texturing workflows and provide more options in the creation process. I've put a lot of hard work into making something that I would frequently use, so I hope it helps someone else as well. Thank you!
