# Temple Mudslide — delivery guide

This package documents a successful Temple Ruins mudslide demonstration in Tomb Raider III Remastered. Read this guide before the historical research chapters. The current route uses **slot 1 / 3089 → save the upper pose in slot 4 → load slot 3 / 3095 → reload the new slot 4 save → finish in room 148**.

## What is included

| Artifact | Purpose |
| --- | --- |
| MudSlide-Part1-Prep.mp4 | Approximately 41 seconds: the local approach to the new slope and preparation of the slot 3 seed. |
| MudSlide-Part2-Exec.mp4 | Approximately 2 minutes 42 seconds: the automated climb, upper save, slope-seed load and successful crossing. |
| Temple-Mudslide-Proof.7z | Complete sanitized proof collection: final chapters, historical research notes, textual measurements and journals, figures, cited screenshots, research scripts and classic source references. Includes FINAL_PROOF.html and the manual walkthrough. |
| FINAL_PROOF.html | One large offline proof page with chapter anchors, directly embedded figures and all 20 buffer-gallery images. |
| Temple-Mudslide-Execution.7z | Portable CE table and Lua bridge, Python replay and its dependencies, setup helper, menu recognition fixtures and execution instructions. |
| START_HERE.html / GUIDE.md | This explanation and tutorial, in browser-readable and plain Markdown forms. |
| MANUAL_WALKTHROUGH.html / MANUAL_WALKTHROUGH.md | Separate hands-on walkthrough: head-nod counting, menu buffers, the height drop after the first 15 buffers, passport saving and the slope-load finish. |
| SHA256SUMS.txt | Integrity hashes of the delivered files. |

The final chapters retain historical comparisons and claims. Earlier chapters refer to seed 3068 or 3088, older upper saves, an uncompleted input-only approach, or an unverified video. Those are historical statements, superseded for the current demonstration by the current-result section of [FINAL_PROOF.html](FINAL_PROOF.html) and this guide. Some early experiments explicitly used position writes; they are not evidence of an input-only route. The current recorded replay uses game input with read-only telemetry to choose pauses. The full proof ZIP includes the sanitized supporting journals, scripts, historical research archive and classic source reference tree.

## Current result and its limits

The final successful source journal is `tomb-raider-analysis/temple-mudslide/data/manual/manual-1790121761988164400.json` inside the proof archive. It reports approximately 155.87 seconds of automation, upper save **3097**, final **room 148**, and preservation of the protected saves. The execution video is longer because it includes menu and end holds. Video timestamps below refer to the delivered media, not to journal wall-clock time.

The new seed is in **room 35**. It begins on sector **7/15** and slides into **8/15**; both measured sectors have X/Z tilt **−3/0**. Sector 8/15 is the slope identified during preparation. The script waits until the character is sliding in the measured range before loading the upper save. Room numbers and sector coordinates follow the analysis/trview convention.

Part 1 shows a local ledge climb and approach to this slope. It does not show a complete route from level spawn, and it has no input overlay. Therefore the recording alone cannot certify every key press or a complete no-jump run. The old seed **3088** was made using a jump and is retained only as a protected historical save; it is not loaded by the current replay. The new seed **3095** is the player's replacement after the no-jump requirement was raised.

The explanation based on cached collision tilt is supported by the measurements and comparison with classic engine source. It is an implementation hypothesis for Remastered, not a claim that its proprietary source has been inspected. The demonstrated outcome and the inferred cause are separate claims.

## Video 1 — preparation, approximately 00:41

Times are approximate and rounded to the nearest useful action boundary.

| Video time | What happens / why it matters |
| --- | --- |
| 00:00–00:07 | Lara approaches the low stone ledge, catches its edge and pulls up. This is the local access sequence shown in the recording. |
| 00:07–00:18 | She turns on the ledge, moves onto/across the slope and aligns downhill. |
| 00:18–00:24 | Positioning settles, followed by the beginning of the slide. |
| 00:25–00:33 | Inventory/passport and the save list open; physical slot 3 is selected. The list initially shows the older counter in that slot. |
| 00:34–00:36 | Saving is confirmed and the menu closes. The resulting seed is 3095, visible in Part 2 and corroborated by the save inventory/journal. |
| 00:36–00:41 | Lara continues the slide, runs out and stops. This is after the seed was saved. |

