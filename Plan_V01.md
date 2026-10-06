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

 Confirm Position 1 is the initial state.
 Confirm one movement command advances to Position 2.
 Confirm the next movement command advances to Position 3.
 Confirm the next movement command returns to Position 1.
 Confirm the target remains visible during the experiment.
 Confirm the application remains responsive.
7. Test Design Before Coding
TC-001: Initial Target Visibility
 Start the application.
 Verify EyeTarget is visible.
 Expected: EyeTarget is visible at Position 1.
TC-002: Move to Position 2
 Start the application.
 Activate the movement command once.
 Verify the target position.
 Expected: EyeTarget is at Position 2.
TC-003: Move to Position 3
 Start the application.
 Move to Position 2.
 Activate the movement command again.
 Verify the target position.
 Expected: EyeTarget is at Position 3.
TC-004: Return to Position 1
 Start the application.
 Move through Position 2.
 Move through Position 3.
 Activate the movement command again.
 Expected: EyeTarget returns to Position 1.
TC-005: Repeated Movement
 Activate movement repeatedly.
 Observe the target.
 Expected: the target follows the defined sequence without unexpected behavior.
TC-006: Restart Behavior
 Stop the application.
 Start the application again.
 Verify the target position.
 Expected: EyeTarget starts at Position 1.
TC-007: Target Visibility During Movement
 Move the target through all positions.
 Observe the target.
 Expected: the target remains visible at each expected position.
TC-008: Console Check
 Run the experiment.
 Open the Unity Console.
 Review errors and warnings.
 Expected: no unexpected runtime errors are generated.
8. Implementation
 Create an EyeTargetController C# script.
 Attach the script to EyeTarget.
 Define the three target positions.
 Define the current target position/state.
 Implement the movement command.
 Implement the position sequence.
 Implement the return to Position 1.
 Add only the logic needed for this mini-project.
 Save the script.
 Return to Unity.
 Allow Unity to compile the script.
 Check the Console for compilation errors.
 Run the application.
 Verify the intended behavior manually.
9. Manual QA Execution
 Execute TC-001.
 Record Pass or Fail.
 Execute TC-002.
 Record Pass or Fail.
 Execute TC-003.
 Record Pass or Fail.
 Execute TC-004.
 Record Pass or Fail.
 Execute TC-005.
 Record Pass or Fail.
 Execute TC-006.
 Record Pass or Fail.
 Execute TC-007.
 Record Pass or Fail.
 Execute TC-008.
 Record Pass or Fail.
 Record any unexpected behavior.
 Capture screenshots where useful.
 Record relevant Console errors if any.
10. Deliberate Defect

Introduce exactly one controlled defect after the correct version works.

BUG-001: Incorrect Third Position
 Change the implementation so Position 3 is intentionally incorrect.
 Do not change the requirement.
 Do not change TC-003.
 Run TC-003.
 Confirm that TC-003 detects the incorrect position.
 Record the failure.
11. Defect Report

Defect ID: BUG-001

Title: EyeTarget moves to an incorrect third position

Environment: Unity / development computer

Steps to Reproduce:

Start MainScene.
Activate EyeTarget movement.
Move to Position 2.
Activate movement again.
Observe the target.

Expected Result:

EyeTarget appears at the predefined Position 3.

Actual Result:

EyeTarget appears at an incorrect location.

Severity: Low

Status: Open

 Create the defect report.
 Link BUG-001 to TC-003.
 Record the expected result.
 Record the actual result.
 Capture evidence if useful.
12. Defect Fix
 Identify the incorrect Position 3 value.
 Correct the implementation.
 Save the script.
 Allow Unity to compile.
 Check the Console.
 Execute TC-003 again.
 Confirm TC-003 passes.
 Change BUG-001 status to Fixed or Ready for Retest.
13. Regression Testing

After fixing BUG-001:

 Execute TC-001 again.
 Execute TC-002 again.
 Execute TC-003 again.
 Execute TC-004 again.
 Execute TC-005 again.
 Execute TC-006 again.
 Execute TC-007 again.
 Execute TC-008 again.
 Confirm the original defect is fixed.
 Confirm no unrelated behavior was broken.
 Close BUG-001 if all relevant tests pass.
14. First Automation Goal

After the manual QA cycle is complete:

 Learn the Unity Test Framework.
 Create a test assembly.
 Create a test for the target's initial position.
 Create a test for movement to Position 2.
 Create a test for movement to Position 3.
 Create a test for the return to Position 1.
 Verify that the automated tests fail when the deliberate defect is introduced.
 Fix the defect.
 Verify that the automated tests pass after the fix.
 Keep the automated tests as regression tests.
15. QA Evidence
 Screenshot the Unity project.
 Screenshot the Hierarchy.
 Screenshot the EyeTarget Inspector.
 Screenshot the running application.
 Save test results.
 Save the defect report.
 Save evidence of the failed test.
 Save evidence of the corrected behavior.
 Document the final test results.
16. Portfolio Connection

Document what this mini-project demonstrates:

 Unity fundamentals.
 C# fundamentals.
 Manual software testing.
 Requirement-based testing.
 Defect management.
 Retesting.
 Regression testing.
 Test automation.
 Evidence-based QA.
Future Connection

This simple cube will eventually become a visual stimulus for the VR eye-tracking project:

Moving EyeTarget
      ↓
Unity interaction
      ↓
VR target
      ↓
Eye-tracking / gaze data
      ↓
Fixation experiment
      ↓
Moving-target experiment
      ↓
Binocular gaze analysis
      ↓
Automated QA
17. Definition of Done

The mini-project is complete when:

 MainScene opens successfully.
 EyeTarget is visible.
 EyeTarget moves through the defined positions.
 The movement sequence works as specified.
 Manual test cases have been executed.
 One deliberate defect has been introduced.
 The defect has been detected.
 The defect has been documented.
 The defect has been fixed.
 Retesting confirms the fix.
 Regression testing passes.
 At least one automated Unity test has been created.
 The project evidence has been documented.
 The project is ready to become the foundation for the VR eye-tracking experiments.
