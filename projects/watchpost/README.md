# Watchpost

### Video monitoring, motion detection, and stream-health records in the browser.

Watchpost is a browser-based video monitoring and recording system. It combines configurable motion detection, timestamped local recordings, passcode-protected live viewing, and stream-health monitoring in one compact application. A built-in HLS adapter brings compatible public video streams into the same detection and recording workflow as a device camera.

![Watchpost running on a public traffic feed](watchpost-desktop.png)

The camera does the work. It compares changes across a configurable motion grid, records when activity crosses the selected threshold, and keeps recording for a chosen interval after movement stops. Sensitivity and ignore zones let the operator tune detection to the scene. Continuous recording is available too, with five-minute motion clips, ten-minute continuous clips, and local folder storage.

![Watchpost during nighttime traffic](watchpost-traffic.png)

The HLS adapter connects stream playback to a monitoring record: segment-number gaps, repeat downloads and changed ETags, source-declared discontinuities, download failures, and recoveries. Feed checks watch for pauses, frozen pictures, and changes in how far playback trails the live edge. Clock and heartbeat checks flag timing changes and an unclean previous session without claiming to know the underlying cause.

Each clip can carry a matching JSON record with its source, timing context, segment metadata, and events during recording. The interface distinguishes device-camera timestamps from stream-receipt timestamps. Recent events persist in browser storage and can be exported as JSONL; with a folder selected, the application also writes daily event and heartbeat files. WebRTC provides passcode-protected remote live viewing.

The interface keeps the camera image central, with amber motion indicators, recording status, and grouped controls that adapt to desktop and phone screens. Connection recovery and visible storage errors are part of the design, because a recorder needs to remain useful when remote viewing fails.

![Watchpost running in a phone browser](watchpost-mobile.jpg)

Watchpost combines browser media APIs, canvas-based motion analysis, local recording, and authenticated peer communication in a portable single-file application. The screenshots come from a live public-feed demonstration on desktop and mobile. Traffic imagery: Caltrans, I-5 south of I-10, Camera 17. No affiliation or endorsement is implied.

The updated adapter and monitoring logic were inspected in source and exercised with focused Chrome checks using simulated stream events and folder writes. The screenshots show the earlier desktop and mobile public-feed demonstration. Full live-stream fault testing, long unattended operation, remote-access security regression testing, and off-device backup remain separate validation work. These records describe observable stream behavior; they do not prove footage authenticity or diagnose an attack.

**Source is privately maintained.** This showcase shares the project and its interface without distributing the application.