## Video 2 — execution, approximately 02:42

| Video time | What happens / why it matters |
| --- | --- |
| 00:00–00:04 | The load list selects the starting save 3089 from physical slot 1. |
| 00:04–00:14 | The replay approaches the lower slope and corrects the facing direction. |
| 00:14–00:24 | One flare is drawn; crouching and the initial flare sequence establish the climb setup, then Lara slides back. |
| 00:24–00:28 | A short walk returns to the lower alignment point; inventory opens. |
| 00:28–00:43 | Eight lower menu buffers establish the calibrated angle: four left, two idle, one left, one idle. |
| 00:43–01:22 | The main crouch/flare climb proceeds. The bridge observes the live state to stop at the upper pause. |
| 01:22–01:57 | Nineteen upper crouch/menu buffers advance from animation frame 8693 to the required crouch frame 6675. |
| 01:57–02:10 | Passport navigation opens the save page while preserving the upper pose. Physical slot 4 is selected and becomes save 3097. |
| 02:11–02:18 | The load list selects slot 3 / 3095, placing Lara on the replacement room 35 slope. |
| 02:18–02:27 | While sliding on the seed slope, the replay opens the load list and reloads slot 4 / 3097. |
| 02:27–02:31 | The upper save resumes with the observed sideways crossing and settling motion. |
| 02:31–02:33 | A short forward walk reaches the final position, identified as room 148 by telemetry. |
| 02:33–02:42 | Inventory remains open at the successful endpoint. |

## Manual play

Read the separate [Temple Mudslide — Manual Walkthrough](MANUAL_WALKTHROUGH.html) for the player's step-by-step inputs and visual cues, including counting Lara's head nods and stopping at the height drop on the buffer after the first 15. A [Markdown copy](MANUAL_WALKTHROUGH.md) is also included. The automatic video starts its upper buffers from an earlier pause and therefore takes 19 instead of the manual example's 16.

## Execution tutorial

### Prerequisites

Use Windows, Tomb Raider III Remastered, Cheat Engine with Lua support (the original environment used CE 7.5), Python 3.10 or newer, and `ffmpeg` available on PATH. The executable must be `tomb123.exe` with the matching `tomb3.dll` layout. The supplied pointer expression is `["tomb3.dll"+3D4D30]+58`; it is build-specific and must be revalidated after game updates. The package does not include the game, level binaries, Cheat Engine, Python, FFmpeg or a personal save bank.

The active save bank must contain **3089 in slot 1**, **3088 preserved**, and the exact calibrated **3095 in slot 3**. Slot 4 will be overwritten with the upper checkpoint. The script is a replay of these specific saves, not a general route generator for arbitrary saves. A recipient who does not have the matching saves can review all evidence but cannot immediately run this calibrated replay. Obtain the required saves separately or perform and validate a new calibration; renaming a counter is insufficient.

Use tank controls, normal 60 FPS, and the following mapping: arrows for movement, **G** walk, **Y** crouch, **E** action, **Space** draw/holster, **comma** flare, **Esc** inventory, **F5/F9** save/load. In particular, use E for Action, even where historical notes mention Ctrl.

The menu recognizer is calibrated for a **1646 × 1089 outer game-window screenshot**, with the original German menu layout, font and scale. The delivered videos are 1630 × 1082 and are not the OCR reference size. Keep the window fully visible and unobscured. A different language, scale, resolution or layout requires recalibration; the recognizer should reject unfamiliar screens.

### Set up and play

