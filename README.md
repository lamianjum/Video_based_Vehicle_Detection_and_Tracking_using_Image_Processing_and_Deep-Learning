# VehicleDetection
Vision-based video monitoring systems offer several advantages. Tracking moving vehicles in video streams has been an active area of research in computer vision. The main aim is to detect and recognize moving objects vehicles from real surveillance videos to avoidcongestion on highways and parking areas for the prevention of accidents In addition to vehicle counts, a much larger set of traffic parameters such as vehicle classifications, lane changes, etc., can  be measured. Vehicle classification is important in the computation of the percentages of vehicle classes that use state-aid streets and highways. Even in large metropolitan areas, there is a need for data about vehicle classes that use a particular street. A classification system like the one proposed here can provide important data for a particular design scenario. To keep an eye on all the vehicles in a particular time domain, finding out accidents caused by overtaking, monitoring the speed of the vehicles are the motivation for this work. 

Here is overview of the work :

![](assets/ab.png)
![](assets/opening.gif)

# Workflow

The detecting module extracts and identifies the desired object, then send the detecting information and object information to the learning and tracking module, respectively. For detection of our vehicles,we used YoloV5, SSD, Mask RCNN. For tracking, it is necessary to find the positions of the object in two consecutive frames to generate the trajectory. For tracking, we used Deep Sortand GOTURN and with that, we have estimated the speed of each vehicle and also counted the number of vehicles. For speed estimation, we have estimated these values manually for the current road to calculate pixels per meter (ppm). We have taken the video frame and calculated the width of the road in pixels. Then converted pixels to meter now following this formula of speed(speed = dmeters X fps X 3.6) we get the values. For counting, we generated a counter and we divided the road into polygons for identifying lanes. Any class object inside the polygon region is boxed and the counter is updated. Thus we are counting,
tracking, and determining the speed of the vehicles.

![](assets/workflow.png)

# Dataset

We have built our own customize dataset.Find our dataset [here](https://drive.google.com/file/d/1YWh3K9SxrcBcwTvMcA9_lpTa2tDKquRF/view?usp=sharing)
For annotation, we used LableMaster.

![](assets/dataset.png)

# Installation
Python 3.6 or later with all requirements.txt dependencies installed, including torch>=1.7. To install run:
```bash
pip install -r requirements.txt
```

# Run Tracker
After you download this project, please download the weight of YOLO V5 model and Deep-SORT model respectively. 
You can download the YOLO weight trained by me from https://drive.google.com/file/d/1-8Xm3eUMMJF5XNiF649kqnqoYeWhv3kT/view?usp=sharing or choose to download the pretrained weight of the YOLO V5 model with using the `./yolov5/weights/downloadweight.sh`.

You can download the Deep-SORT weight trained by me from https://drive.google.com/file/d/1-GjB1pGudjM70C1Jk7WhWUWShzCvvvra/view?usp=sharing or choose to download the pretrained weight of the Deep-SORT model from https://drive.google.com/file/d/1-EsIHxEqr9elRryUqPBcBBAY3qoIEbZS/view?usp=sharing . And then put the weight into the folder namely `/deep_sort_pytorch/deep_sort/deep/checkpoint`.

Finanlly, you can choose to download the test video producted by me from https://drive.google.com/file/d/1cMch88P8xZ95SoHN88aC53oiOLlD3Egb/view?usp=sharing.

Tracking can be run on most video formats

```bash
python3 track.py --source ...
```

- Video:  `--source file.mp4`
- Webcam:  `--source 0`
- RTSP stream:  `--source rtsp://170.93.143.139/rtplive/470011e600ef003a004ee33696235daa`
- HTTP stream:  `--source http://wmccpinetop.axiscam.net/mjpg/video.mjpg`

MOT compliant results can be saved to `inference/output` by 

```bash
python3 track.py --source ... --save-txt
```

![](assets/counting.gif)

# Data Analysis

![](assets/mask.png)
![](assets/yolov5.png)
![](assets/ssd.png)

# Performance Analysis

![](assets/pf1.png)
![](assets/pf2.png)
![](assets/pf3.png)
![](assets/pf4.png)

# Applications.
1. Traffic monitoring.
2. Vehicle speed detection from traffic camera.
3. Accident detection.
4. Environment monitoring for self driving cars.
5. Object tracking drones.




