# VR Automation Testing 3-Month Learning Plan

**Goal:** Go from zero to being able to design and run automated test suites for VR applications:
- [ ] Functional
- [ ] UI/interaction
- [ ] Performance, and 
- [ ] Regression testing

across engine-level (Unity/Unreal), device-level (Android/Quest), and browser-level (WebXR) targets.

**Format:** 30–45 min on weekdays (reminder set for 11:00 AM, Mon–Fri). Weekends are optional catch-up/reading days - no new material introduced then.

**Hardware note:** VR headset is not required for Months 1–2. Simulators (Unity XR Device Simulator, WebXR browser emulators) cover almost everything. A real headset becomes genuinely useful in Month 3 for on-device validation. Even without a headset, the capstone can be fully completed in WebXR + Unity Editor simulation.

---

## Free Platforms & Tools You'll Use (all Free)

|  | Category | Tool | Notes |
|---|---|---|---|
| ⛔ | Game engine | **Unity Personal** | Free tier, includes XR Interaction Toolkit |
| ⛔ | Game engine (alt.) | **Godot 4 + Godot XR Tools** | Fully open-source alternative if avoiding Unity's ToS |
| ⛔ | Game engine (alt.) | **Unreal Engine** | Free, VR template included |
| ⛔ | No-headset VR testing | **Unity XR Device Simulator** | Simulates headset + controllers with mouse/keyboard in-editor |
| ⛔ | WebXR framework | **A-Frame** | Open-source, runs in any browser, no install |
| ⛔ | WebXR emulator | **Immersive Web Emulator** (Chrome/Edge extension, by Meta) | Simulates a headset in devtools - no hardware needed |
| ☑️ | Web automation | **Playwright** | Automates browser-based WebXR/A-Frame scenes |
| ☑️ | Web automation (alt.) | **Selenium** | Web-automation |
| ☑️ | Mobile/device automation | **Appium** | Drives Android-based headsets (Quest runs Android) via UIAutomator2/Espresso drivers |
| ⛔ | Image-based automation | **Airtest Project** (NetEase) | Screenshot/image-recognition-based automation - works even when there's no accessible UI tree, common in VR |
| ⛔ | Conformance/standards testing | **OpenXR SDK + Conformance Test Suite** (Khronos, free, open-source) | Industry-standard XR API test suite |
| ⛔ | Sideloading/device testing | **SideQuest** (free) | Install/test unsigned APKs on Quest hardware |
| ⛔ | Device diagnostics | **Meta Quest Developer Hub (MQDH)** (free, needs Meta dev account, no hardware) | Logs, performance capture, device management |
| ⛔ | CI/CD | **GitHub Actions** (free tier: 2,000 min/month private, unlimited public repos) | Automate test runs on push |
| ⛔ | 3D asset creation | **Blender** (free) | Build simple test scenes/props if needed |
| ☑️ | Version control | **Git + GitHub** (free) | Portfolio hosting for your capstone |

---

## Month 1 - Foundations (Weeks 1–4)

**Theme:** Understand VR fundamentals, testing fundamentals, and get comfortable building/running a basic VR scene without a headset.

### Week 1: Testing fundamentals + VR concepts
- Automation testing fundamentals refresher: test pyramid, functional vs. non-functional testing, flaky tests, test data management (skip as QA background)
- VR-specific concepts: 6DOF vs 3DOF, degrees of freedom, locomotion types (teleport, smooth), UI raycasting/pointer interaction, comfort/motion sickness as a *testable* quality attribute
- **Task:** Install Unity Personal + XR Interaction Toolkit. Open a sample VR scene and interact with it using the **XR Device Simulator** (no headset).

### Week 2: WebXR basics (fastest path to "something running")
- Learn A-Frame basics: `<a-scene>`, entities, components, the DOM-based structure
- Install the **Immersive Web Emulator** browser extension
- **Task:** Build a tiny A-Frame scene (a box you can click to change color, a simple menu with 2 buttons) and interact with it via the emulator.

### Week 3: First automated test - Playwright on WebXR
- Learn Playwright basics: selectors, `click()`, `expect()`, headless vs headed runs
- **Task:** Write a Playwright script that loads your Week 2 A-Frame scene and asserts that clicking a button changes an element's attribute/color. This is your first real "VR automation test," even though it's browser-based.
- **Why this matters:** A-Frame exposes standard DOM elements, so this proves the core insight - a lot of VR testing is "normal web/app automation" pointed at unusual content.

### Week 4: Unity Test Framework basics
- Learn Unity Test Framework (UTF): Edit Mode vs Play Mode tests, `[Test]` and `[UnityTest]` attributes, assertions
- **Task:** Add 2–3 Play Mode tests to your Unity scene from Week 1 - e.g., "when the XR simulator triggers a grab event, the object's parent becomes the hand," or "when player enters trigger zone, a UI panel activates." Run them via the XR Device Simulator, no headset.

