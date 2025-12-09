# Prompt Object Segmentation and Tracking
## Objective
Given **two input videos**, the goal is to:
1. Detect and segment the target object.
2. Blur only the background while keeping the object sharp.
3. Produce output videos using:
   - **SAM (Segment Anything Model)**  
   - **YOLOv8-Seg (Ultralytics segmentation model)**
4. Compare results between the two segmentation approaches.




---

## Methods Used

### 1. SAM Segmentation (Video 1)
- Model used: `vit_b`
- Bounding box manually selected on first frame.
- Predictor applied frame-by-frame.
- Masks cleaned (closing + dilation).
- Background blurred using Gaussian blur.
- Final video exported at 30 FPS.

### 2. YOLOv8 Segmentation (Video 2)
- Model used: `yolov8s-seg.pt`
- Fully automated segmentation on every frame.
- Extracted polygon mask → binary mask → blur background.
- Exported final blurred output.

---

## Results Summary

### **Video 1 (SAM)**  
- Strong object boundary quality  
- Very smooth and accurate mask  
- Best for videos with a single clear object

### **Video 2 (YOLO)**  
- Automatic and fast  
- Good enough for moving objects  
- Perfect for sports / fast motion  

---

## ibraries Used
- OpenCV
- NumPy
- Ultralytics YOLOv8
- Meta Segment Anything
- Matplotlib

---

## utput Files
- `blurred_video1_SAM.mp4`
- `blurred_video2_YOLO.mp4`

---

##  Conclusion
Both models are effective, but:

- **SAM** gives higher-quality segmentation but requires manual input.
- **YOLOv8** is better for automation and speed, especially when objects move fast.

The assignment demonstrates the strength of combining segmentation + tracking + background blurring.

