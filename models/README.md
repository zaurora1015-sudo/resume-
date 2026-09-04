# Blender / GLB delivery contract

Active asset: `four-traits-world.glb`.

The current export contains five orthographic cameras:

- `WEB_CAMERA_Main`
- `WEB_CAMERA_Reception`
- `WEB_CAMERA_Green`
- `WEB_CAMERA_Blue`
- `WEB_CAMERA_Pottery`

The web app keeps model ownership separate from interaction ownership. The GLB
is parented under `modelRoot`; subtle pointer movement is applied to its parent
`motionRig`. Room hotspot anchors live in `src/scene/FourTraitsWorld.ts`, so a
future model replacement does not require editing mesh data.

Recommended export pipeline:

- binary glTF (`.glb`), +Y up;
- export the five cameras;
- WebP images, quality about 80;
- `EXT_meshopt_compression` enabled;
- retain UVs and normals, omit tangents and unused vertex colors;
- keep PBR surfaces matte and retain authored emission on visible lamp parts;
- use a new versioned model URL when deploying a replacement, so immutable
  browser/CDN caching cannot serve an older scene.

The adjacent manifest records the source, cameras, lights, tone settings, and
user-edited frosted-panel integrity check.
