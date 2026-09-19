# WORKSHOP-5 🚘 License Plate Detection using OpenCV and Haar Cascade Classifier
## Name: MEYYAPPAN T
## Reg.No: 212223240086

## 📌 Overview

This project demonstrates **automatic license plate detection** using **OpenCV's Haar Cascade Classifier**. The system can detect vehicle number plates from both static images and live webcam streams.

Haar Cascade classifiers are lightweight, fast, and suitable for real-time object detection tasks, making them useful for applications such as:

* Automatic Number Plate Recognition (ANPR)
* Smart Parking Systems
* Traffic Monitoring
* Toll Collection Systems
* Security and Surveillance

> **Note:** This project focuses only on detecting the license plate region. It does not perform Optical Character Recognition (OCR) to extract plate numbers. OCR functionality can be integrated later using Tesseract OCR or deep learning-based text recognition models.

---

## 🎯 Objectives

* Detect license plates from vehicle images.
* Perform real-time plate detection using a webcam.
* Visualize detected plates with bounding boxes.
* Build a foundation for future ANPR systems.

---

## 🧠 Methodology

The system follows three main stages:

### 1. Load Haar Cascade Classifier

A pre-trained Haar Cascade XML file is used to detect license plate regions.

```python
haarcascade_russian_plate_number.xml
```

### 2. Detect License Plates

The image is converted to grayscale and processed using OpenCV's `detectMultiScale()` method.

### 3. Visualize Detection Results

Detected license plate regions are highlighted using rectangular bounding boxes.

---

## 📁 Project Structure

```text
License-Plate-Detection/
│
├── ws_05.ipynb                           # Main Jupyter Notebook
├── haarcascade_russian_plate_number.xml  # Haar Cascade model
│
├── images/
│   └── sample_plate.jpg                  # Input image
│
├── results/
│   └── output_detection.jpg              # Detection output
│
└── README.md
```

---

## 🛠️ Requirements

Install the required Python libraries:

```bash
pip install opencv-python numpy
```

For Jupyter Notebook support:

```bash
pip install notebook
```

---

## ▶️ Running the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/License-Plate-Detection.git
cd License-Plate-Detection
```

### Step 2: Launch Jupyter Notebook

```bash
jupyter notebook ws_05.ipynb
```

### Step 3: Execute the Notebook

Run all cells sequentially to:

* Load the Haar Cascade model
* Read an input image
* Detect license plates
* Display detection results

---

## 🧪 Image-Based Detection

```python
import cv2

# Load Haar Cascade
plate_cascade = cv2.CascadeClassifier(
    "haarcascade_russian_plate_number.xml"
)

# Read image
img = cv2.imread("images/sample_plate.jpg")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Detect plates
plates = plate_cascade.detectMultiScale(
    gray,
    scaleFactor=1.1,
    minNeighbors=4
)

# Draw bounding boxes
for (x, y, w, h) in plates:
    cv2.rectangle(
        img,
        (x, y),
        (x + w, y + h),
        (0, 255, 0),
        3
    )

# Display result
cv2.imshow("License Plate Detection", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

---

## 🎥 Real-Time Webcam Detection

```python
import cv2

plate_cascade = cv2.CascadeClassifier(
    "haarcascade_russian_plate_number.xml"
)

cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()

    gray = cv2.cvtColor(
        frame,
        cv2.COLOR_BGR2GRAY
    )

    plates = plate_cascade.detectMultiScale(
        gray,
        1.1,
        4
    )

    for (x, y, w, h) in plates:
        cv2.rectangle(
            frame,
            (x, y),
            (x + w, y + h),
            (255, 0, 0),
            3
        )

    cv2.imshow(
        "License Plate Detection",
        frame
    )

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

---

## 📊 Results

### Input

Vehicle image or live webcam feed.

### Output

* Automatic detection of license plate regions.
* Bounding box drawn around detected plates.
* Real-time visualization for webcam streams.

---

## 📈 Advantages

✅ Fast and lightweight detection

✅ Suitable for real-time applications

✅ Easy to implement using OpenCV

✅ Low computational requirements

---

## ⚠️ Limitations

* Sensitive to lighting conditions.
* Performance decreases for tilted or partially visible plates.
* Limited accuracy compared to modern deep learning detectors.
* Does not recognize plate text.

---

## 🎯 Applications

* Automatic Number Plate Recognition (ANPR)
* Smart Parking Management
* Toll Plaza Automation
* Traffic Law Enforcement
* Vehicle Tracking Systems
* Security Surveillance

---

## 🔮 Future Enhancements

* Integrate Tesseract OCR for plate number extraction.
* Apply image preprocessing techniques such as:

  * Denoising
  * Thresholding
  * Contrast Enhancement
* Train custom Haar Cascades for regional license plates.
* Replace Haar Cascade with deep learning models such as:

  * YOLOv8
  * SSD
  * Faster R-CNN
* Deploy as a web or mobile application.

---

## 👨‍💻 Technologies Used

* Python
* OpenCV
* NumPy
* Jupyter Notebook
* Haar Cascade Classifier

---

## 📜 Conclusion

This project successfully demonstrates license plate detection using OpenCV's Haar Cascade Classifier. While Haar Cascades offer a simple and efficient approach for real-time detection, integrating OCR and modern object detection models can significantly improve accuracy and enable complete Automatic Number Plate Recognition (ANPR) systems.
