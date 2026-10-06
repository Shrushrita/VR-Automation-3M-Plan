# Mini QA Challenge: Moving EyeTarget

## 1. Challenge Overview

- [ ] Create a small Unity 3D application called **Moving EyeTarget**.
- [ ] Use a cube named `EyeTarget` as the visual target.
- [ ] Make the target move between three predefined positions.
- [ ] Test the feature manually before automating it.
- [ ] Introduce one deliberate defect.
- [ ] Confirm that the test detects the defect.
- [ ] Fix the defect.
- [ ] Retest the failed case.
- [ ] Run regression tests to confirm that the fix did not break existing behavior.

## 2. Learning Objectives

- [ ] Understand Unity scenes and GameObjects.
- [ ] Practice using the Hierarchy and Inspector.
- [ ] Create a simple C# script.
- [ ] Understand how a script controls a GameObject.
- [ ] Practice writing a requirement before implementation.
- [ ] Create manual QA test cases.
- [ ] Execute tests and record results.
- [ ] Create a basic defect report.
- [ ] Practice defect retesting and regression testing.
- [ ] Prepare for later Unity automated testing.

## 3. Project Setup

- [ ] Open Unity Hub.
- [ ] Create or open the project `VR-Eye-Tracking-Lab`.
- [ ] Confirm the project opens without errors.
- [ ] Create or open `Assets/Scenes`.
- [ ] Create a scene named `MainScene`.
- [ ] Save the scene.
- [ ] Confirm the Hierarchy contains the expected basic objects.
- [ ] Confirm the Console has no unexpected errors.

## 4. Scene Setup

- [ ] Keep the `Main Camera`.
- [ ] Keep a light source such as `Directional Light`.
- [ ] Create a 3D Cube.
- [ ] Rename the cube `EyeTarget`.
- [ ] Position `EyeTarget` so it is visible from the camera.
- [ ] Confirm the target appears in Game view.
- [ ] Save the scene.

## 5. Requirement

### REQ-001: EyeTarget Movement

> When the user activates the movement command, `EyeTarget` shall move from its current position to the next predefined target position.

- [ ] Review the requirement before coding.
- [ ] Define Position 1 as the starting position.
- [ ] Define Position 2 as the second position.
- [ ] Define Position 3 as the third position.
- [ ] Define the movement command.
- [ ] Define what should happen after Position 3.
- [ ] Decide whether the target should return to Position 1.
- [ ] Document the expected positions clearly.

## 6. Initial Expected Behavior

Example:

```text
Position 1 → Position 2 → Position 3 → Position 1
