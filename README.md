# Social-Distancing-Detection-using-Computer-Vision

Detecting compliance of social distancing using Computer Vision and Deep Learning using YOLO v5 (yolov5x). The model is pre-trained on COCO dataset on 80 different classes.

## Setting up the environment
Create a virtual environment: `python -m venv <env-path>`

Install the libraries: `pip install -r ./code/requirements.txt`

## Inference using detect.py

Weights to downloaded are given below or they automatically will be downloaded when the following command is run. The `--classes` tag is used to detect only people. The results of inference will be stored under runs/detect/. Instead of specifying `yolov5x.pt` path to other model weights can be provided.

`python ./code/detect.py --weights yolov5x.pt --source <video-path> --classes 0`

See the [YOLOv5 Docs](https://docs.ultralytics.com/yolov5/) for full documentation on training, testing and deployment.

### Pretrained Checkpoints

| Model                                                                                           | size<br><sup>(pixels) | mAP<sup>val<br>50-95 | mAP<sup>val<br>50 | Speed<br><sup>CPU b1<br>(ms) | Speed<br><sup>V100 b1<br>(ms) | Speed<br><sup>V100 b32<br>(ms) | params<br><sup>(M) | FLOPs<br><sup>@640 (B) |
| ----------------------------------------------------------------------------------------------- | --------------------- | -------------------- | ----------------- | ---------------------------- | ----------------------------- | ------------------------------ | ------------------ | ---------------------- |
| [YOLOv5n](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5n.pt)              | 640                   | 28.0                 | 45.7              | **45**                       | **6.3**                       | **0.6**                        | **1.9**            | **4.5**                |
| [YOLOv5s](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5s.pt)              | 640                   | 37.4                 | 56.8              | 98                           | 6.4                           | 0.9                            | 7.2                | 16.5                   |
| [YOLOv5m](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5m.pt)              | 640                   | 45.4                 | 64.1              | 224                          | 8.2                           | 1.7                            | 21.2               | 49.0                   |
| [YOLOv5l](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5l.pt)              | 640                   | 49.0                 | 67.3              | 430                          | 10.1                          | 2.7                            | 46.5               | 109.1                  |
| [YOLOv5x](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5x.pt)              | 640                   | 50.7                 | 68.9              | 766                          | 12.1                          | 4.8                            | 86.7               | 205.7                  |
|                                                                                                 |                       |                      |                   |                              |                               |                                |                    |                        |
| [YOLOv5n6](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5n6.pt)            | 1280                  | 36.0                 | 54.4              | 153                          | 8.1                           | 2.1                            | 3.2                | 4.6                    |
| [YOLOv5s6](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5s6.pt)            | 1280                  | 44.8                 | 63.7              | 385                          | 8.2                           | 3.6                            | 12.6               | 16.8                   |
| [YOLOv5m6](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5m6.pt)            | 1280                  | 51.3                 | 69.3              | 887                          | 11.1                          | 6.8                            | 35.7               | 50.0                   |
| [YOLOv5l6](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5l6.pt)            | 1280                  | 53.7                 | 71.3              | 1784                         | 15.8                          | 10.5                           | 76.8               | 111.4                  |
| [YOLOv5x6](https://github.com/ultralytics/yolov5/releases/download/v7.0/yolov5x6.pt)<br>+ [TTA] | 1280<br>1536          | 55.0<br>**55.8**     | 72.7<br>**72.7**  | 3136<br>-                    | 26.2<br>-                     | 19.4<br>-                      | 140.7<br>-         | 209.8<br>-             |


## OpenVINO Optimization

Convert the model weights to OpenVINO IR format(.xml and .bin).

`python ./code/export.py --weigths <weights-path> --include openvino`

Run inference using the converted weights. The path `<folder-path>` is the path to the folder consisting .xml and .bin files.

See the [OpenVINO Docs](https://docs.openvino.ai/2022.3/notebooks/226-yolov7-optimization-with-output.html#verify-model-inference) for conversion and optimization.

`python ./code/detect.py --weights <folder-path> --source <video-path> --classes 0`

#### Weights: [YOLOV5x weights](https://drive.google.com/file/d/1yAqbr7ijYVVXaP5QRpnyMIScr2JoAq_W/view?usp=sharing)

## Results

https://github.com/S4HILp/Social-Distancing-Detection-using-Computer-Vision/assets/84588638/c3cd8d74-a634-4f71-a4c0-3f52086d8b06


