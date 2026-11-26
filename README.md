# Physics Lab

An interactive physics environment that helps you learn through play.

## [Launch Physics Lab](https://aaron-ragsdale.github.io/PhysicsLab/)

Free Play lets you grab, throw, stack and collide objects. Place balls, blocks, triangles, dominoes, ramps, platforms and pendulums. Experiment with gravity, materials, restitution, friction and size. Pause, single-step or change simulation speed. Try the playground, empty arena, domino run or block tower presets.

Material and object-property changes apply to newly placed objects. Matter.js 0.20.0 loads from jsDelivr and runs locally in the browser. No API keys, backend or build step required. Internet access is needed to load the engine unless cached.

## 2D and 3D labs

- [2D Lab](https://aaron-ragsdale.github.io/PhysicsLab/): existing Matter.js playground plus Draw shape. Drag a closed outline, choose Smart snap for circles and rectangles or Smoothed custom shape for irregular polygons. Choose Fixed object to create stationary geometry. Use Grab / throw to interact afterward.
- [3D Lab](https://aaron-ragsdale.github.io/PhysicsLab/3d.html): Three.js rendering and Rapier rigid-body simulation. Orbit the camera, place spheres, blocks, cylinders, ramps and platforms, or grab and reposition bodies.
- Import local STL, OBJ, PLY, GLB or self-contained GLTF files. Geometry is normalized to the requested longest dimension in meters; STL is assumed Z-up. Imported meshes use a lab material rather than their original textures. Select convex hull, bounding box or fixed triangle mesh collision. Hulls approximate concave geometry; triangle meshes are fixed only. File limit 50 MB, vertex limit 300,000.
- Adjust gravity, friction, bounce, mass and simulation speed. Select objects to rotate or remove them. The experimental 3D hand cursor uses a single selected hand and screen-plane grab/release, not calibrated depth.
- Both pages run locally in the browser after downloading dependencies. No model upload or backend is required. WebGL and HTTPS camera support depend on the device. Scene persistence, STL export and 2D-to-3D extrusion are not yet implemented.

## Hosting

In Settings → Pages, select Deploy from a branch, main, / (root), and Save.

## Future modes

Challenges and Sports are placeholders. Free Play is the first playable mode.

## Optional pose controls

Select Enable pose control and grant camera access. MediaPipe Pose Landmarker Lite runs locally, tracking wrists or wrists and ankles. Move tracked points through objects to impart velocity. Adjust motion strength and tracking responsiveness in the sidebar. Mouse and touch remain available. Disable pose control to stop the camera. The model and runtime download from external hosts; camera frames are processed locally. Camera access requires HTTPS and browser permission. This is a 2D motion mapping, not calibrated physical force measurement.

### Gesture commands

Choose Push + hold to grab, Push only, or Hold to grab only. With a selected wrist or index landmark, hover steadily over a movable object for the configured hold duration (default 0.8 seconds). The amber countdown ring shrinks and turns green when the object is grabbed. Move the object at least 40 simulation pixels, then hold still for the same duration to release. Space or Release objects also releases held objects, using the most recent hand velocity when available. If a controlling landmark becomes invisible or stale, the object is released automatically. Only one grab per physical hand is supported. Tracking thresholds and timing may need tuning on individual devices.

### Tracking stability and diagnostics

Physics Lab supports Lite, Full (default), and Heavy pose models. Select GPU (default, CPU fallback on initialization failure) or CPU while pose control is disabled, then enable tracking. Target inference FPS is adjustable. One Euro adaptive filtering and speed-limited virtual interaction cursors smooth motion between predictions. Outliers are excluded and reacquisition requires stable samples and the configured cooldown; invisible points cannot interact. A 100 ms per-landmark/per-object impact cooldown reduces repeated velocity impulses. The performance monitor reports rendering FPS, completed inference FPS, average synchronous inference time and rejected landmark predictions. Enable Show raw predictions to compare raw red crosses with filtered interaction circles. Diagnostics are local; inference timing does not measure total camera-to-display latency. Actual performance depends on device and model.
