# usdCharacter — open-source character technology stack for OpenUSD

![usdRig two-bone IK evaluated live](https://raw.githubusercontent.com/usdCharacter/usdRig/main/docs/gifs/two_bone_ik.gif)

**usdCharacter is an open-source character technology stack built on
[OpenUSD](https://openusd.org/)**, the open scene-description standard from
Pixar. Our tools put *character rigging, animation, and deformation* directly
inside USD scenes: rigs with controls, constraints, solvers, skinning, blend
shapes, and deformers are authored in OpenUSD, evaluated live, and rendered
through Hydra — no proprietary rig format, no lossy FBX round-trips.

The flagship project is **[usdRig](https://github.com/usdCharacter/usdRig)**,
whose engine **RigExec** is the rigging layer on top of OpenUSD and
[OpenExec](https://openusd.org/release/intro_to_openexec.html): OpenUSD
describes the scene, OpenExec computes, and RigExec rigs.

## The stack

| Project | What it does |
|---|---|
| [usdRig](https://github.com/usdCharacter/usdRig) | OpenUSD character-rigging engine (RigExec): FK/IK, constraints, movers, skinning, Delta Mush, `.rigexec` export — C++ |
| [usdRig_godot](https://github.com/usdCharacter/usdRig_godot) | Godot 4.7+ plugin that plays baked `.rigexec` rigs with no USD install |
| [usdRig_unreal](https://github.com/usdCharacter/usdRig_unreal) | Unreal Engine plugin re-posing baked rigs through Control Rig and Sequencer |
| [usdRig_maya](https://github.com/usdCharacter/usdRig_maya) | Maya plug-in plus a read-only OpenUSD file format for Maya ASCII |
| [usdRig_blender](https://github.com/usdCharacter/usdRig_blender) | Read-only OpenUSD file format that opens Blender `.blend` files as RigExec rigs |
| [usdRig_assets](https://github.com/usdCharacter/usdRig_assets) | Character and component asset library in USD |
| [usdRig_movers](https://github.com/usdCharacter/usdRig_movers) | External deformation movers (curvenet) built on the public mover-plugin API |
| [usdGen](https://github.com/usdCharacter/usdGen) | OpenUSD-based geometry instancing for dense character environments |
| [usdGen_tools](https://github.com/usdCharacter/usdGen_tools) | `usdview` plug-ins and CLI utilities for USD geometry workflows |
| usdRig_ios / usdRig_android | `usdview` with RigExec tools on iPad and Android (Storm over HgiMetal/HgiVulkan) |

## Getting started

- **Try it in minutes:** download a self-contained **usdRig release bundle**
  (Windows, macOS, Linux — no OpenUSD, Python, or Qt required) from
  [the latest release](https://github.com/usdCharacter/usdRig/releases/latest).
- **Learn the rigging model:** [usdRig documentation](https://usdcharacter.github.io/usdRig/)
  — node reference, tutorials, and animator tools (picker, marking menu, TouchPose).
- **Author rigs in USD:** start from the [example rigs](https://github.com/usdCharacter/usdRig/tree/main/examples),
  from a minimal rig to a full biped character.
- **Play rigs in game engines:** the Godot and Unreal plugins run the USD-free
  standalone runtime — the same operation graph the viewport evaluates.

## Why rig inside OpenUSD?

Character pipelines are usually locked in per-DCC rig formats that do not
survive interchange. OpenUSD is the industry-standard scene format
(adopted by Pixar, NVIDIA, Autodesk, SideFX, Epic, and the
[Alliance for OpenUSD](https://aousd.org/)), but until now it had no rigging
system: `UsdSkel` stores skeletons and skin binds, and OpenExec provides a
computation engine — neither evaluates a live control rig. usdCharacter
closes that gap: rig data stays in the scene graph, travels between tools,
and stays animatable.

## Open source and community

Everything project-authored in the public repos is **MIT licensed** (bundled
third-party components keep their own terms). usdCharacter participates in
the OpenUSD community:

- [Alliance for OpenUSD forum](https://forum.aousd.org/) — discussion of rigging in USD
- [awesome-openusd](https://github.com/matiascodesal/awesome-openusd) — the community resource list
- [ASWF USD Working Group](https://lf-aswf.atlassian.net/wiki/spaces/WGUSD) — upstream standardization

Contributions are welcome — see
[CONTRIBUTING.md](https://github.com/usdCharacter/usdRig/blob/main/CONTRIBUTING.md)
and issues labeled [`good first issue`](https://github.com/usdCharacter/usdRig/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22).
