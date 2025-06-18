🔍 Code Breakdown
📁 main.py
This is the main script that:

Loads a video (cv2.VideoCapture)

Applies background subtraction to detect moving objects

Tracks detected objects across frames

Displays the result with bounding boxes and IDs

✅ Step-by-step explanation:
Line 1–2: Import OpenCV (cv2) and the custom tracker from tracker.py.

Line 5: Create an instance of EuclideanDistTracker.

Line 7: Load the video highway.mp4.

Line 10: Create a background subtractor to detect moving objects (MOG2).

📦 In the loop:
Extract ROI: Focus on part of the frame [340:720, 500:800] — a cropped area, presumably where cars appear.

Detect motion:

Apply background subtractor.

Apply a binary threshold to extract clear shapes.

Find contours (connected components).

Ignore small contours (noise).

Track objects:

Use the tracker.update(detections) to assign or reuse object IDs based on position.

Draw and label objects:

Draw bounding boxes and display ID labels on the region of interest (ROI).

Show result:

Display the roi, full frame, and binary mask.

⚙️ tracker.py
This defines the class EuclideanDistTracker, which tracks objects using the distance between their center points.

📌 Key ideas:
Keeps a dictionary of previous object positions (self.center_points).

For each new detection:

Calculates the center of the bounding box.

Compares it to existing tracked points using Euclidean distance.

If it's within a threshold (< 25 pixels), it's considered the same object → reuse ID.

If it's a new object → assign a new ID.

Also cleans up unused IDs to avoid memory bloat.

✅ Summary
This code:

Detects moving vehicles or objects in a specific region of a video frame.

Assigns a unique ID to each object.

Tracks them across frames using a simple distance-based method.
