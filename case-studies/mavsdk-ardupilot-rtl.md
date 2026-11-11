# Generate a compatible return-to-launch mission item for ArduPilot

## Problem

MAVSDK can append a return-to-launch (RTL) item when uploading a mission. It used NaN for four unused parameters. ArduPilot rejected those parameters during mission upload, so enabling the option could prevent a mission from uploading.

## Change

For ArduPilot, the generated RTL item now uses zero for the four unused parameters. Other autopilots keep the previous NaN values.

## Validation and scope

The merged change includes a system test and its build registration. The test uploads and reads back the generated item for ArduPilot and PX4 configurations. Separate ArduPilot 4.7.2 software-in-the-loop testing supported the mission-upload diagnosis; it was not an armed-flight or hardware test.

At the final PR head, the Linux build/test and fuzzing workflows failed; macOS, Windows and Kotlin workflows succeeded. The failures were disclosed during review, and their cause was not established. This entry does not claim fully passing CI.

## Upstream evidence

[MAVSDK #3213](https://github.com/mavlink/MAVSDK/pull/3213) was approved by JonasVautherin and merged by julianoes on 10 November 2026 at [commit `fc2bd5d`](https://github.com/mavlink/MAVSDK/commit/fc2bd5dda3d4e02ed10d0f47cb6cf34d5a0ad982). The maintainer-created squash commit records a different author email from my preferred contribution email.
