# 步姿 Pose Lab

A browser-based prototype for static pose review and walking-video analysis. It runs MediaPipe Pose Landmarker in the browser, overlays a detected skeleton, estimates elbow/hip/knee angles, and exports sampled landmark data as JSON.

## Run

Open `index.html` from a static web server or deploy the repository with GitHub Pages. The page loads the pinned MediaPipe Tasks Vision 1.1.1 package and pose model from their public CDN on first launch, so an internet connection is needed to initialize analysis. Photo and video files are processed in the browser and are not uploaded by this app.

## Features

- Photo mode: all 33 pose landmarks, a full skeleton overlay, and bilateral elbow, hip, and knee angle estimates. Drag any visible point to manually correct its position; corrected image-plane angles and JSON exports update with the edit.
- Video mode: local video playback, selectable 24/25/30/50/60 FPS frame stepping, seek-to-frame correction, timestamped pose sampling, angle timeline, preliminary cadence context, and bilateral shoulder, elbow, wrist, hip, knee, and ankle angle estimates.
- Gait event log: mark left/right heel strike, toe-off, or a custom observation on the current frame; jump to or delete logged events. The JSON report includes event type, side, timestamp, and frame index. Landmark edits remain attached to their video frame.
- Drag-and-drop upload, capture guidance, confidence indicators, draggable landmark correction, overlay toggle, session clearing, and JSON export.
- Responsive Traditional Chinese interface.

## Limits

This is an early prototype. Joint angles are image-based 3D landmark estimates from a single camera, sensitive to view angle, lighting, occlusion, and frame quality. Wrist angle is approximated with the elbow, wrist, and index-finger landmarks. The gait view does not infer calibrated walking speed or real-world step length, and is not a medical or diagnostic tool.

## Privacy

The app does not send the selected photo or video to a server. The model runtime and model asset are fetched from jsDelivr and Google Cloud Storage. MediaPipe's package may send usage/performance metrics; review its current privacy documentation before production use.

## References

- [MediaPipe Pose Landmarker for Web](https://developers.google.com/edge/mediapipe/solutions/vision/pose_landmarker/web_js)
- [MediaPipe Tasks Vision on npm](https://www.npmjs.com/package/@mediapipe/tasks-vision)
