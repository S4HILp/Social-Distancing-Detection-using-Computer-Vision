# Social-Distancing-Detection-using-Computer-Vision

Detecting compliance of social distancing using Computer Vision and Deep Learning using YOLO v5 (yolov5x).

## Setting up the environment
Create a virtual environment: `python -m venv <env-path>`

Install the libraries: `pip install -r requirements.txt`

## Inference using detect.py

Weights will automatically be downloaded when the following command is run. The `--classes` tag is used to detect only people. The results of inference will be stored under runs/detect/.

`python detect.py --weights <weights-path> --source <video-path> --classes 0`

See the [YOLOv5 Docs](https://docs.ultralytics.com/yolov5/) for full documentation on training, testing and deployment.

## OpenVINO Optimization

Convert the model weights to OpenVINO IR format(.xml and .bin).

`python export.py --weigths <weights-path> --include openvino`

Run inference using the converted weights. The path `<folder-path>` is the path to the folder consisting .xml and .bin files.

See the [OpenVINO Docs](https://docs.openvino.ai/2022.3/notebooks/226-yolov7-optimization-with-output.html#verify-model-inference) for conversion and optimization.

`python detect.py --weights <folder-path> --source <video-path> --classes 0`

## Results

https://github.com/S4HILp/Social-Distancing-Detection-using-Computer-Vision/assets/84588638/c3cd8d74-a634-4f71-a4c0-3f52086d8b06


