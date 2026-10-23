# Watchpost

**Created and designed by [Tyler Katayama](https://github.com/tylerkat89) · [Original project](https://github.com/tylerkat89/tylerkat89/tree/main/projects/watchpost)**

### Monitor the picture. Keep a record of the feed.

Watchpost brings camera feeds and compatible public video streams into a single browser-based monitoring and recording system. It combines configurable motion detection, timestamped local clips, passcode-protected live viewing, and a record of changes in stream health. The built-in HLS adapter lets public streams use the same detection and recording workflow as a device camera.

![Watchpost running on a public traffic feed](watchpost-desktop.png)

Motion detection compares changes across a configurable grid, starts recording when activity crosses the selected threshold, and continues for a chosen interval after movement stops. Sensitivity and ignore zones let the operator tune detection to the scene. Long motion recordings split at five minutes; continuous recordings split at ten. A selected local folder stores completed clips.

![Watchpost during nighttime traffic](watchpost-traffic.png)

The HLS adapter records segment gaps, repeated downloads, changes in server-provided segment identifiers, source-declared breaks, download failures, and recoveries. Feed checks watch for pauses, frozen pictures, and changes in how far playback trails the live edge. Clock and heartbeat checks flag timing changes and an unclean previous session without claiming to know the underlying cause.

Each clip can carry a matching JSON record with its source, timing context, segment metadata, and events during recording. The interface distinguishes device-camera timestamps from stream-receipt timestamps. Recent events persist in browser storage and can be exported as JSONL; with a folder selected, the application also writes daily event and heartbeat files. WebRTC provides passcode-protected remote live viewing.

The interface keeps the camera image central, with amber motion indicators, recording status, and grouped controls that adapt to desktop and phone screens. Connection recovery and visible storage errors are part of the design, because a recorder needs to remain useful when remote viewing fails.

![Watchpost running in a phone browser](watchpost-mobile.jpg)

Watchpost combines browser media APIs, canvas-based motion analysis, local recording, and authenticated peer communication in a portable single-file application. The screenshots come from a live public-feed demonstration on desktop and mobile. Traffic imagery: Caltrans, I-5 south of I-10, Camera 17. No affiliation or endorsement is implied.

The updated adapter and monitoring logic were inspected in source and exercised with focused Chrome checks using simulated stream events and folder writes. The screenshots show the earlier desktop and mobile public-feed demonstration. Full live-stream fault testing, long unattended operation, remote-access security regression testing, and off-device backup remain separate validation work. These records describe observable stream behavior; they do not prove footage authenticity or diagnose an attack.

**Source is privately maintained.** This showcase shares the project and its interface without distributing the application.


## Attribution

If you reference or adapt Watchpost, please keep the project name and creator credit attached so others can find the original work.

> Based on Watchpost by Tyler Katayama — https://github.com/tylerkat89/tylerkat89/tree/main/projects/watchpost

This credit line identifies the project's origin; it does not grant a license or change existing reuse terms.
