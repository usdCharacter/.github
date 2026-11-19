# usdCharacter — character rigging and hair and fur grooming in OpenUSD

usdCharacter is a collection of open-source experiments in [OpenUSD](https://openusd.org/)
character rigging and grooming for artists and AI agents. With [usdRig](https://github.com/usdCharacter/usdRig)
and [usdGen](https://github.com/usdCharacter/usdGen), artists can author and edit rigs
and grooms interactively in `usdview` through plugins. Agents can work with the same
USD scenes using the projects’ schemas and examples.

## Try a rig or a groom

- **usdRig · [Build a rolling ball rig](https://usdcharacter.github.io/usdRig/concepts/tutorial-rolling-ball/).**
  Start with an unrigged ball. In Noodles, the node editor in `usdview`, connect a
  control so that dragging it across the floor makes the ball roll. Follow the
  3:13 video or use the illustrated steps and starter files. No scripting required.
- **usdGen · [Shape a hair groom with Pomade](https://github.com/usdCharacter/usdGen/blob/main/docs/pomade-tool.md).**
  Draw a region on the scalp, shape its guides in `usdview`, and save the groom as USD.
  Explore the [ponytail example](https://github.com/usdCharacter/usdGen/blob/main/examples/pomade-ponytail.usda)
  to see how a groom is described on the stage.

## Rigging schemas and authoring tools

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
   between IK and FK, edit animation curves, and see the pose change in `usdview`.
4. **Bring characters into other tools.** Bake supported rigs for playback in
   other applications. RigExec is the evaluator behind the live viewport and
   the `.rigexec` export; the USD stage remains the authoring source.

## Run usdRig locally

Download the [latest usdRig release](https://github.com/usdCharacter/usdRig/releases/latest)
for Windows x64, macOS (Apple Silicon), or Linux x86-64. To pose the full character,
clone the [usdRig repository](https://github.com/usdCharacter/usdRig) and open
[`examples/biped/Biped_stack.usda`](https://github.com/usdCharacter/usdRig/blob/main/examples/biped/Biped_stack.usda)
in `usdview`. Open the file from the checkout rather than downloading it alone:
it loads the body and face from neighboring layers. Select a control in the character
picker and move it in the viewport to try your first pose. For more, see the
[usdRig documentation](https://usdcharacter.github.io/usdRig/).

## Public projects

| Project | What it adds |
|---|---|
| [usdRig](https://github.com/usdCharacter/usdRig) | Character-rigging schemas, authoring APIs, and interactive rigging and animation plugins for `usdview` |
| [usdGen](https://github.com/usdCharacter/usdGen) | Hair and fur grooming schemas and interactive grooming with Pomade in `usdview` |
| [usdRig_godot](https://github.com/usdCharacter/usdRig_godot) | Play baked characters in Godot without an OpenUSD installation |
| [usdRig_unreal](https://github.com/usdCharacter/usdRig_unreal) | Re-pose baked characters in Unreal Engine via Control Rig and Sequencer |
| [usdRig_maya](https://github.com/usdCharacter/usdRig_maya) | Animate baked characters in Maya; read Maya ASCII through an OpenUSD file-format plugin |
| [usdRig_blender](https://github.com/usdCharacter/usdRig_blender) | Read Blender `.blend` files as OpenUSD rigs for usdRig |

## UsdSkel vs. usdRig: transporting motion and authoring rigs

**[UsdSkel](https://openusd.org/release/api/usd_skel_page_front.html) is designed for compact transport.**
Its standard OpenUSD schemas carry a skeleton, skinning bindings, and animation
between tools. A walk cycle, for example, can travel as joint transforms without
requiring the receiving tool to recreate the animator’s controls.

**[usdRig](https://github.com/usdCharacter/usdRig) is designed for robust rig authoring.**
Its project-defined OpenUSD schemas describe the controls, constraints, solvers,
and deformers that produce a pose. To change how a knee bends when an animator
moves a foot control, edit the rig in `usdview` using the usdRig plugins.

[usdRig](https://github.com/usdCharacter/usdRig) is experimental and MIT-licensed;
bundled and derived third-party material retains its own terms. See the
[contributor guide](https://github.com/usdCharacter/usdRig/blob/main/CONTRIBUTING.md)
to get involved, or visit the [Alliance for OpenUSD forum](https://forum.aousd.org/)
for broader discussion about character workflows in USD.
