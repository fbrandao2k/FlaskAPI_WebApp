# Flask Python API - Web App - Object detection in a streaming video or Webcam

Based on the Udemy course: [YOLOv8, Train Custom Dataset, Object Detection, Segmentation, Tracking, Real World 17 + Projects & Web Apps in Python](https://www.udemy.com/course/yolov8-the-ultimate-course-for-object-detection-tracking/?utm_source=adwords&utm_medium=udemyads&utm_campaign=LongTail_la.EN_cc.BR&campaigntype=Search&portfolio=Brazil&language=EN&product=Course&test=&audience=DSA&topic=&priority=&utm_content=deal4584&utm_term=_._ag_112130202440_._ad_467215026440_._kw__._de_c_._dm__._pl__._ti_aud-2297301418005%3Adsa-1007766171312_._li_9217442_._pd__._&matchtype=&gad_source=1&gclid=Cj0KCQjwj4K5BhDYARIsAD1Ly2ob30_806U1E4g9s2P3xlHKqpn1GkUzKFMkj54bLi7W_D8RbAfryoQaAhKOEALw_wcB&couponCode=LETSLEARNNOW)

Here’s an overview of what this code accomplishes:

## Features

* Flask API Python
* Stream video
* Webcam video capture
* Real-time object detection with YoloV8

### flaskapp.py:

Sets up a Flask web server with two main routes (/video and /webcam).
The generate_frames function handles video processing by passing a video file or webcam feed through a YOLO model (defined in YOLO_Video.py) and outputs frames with bounding boxes drawn around detected objects.
The output is then streamed as an MJPEG video over HTTP.
YOLO_Video.py:

Uses YOLO (You Only Look Once) v8 for real-time object detection.
The video_detection function reads frames from a video file or webcam feed, processes each frame with the YOLO model to identify objects, and draws bounding boxes with labels (object name and confidence).
Detected frames are then streamed back to flaskapp.py for HTTP delivery.
Code Breakdown
In flaskapp.py:

The Flask library handles the web server.
generate_frames:
Passes a video path to video_detection (from YOLO_Video.py).
Converts each processed frame to bytes and streams as an MJPEG sequence.
Routes:
/video: Streams a specified video file.
/webcam: Streams a live webcam feed.

### YOLO_Video.py:

video_detection:
Initializes YOLO v8 with a weights file to detect various object classes (e.g., people, cars).
Reads each frame, identifies objects, draws bounding boxes, and labels them with object names and confidence scores.
The resulting frames are returned one by one, allowing for real-time video streaming in flaskapp.py.
Overall, this setup performs object detection on video and streams it over a Flask server as an MJPEG video, making it accessible via a web browser.

## How to use it

In the terminal, go to this folder, then install all python requirements:

```
pip install -r requirements.txt
```

And run:

```
python flaskapp.py
```

In the web browser, go to:

* http://127.0.0.1:5000/video -> run the real time object detection in the video
* http://127.0.0.1:5000/webcam -> to the real time object detection from the webcam







