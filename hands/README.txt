HAND RIGS
Copyright © 2026 Forrest Moulin

Two rigged hands with embedded textures, ready to load as GLB files.
Each hand has 21 joints: one wrist, 15 finger controls and five tip endpoints.
The hands start open. There are no forearms or animation clips.

FILES
  assets/left-hand.glb   Left hand
  assets/right-hand.glb  Right hand
  mappings.json         All 21 landmark indices and exact bone names for both hands
  LICENSE.txt           MIT license and scope

BONE MAPPING
Left-hand names start with LeftHand; right-hand names start with RightHand.
The wrist is LeftHand or RightHand. Add the suffix below for each finger joint.
Indices are MediaPipe landmark indices (0-based), NOT glTF node indices.
Read each row from left to right:

  Part     Landmark indices   Bone suffixes
  Wrist    0                  (none)
  Thumb    1, 2, 3, 4          Thumb1, Thumb2, Thumb3, Thumb4
  Index    5, 6, 7, 8          Index1, Index2, Index3, Index4
  Middle   9, 10, 11, 12       Middle1, Middle2, Middle3, Middle4
  Ring     13, 14, 15, 16      Ring1, Ring2, Ring3, Ring4
  Pinky    17, 18, 19, 20      Pinky1, Pinky2, Pinky3, Pinky4

Example: landmark 6 maps to LeftHandIndex2 or RightHandIndex2.
Each finger is a chain: wrist -> joint 1 -> 2 -> 3 -> 4.
Joints 1-3 control bending; joint 4 marks the tip and does not deform the mesh.
For fingers, 1/2/3 mean base/middle/end knuckle (MCP/PIP/DIP).
For the thumb, they mean base/knuckle/end joint (CMC/MCP/IP).

HOW TO USE
1. Load the GLB for the person's left or right hand.
2. Find bones by name using mappings.json; do not rely on node array order.
3. Keep the model's rest transforms and bone lengths. Pose the wrist and rotate
   finger joints. Tip endpoints follow their parents.
4. For tracking, use consecutive landmark pairs as finger directions (e.g. 5->6
   drives Index1). Convert tracking coordinates to your scene, then calculate
   rotations relative to each bone's parent and rest pose. The mapping identifies
   joints; it is not a complete tracking or retargeting implementation.
5. Position and scale the loaded model to suit your scene; source scale is retained.

Landmark reference:
https://developers.google.com/edge/mediapipe/solutions/vision/hand_landmarker

LICENSE
Forrest Moulin's original contributions, including this README and mappings.json,
are licensed under the MIT License in LICENSE.txt. You may use, modify and share
those materials, including commercially, while retaining the copyright and license.
Third-party models and textures retain their original rights; their source license
was not recorded in this package.