1. Extract `Temple-Mudslide-Execution.7z` to a writable folder. Keep its directory structure. Back up your active save bank before a run.
2. Open a terminal in the extracted `Temple-Mudslide-Execution` folder and run `python setup.py`. Select your active `savegame.dat`. Setup checks the required counters/seed and FFmpeg, then writes local configuration and runtime locator files. No save data is changed by setup.
3. Start the game, load into Temple Ruins, and attach Cheat Engine to `tomb123.exe`. Open `MudSlide-Bridge.ct`. Allow its Lua loader and select `START_BRIDGE.lua` from this package in the file picker. This loads the Lua file with its filename available, allowing it to locate the other package files. Keep CE open, and leave every value-freeze checkbox clear.
4. Start from normal gameplay and run `python run_replay.py`. You have five seconds to focus the game. If the inventory ring is already open, use `python run_replay.py --from-inventory` instead. That option is not for an open passport or F9 list.
5. Let the replay finish without pressing game keys or moving another window over the game. It loads slot 1, climbs, saves to slot 4, loads slot 3 and returns to the new slot 4 checkpoint. The final inventory pause in room 148 marks completion.
6. Inspect the newly generated journal under `data/manual/`. Require `completed: true`, the room 148 endpoint and protected-record preservation. A video that merely looks close to the endpoint is not the automated success check.

To stop, run `python stop.py`; losing game focus also causes the bridge to reject/pause input. Check the actual game state before restarting. After a stop, reload `START_BRIDGE.lua`. Do not blindly retry a failed save or load. If recording, start and stop the recorder yourself; the replay does not control recording software.

The execution distribution replaces personal paths with runtime configuration and adds a focus countdown. Diagnostic position/flare memory setters are disabled in the shipped execution bridge. Use its documented playback entry point. The portable package has been checked offline; it has not been demonstrated on a different recipient's machine.

## How the proof is organized

Open [FINAL_PROOF.html](FINAL_PROOF.html) for the complete anchored page, with twelve chapters and 36 embedded images. The full proof ZIP restores the research directory layout: final publication chapters under `tomb-raider-analysis/temple-mudslide/docs/final/`, historical notes under `archive/`, textual measurements and journals under `data/`, research scripts under `scripts/`, selected screenshots under `media/screenshots/`, and classic source references under `tomb3/`. FINAL_PROOF.html and the manual walkthrough are also at the archive root. The HTML remains a self-contained offline reading edition; consult the full ZIP for supporting records. Some archived notes retain their original German.

The measured upper checkpoint is X **54234/54235**, Y **3355**, yaw **14629**, room **136**, state **71**, animation **222**, frame **6675**. The new seed begins at X **74328**, Y **−2110**, Z **58765**, yaw **16384** in room 35. The replay loads the upper save while the seed is sliding at X **74600–75450**, state **24**, animation **70**. The proposed cached-tilt mechanism selects the +X slide direction; the observed crossing is approximately 500 units before the final forward walk to room 148.

## Privacy, provenance and redistribution

Delivered text and structured records have local absolute paths, the known account/machine names and account identifier removed or replaced. Part 1 is stream-copied; Part 2 is re-encoded as H.264 below 100 MB at its original resolution and frame rate. Both retain their original audio streams, with original container metadata removed; **original audio is retained as requested**. Audio content is not anonymized or certified free of identifying speech. The video review used sampled frames, so it is not a frame-by-frame privacy certification.

Raw save banks, runtime files, user configuration, Git history and unrelated captures are excluded. The proof ZIP includes sanitized textual measurements, historical journals, research scripts and classic source references, together with the final publication and cited screenshots. Uncited raw captures and earlier large recordings are excluded. Private local configuration, screenshots, logs and save backups generated by future executions must be reviewed separately before sharing again.

Sanitization changes file bytes. Archive manifests hash the delivered copies; old hashes embedded in historical reports describe their original evidence and are not hashes of the sanitized copies. Classic source references describe the analysis model, not the Remastered source. Their accompanying license is included under `tomb3/LICENSE.md`.
