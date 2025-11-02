# Hero Character Tutorial Project

This Unity 3D project accompanies a YouTube tutorial that walks through a full art-to-engine pipeline: generating a hero concept with AI, creating a 3D character from that concept, rigging and animating the model, and wiring it up inside Unity with gameplay-ready controls (including an attack animation and sword support).

## Pipeline Overview
1. **Ideation with GPT** – Draft the hero concept, personality brief, and visual prompts using GPT for fast iteration on narrative and aesthetic direction.
2. **Concept Art in Midjourney** – Feed the GPT-crafted prompt into Midjourney to produce key art references that guide 3D production.
3. **Image ➜ 3D via 3DAI Studio** – Import a selected Midjourney image into 3DAI Studio to generate an initial character mesh and textures.
4. **Rigging**
   - **AccuRIG** – Auto-rig the generated mesh for quick turnaround and accurate joint placement.
   - **Mixamo** – Optionally refine or retarget animations, and grab additional mocap clips (walk, run, attack, idle, etc.).
5. **Unity Integration**
   - Import the rigged character and animation clips into Unity 2022+.
   - Configure the Animator Controller layers, masks, and parameters.
   - Drop in the SUPER Character Controller package for third-person movement and camera logic.
   - Extend the controller with an attack state, sword interaction, and animation triggers.
6. **Gameplay Polish**
   - Add props (e.g., sword) and configure inverse kinematics or sockets as needed.
   - Tune locomotion / sprint / crouch parameters, animator blending, and camera follow behaviour.
   - Bake lighting or add post-processing for the final presentation.

## Repository Layout
- `Assets/` – Unity assets for the tutorial scene, imported character, animations, and controller scripts.
- `Packages/` – Unity Package Manager manifest and lock files.
- `ProjectSettings/` – Unity project configuration.
- `UserSettings/` – Editor-only preferences; ignored by Git.
- `.gitignore` – Unity-friendly ignore list to keep generated files out of source control.
- `.gitattributes` – Git LFS rules for large binary assets (textures, models, audio, video).

## Attack Animation Integration
The tutorial extends **Character Controller SUPER** (`SUPERCharacterAIO`) with an `Attack` trigger that listens for the left mouse button and fires a masked upper-body animation layer. Key steps covered in the video and implemented in this repo:

- Add the `a_AttackTrigger` parameter in the controller inspector and link it to the Animator.
- Map the attack animation to an override layer with an upper-body mask so locomotion continues uninterrupted.
- Configure the animator transitions (Any State ➜ Attack ➜ Locomotion) with appropriate exit times and durations to play the full clip.

## Requirements
- Unity 2022 LTS (or newer) with the built-in render pipeline.
- Git LFS (`git lfs install`) – required for large binary assets tracked in this project.
- SUPER Character Controller asset (bundled in `Assets/SUPER Character Controller`).

## Quick Start
1. Clone the repository and fetch LFS assets:
   ```bash
   git clone <your-repo-url>
   cd hero_character
   git lfs install
   git lfs pull
   ```
2. Open the project in Unity Hub.
3. Load the main tutorial scene from `Assets/Scenes/` (see YouTube description for the exact path).
4. Enter Play Mode to test movement, camera control, and the attack animation.

## Suggested Tutorial Sections
Use this README as an outline for the YouTube chapters or blog notes:

1. Prompt crafting in GPT (concept, costume, personality).
2. Visual generation in Midjourney; selecting reference frames.
3. 3DAI Studio workflow: importing art, generating mesh, exporting FBX/texture maps.
4. Rigging passes in AccuRIG and Mixamo; downloading animation clips.
5. Unity import pipeline, material setup, Animator construction, controller wiring.
6. Extending SUPER Character Controller: input hooks, attack trigger, sword setup.
7. Final polish, lighting, and recording tips.

## Contributing
Feel free to fork and adapt the workflow—pull requests with improvements to the controller, documentation, or tooling are welcome. Please run through the tutorial steps before submitting edits so the pipeline remains reproducible.

## License
See the root-level license file or video description for usage terms covering generated art, 3D assets, and the SUPER Character Controller package.
