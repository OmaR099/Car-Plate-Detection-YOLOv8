# Car Plate Detection Using YOLOv8  

This project implements a Car Plate Detection system using the YOLOv8 (You Only Look Once version 8) model. The workflow involves gathering data through frame extraction from videos, annotating frames with bounding boxes for car plates using Roboflow, filtering out unused frames, training the YOLOv8 model, and testing it on video input. The detected license plate information is then extracted using PyTesseract and saved to a text file along with the date and time of detection.  

<img src="https://github.com/user-attachments/assets/dda06c4f-a00c-4af3-88b8-06baa14397a7" alt="image" width="850" height="850" />

## Table of Contents  

- [Features](#features)  
- [Prerequisites](#prerequisites)  
- [Data Collection](#data-collection)  
- [Data Annotation](#data-annotation)  
- [Training the Model](#training-the-model)  
- [Results](#results)  
- [License](#license)  
- [Acknowledgements](#acknowledgements)  

## Features  

- **Frame Extraction**: Automatically extracts frames from video files for analysis.  
- **Annotation**: Annotate frames with bounding boxes for license plates using Roboflow.  
- **Model Training**: Train the YOLOv8 model using customized datasets.  
- **Plate Detection**: Detect and extract license plate information from videos.  
- **Text Extraction**: Use PyTesseract to convert detected plates into text and save them to a file.  

## Prerequisites  

Before you begin, ensure you have the following installed:  

- Python 3.7 or higher
- YOLOv8 model files
- Roboflow account for annotation
- Tesseract OCR installed on your system

## Data Collection

Data was collected by creating a directory of images from a short video getting 100 frames using the frame extraction method.

## Data Annotation

**Annotate Frames:** Use Roboflow to annotate the extracted frames. Follow these steps:

- Upload the extracted frames to Roboflow.
- Create bounding boxes around the license plates in each frame.
- Export the annotations in YOLO format.

**Filter Frames:** After annotation, remove frames that do not contain any license plates. This will help in reducing the dataset size and improving training efficiency.

## Training the Model

Train YOLOv8: Use the following command to train the YOLOv8 model with the annotated dataset. The model will be trained for 100 epochs with an image size of 800.

```bash
!yolo task=detect mode=train model=yolov8s.pt data=path/to/your/data.yaml epochs=100 imgsz=800 plots=True
```
Ensure that your data.yaml file is correctly configured to point to your training and validation datasets.

![image](https://github.com/user-attachments/assets/2d538e7e-fb7d-4b18-a348-b15cdf2af420)

## Results

The output of the model will be saved in a text file named car_plate_data.txt, which contains the detected license plate information along with the date and time of detection for each frame where a plate was identified.

<img src="https://github.com/user-attachments/assets/37463ae1-d1cd-4b26-98ef-c71a8d23b320" alt="image" width="450" height="450" />
<img src="https://github.com/user-attachments/assets/dae8a091-a297-46a9-ae8c-724b06995004" alt="image" width="450" height="450" />

## License

This project is licensed under the MIT License.

## Acknowledgements

- YOLOv8 for providing a state-of-the-art object detection model.
- Roboflow for offering tools for image annotation and dataset management.
- PyTesseract for providing OCR capabilities to extract text from images.