**Month 1 milestone:** You can build a minimal VR scene (Unity or WebXR) and write at least one automated test against it in two different toolchains.

---

## Month 2 - Core Automation Skills (Weeks 5–8)

**Theme:** Learn the tools that are actually used for VR-specific automation: device-level automation, image-based automation, and structured interaction testing.

### Week 5: Appium fundamentals
- Set up Appium + Appium Inspector, connect to an Android emulator (standard Android emulator is fine to start - you don't need Quest hardware yet)
- Learn UIAutomator2 driver basics: locating elements, tap/swipe gestures, launching an app
- **Task:** Automate installing and launching a simple Android app (any free APK) via Appium as a dry run before pointing this at VR-specific content.

### Week 6: Appium against a VR/game context + Airtest intro
- VR apps often don't expose a normal accessibility tree (Unity/Unreal render to a single surface), so pure UIAutomator2 element-finding often fails - this is the key limitation you need to *feel* firsthand
- Install **Airtest** and learn its image-recognition-based approach: `touch(Template("button.png"))` instead of finding elements by ID
- **Task:** Use Airtest to automate a click sequence in your Week 4 Unity scene (built to a PC/Android build) purely by matching screenshots - this is the workaround for opaque game-engine UIs.

### Week 7: Test design for VR-specific failure modes
- Learn to write test cases for VR-specific risks: object interaction (grab/release/throw), locomotion (teleport lands in valid area, doesn't clip through walls), UI reachability (buttons not out of raycast range), performance-triggered issues (dropped frames during interaction)
- **Task:** Write a structured test plan (just a markdown/spreadsheet doc) covering 15–20 test cases for a sample VR scene, categorized as functional / interaction / performance / comfort

### Week 8: CI integration
- Learn GitHub Actions basics: workflows, triggers, running a headless test job
- **Task:** Push your Unity project + UTF tests to GitHub and set up a GitHub Actions workflow that runs your Play Mode tests on every push (Unity has an official `game-ci/unity-test-runner` action, free for open-source/personal repos)

**Month 2 milestone:** You've used 3 different automation approaches (Playwright/web, Appium/device, Airtest/image-based) and understand *when* to reach for each. You have a CI pipeline running tests automatically.

---

## Month 3 - Integration, Performance, and Capstone (Weeks 9–12)

**Theme:** Bring it together into a portfolio-ready project; add performance testing; get on real hardware if possible.

### Week 9: Performance testing
- Learn what to measure in VR specifically: frame rate (must stay high - drops cause motion sickness, not just "jank"), frame time consistency, GPU/CPU usage
- Free tools: **Unity Profiler** (built-in), **OVR Metrics Tool** (free, Meta, needs a Quest device - skip if no hardware and note it as a gap to fill later)
- **Task:** Profile your Unity scene under simulated load (spawn many objects) and record baseline frame-time metrics; write a simple pass/fail threshold check

### Week 10: OpenXR conformance + standards awareness
- Skim the **OpenXR Conformance Test Suite** docs to understand how the industry tests XR runtimes at the API level - you won't run the full suite, but understanding it is valuable for interviews/context
- **Task:** Read through 2–3 conformance test cases and summarize in your own words what they check and why

### Week 11: Capstone project - build
- Pick a small open-source VR/WebXR project (A-Frame's official examples repo, or a Unity XR sample) as your test target
- **Task:** Write a test plan + automated test suite covering:
  - 5+ Playwright tests (if WebXR) or UTF tests (if Unity) for functional/interaction behavior
  - 2–3 Airtest-based visual regression checks
  - 1 performance check with a defined threshold
  - A GitHub Actions workflow running it all on push

### Week 12: Capstone project - document & polish
- Write up a short test strategy doc (1–2 pages): scope, tools chosen and why, coverage, known gaps
- Push everything to a public GitHub repo - this becomes your portfolio piece
- **If you have headset access by now:** sideload your test build via SideQuest and manually validate 2–3 of your automated checks actually match real-device behavior - document any discrepancies (simulators are never 100% accurate)

**Month 3 milestone:** A public, documented, CI-integrated VR test automation project you can show in an interview or add to a resume.

---

## Suggested Weekly Rhythm
- **Mon–Thu:** New concept + hands-on task (the 11 AM slot)
- **Fri:** Review the week, clean up code/tests, write a 3–5 sentence log of what worked/didn't (this log becomes capstone documentation material later)
- **Weekend (optional):** Catch-up only, no new material

## If You Fall Behind
The plan has intentional slack: Month 1 tools carry through the whole plan, so skipping a day never blocks the next day's task. If a week clearly needs more time, compress Week 10 (the OpenXR reading week) first - it's the most skippable without losing hands-on skill.
