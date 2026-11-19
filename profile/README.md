# usdCharacter — digital characters in OpenUSD

![A rig evaluated live by RigExec in usdview](https://raw.githubusercontent.com/usdCharacter/usdRig/main/docs/gifs/two_bone_ik.gif)

**usdCharacter is an open-source character technology stack for building,
rigging, and animating digital characters entirely inside
[OpenUSD](https://openusd.org/)** — the open scene-description standard from
Pixar. In our stack a character is one living USD scene: mesh, skeleton,
controls, constraints, weights, deformers and animation all travel together in
the scene graph, evaluated live and rendered through Hydra. No proprietary rig
formats, no lossy FBX round-trips, no rig that dies when it leaves its DCC.

The flagship engine, **[RigExec](https://github.com/usdCharacter/usdRig)**,
adds the rigging layer OpenUSD never had: OpenUSD describes the scene,
[OpenExec](https://openusd.org/release/intro_to_openexec.html) computes, and
RigExec rigs the character.

## The character workflow, end to end

1. **Build a character** — assemble a body from USD components in the
   [character asset library](https://github.com/usdCharacter/usdRig_assets)
   and fit it with the compose-character workflow
   ([component selection, fit layers, bindings](https://github.com/usdCharacter/usdRig/tree/main/asset_lib)).
2. **Rig it live** — controls, FK, two-bone and chain IK, spline IK, twist,
   constraints, and ordered deformation "movers": skinning, blend shapes,
   lattices, smoothing, Delta Mush. The
   [full biped character example](https://github.com/usdCharacter/usdRig/tree/main/examples/biped)
   is a rig you can open and drive in `usdview`.
3. **Animate it** — animator tools in the viewport: TouchPose, the marking
   menu, pickers, curves and layers, plus a graph editor for the rig itself.
   Poses bake to a compact `.rigexec` binary with an independent CPU check.
4. **Ship the character** — the same baked rig plays in
   [Godot](https://github.com/usdCharacter/usdRig_godot),
   [Unreal](https://github.com/usdCharacter/usdRig_unreal) (through Control Rig
   and Sequencer), [Maya](https://github.com/usdCharacter/usdRig_maya) and
   [Blender](https://github.com/usdCharacter/usdRig_blender) using a USD-free
   standalone runtime.

## The stack

| Project | Character role |
|---|---|
| [usdRig](https://github.com/usdCharacter/usdRig) | The character-rigging engine (RigExec) — rigging, skinning, deformation, `.rigexec` bake — C++ |
| [usdRig_assets](https://github.com/usdCharacter/usdRig_assets) | Character and body-component library in USD |
| [usdRig_movers](https://github.com/usdCharacter/usdRig_movers) | Extra deformation movers (curvenet) for character skin and cloth |
| [usdRig_godot](https://github.com/usdCharacter/usdRig_godot) | Play baked characters in Godot 4.7+ with no USD install |
| [usdRig_unreal](https://github.com/usdCharacter/usdRig_unreal) | Re-pose baked characters in Unreal via Control Rig / Sequencer |
| [usdRig_maya](https://github.com/usdCharacter/usdRig_maya) | Animate baked characters in Maya; read OpenUSD character files |
| [usdRig_blender](https://github.com/usdCharacter/usdRig_blender) | Open Blender `.blend` characters as RigExec rigs |
| [usdGen](https://github.com/usdCharacter/usdGen) | Geometry instancing for the worlds characters live in |
| [usdGen_tools](https://github.com/usdCharacter/usdGen_tools) | `usdview` plug-ins and CLI utilities for USD workflows |
| usdRig_ios / usdRig_android | Drive character rigs on iPad and Android |

## Try a character in minutes

- Download a **self-contained release bundle** (Windows, macOS, Linux — no
  OpenUSD, Python, or Qt needed) from the
  [latest usdRig release](https://github.com/usdCharacter/usdRig/releases/latest)
  and open the bundled example rigs.
- Learn the rigging model in the
  [usdRig documentation](https://usdcharacter.github.io/usdRig/) — node
  reference, tutorials, and animator tools.
- Start small: [the smallest rig](https://github.com/usdCharacter/usdRig/blob/main/examples/rigexec_flat.usda),
  the [animated arm](https://github.com/usdCharacter/usdRig/blob/main/examples/ArmShotAnim.usda),
  then the [biped](https://github.com/usdCharacter/usdRig/tree/main/examples/biped).

## Why rig characters inside OpenUSD?

Character pipelines break at interchange: every DCC locks rigs in its own
format, and skeletons exported as
[UsdSkel](https://openusd.org/release/api/usd_skel_page_front.html) lose the
controls and deformers that made them poseable. OpenUSD — adopted by Pixar,
NVIDIA, Autodesk, SideFX, Epic and the
[Alliance for OpenUSD](https://aousd.org/) — had no rigging system.
usdCharacter supplies one: characters stay animatable as they move between
tools, engines, and time.

## Open source and community

Project-authored code and documentation in the public repos are
**MIT licensed** (bundled third-party components keep their own terms).
We are active in the OpenUSD community:

- [Alliance for OpenUSD forum](https://forum.aousd.org/) — rigging in USD threads
- [awesome-openusd](https://github.com/matiascodesal/awesome-openusd) — the community resource list
- [ASWF USD Working Group](https://lf-aswf.atlassian.net/wiki/spaces/WGUSD) — upstream standardization

Want to build characters with us? See
[CONTRIBUTING.md](https://github.com/usdCharacter/usdRig/blob/main/CONTRIBUTING.md)
and issues labeled [`good first issue`](https://github.com/usdCharacter/usdRig/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22).
