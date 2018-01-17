---
title: AssetBundle Dependencies
---

NOTE: Some of the mechanisms discussed here are not officially documented by Unity. 
They can change at any time in future Unity builds. At the meantime, all researches 
are done with Unity 5.x.

Unity allows developers to build selected assets into asset bundles so that they can
be separate from the main game and streamed to device dynamically at runtime. An asset
bundle is an archive format which can contain one or more serialized Unity objects.
Game developer can choose to build one bundle with many assets or many bundles each of
which contains one or more assets. 

It's important for game developers to understand what will be included in an asset bundle.
Knowing it will help developers properly assign assets to bundles and make efficient use of 
bandwidth and memory at runtime. Unity has made some clarification in the documentation
below.

<https://docs.unity3d.com/Manual/AssetBundles-Dependencies.html>

Sometimes certain common dependencies such as a material can be referenced by many other 
assets in bundles. To avoid each asset bundle to contain full copies of such shared dependencies,
developers will want to assign such dependencies to asset bundles as well.

Consider following assets from Low-Poly Park (available in [Unity Asset Store](https://www.assetstore.unity3d.com/en/#!/content/61922)):

```
  Assets
     |---Materials
     |     |---Illumin.mat
     |     \---Park_Material.mat (*)
     |
     |---Models
     |     |---NaturalPark.fbx
     |     |---NaturalPark Hovels.fbx
     |     \---NaturalParkAutumn.fbx
     |
     |---Prefabs
     |     |---Bench.prefab
     |     |---BenchTable.prefab
     |     |---Boat.prefab
     |     |---Bridge.prefab
     |     |---Bush.prefab
     |     \---...
     |
     \---Textures
           |---Park_Specular.tga
           \---Park_Texture.tga
```

