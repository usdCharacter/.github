# usdCharacter — digital characters in OpenUSD

**usdCharacter is an open-source technology stack for building, rigging, and
animating digital characters in [OpenUSD](https://openusd.org/).** Its flagship
project, [usdRig](https://github.com/usdCharacter/usdRig), brings together
**OpenUSD character-rigging schemas**, **interactive and programmatic authoring
tools**, and **full Hydra 2 integration for live character display**.

## Rigging schemas, authoring tools, and Hydra 2

- **Character-rigging schemas.** Describe controls, joints, FK and IK solvers,
  constraints, weight fields, and ordered deformations as typed USD prims,
  attributes, and relationships. The rig can be assembled from reusable
  components and edited in USD layers alongside the character's geometry and
  animation. Browse the [schema definitions](https://github.com/usdCharacter/usdRig/blob/main/libs/rigExecSchema/schema.usda)
  and [node reference](https://usdcharacter.github.io/usdRig/reference/).
- **Rig authoring and animation tools.** Build and connect rig components with
  the [C++ and Python authoring APIs](https://github.com/usdCharacter/usdRig/tree/main/libs/rigExecAuthoring).
  In `usdview`, use viewport gizmos, character pickers, TouchPose, a marking
  menu, curve editing, and layer inspection to pose characters and edit
  animation. See the [animator tools](https://usdcharacter.github.io/usdRig/tools/)
  and [Python rig examples](https://github.com/usdCharacter/usdRig/tree/main/examples/python).
- **Full Hydra 2 integration.** Filtering scene indices publish evaluated
  transforms, deformed mesh points, normals, and bounds as standard Hydra data.
  Poses and deformations update live in `usdview` without writing evaluated
  results back to the authored USD layers. See the
  [Hydra 2 scene-index implementation](https://github.com/usdCharacter/usdRig/blob/main/libs/rigExecImaging/sceneIndices.h).

## The character workflow, end to end

1. **Assemble and fit.** Start with the
   [USD body components bundled with usdRig](https://github.com/usdCharacter/usdRig/tree/main/asset_lib/components)
   and adapt them to your character with the
   [character assembly workflow](https://github.com/usdCharacter/usdRig/blob/main/skills/compose-character/SKILL.md).
2. **Rig and deform.** Connect controls, solvers, constraints, and skinning or
   blend shape operations. The
   [biped example](https://github.com/usdCharacter/usdRig/tree/main/examples/biped)
   shows how the pieces fit together in a complete character.
3. **Pose and animate.** Pick controls directly on the character, switch
   between IK and FK, edit animation curves, and see the result in the Hydra
   viewport as you work.
4. **Bring characters into other tools.** Bake supported rigs for playback in
   other applications. RigExec is the evaluator behind the live viewport and
   the `.rigexec` export; the USD stage remains the authoring source.

## Try it

Download the [latest usdRig release](https://github.com/usdCharacter/usdRig/releases/latest)
for Windows x64, macOS (Apple Silicon), or Linux x86-64. Open the bundled
[animated arm](https://github.com/usdCharacter/usdRig/blob/main/examples/ArmShotAnim.usda)
in `usdview` to try live posing and playback. The
[usdRig documentation](https://usdcharacter.github.io/usdRig/) takes you from
that first rig to composing and authoring a character of your own.

## Public projects

| Project | What it adds |
|---|---|
| [usdRig](https://github.com/usdCharacter/usdRig) | Character-rigging schemas, authoring and animation tools, Hydra 2 imaging, and rig evaluation |
| [usdRig_godot](https://github.com/usdCharacter/usdRig_godot) | Play baked characters in Godot without an OpenUSD installation |
| [usdRig_unreal](https://github.com/usdCharacter/usdRig_unreal) | Re-pose baked characters in Unreal Engine via Control Rig and Sequencer |
| [usdRig_maya](https://github.com/usdCharacter/usdRig_maya) | Animate baked characters in Maya; read Maya ASCII through an OpenUSD file-format plugin |
| [usdRig_blender](https://github.com/usdCharacter/usdRig_blender) | Read Blender `.blend` files as OpenUSD rigs for usdRig |
| [usdGen](https://github.com/usdCharacter/usdGen) | OpenUSD geometry instancing for the environments characters inhabit |

## How this fits into OpenUSD

[UsdSkel](https://openusd.org/release/api/usd_skel_page_front.html) describes
skeletons, skinning bindings, and skeletal animation. usdRig's project-defined
schemas describe a different part of the character: the editable controls,
solvers, and deformation graph used to create a pose. They are implemented as
OpenUSD extensions, not presented as standard OpenUSD schemas.

[usdRig](https://github.com/usdCharacter/usdRig) is experimental and MIT-licensed;
bundled and derived third-party material retains its own terms. See the
[contributor guide](https://github.com/usdCharacter/usdRig/blob/main/CONTRIBUTING.md)
to get involved, or visit the [Alliance for OpenUSD forum](https://forum.aousd.org/)
for broader discussion about character workflows in USD.
