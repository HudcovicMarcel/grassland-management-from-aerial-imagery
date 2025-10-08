Grassland Management from Aerial Imagery (GMAI)

The Grassland Management from Aerial Imagery (GMAI) dataset provides high-resolution aerial images and annotations of grassland management objects. It is designed for object detection tasks supporting research in grassland ecology, biodiversity monitoring, and sustainable land management.

Features
High-resolution orthophotos of grassland areas in the Alps and Carpathians
Bounding box annotations of management-related objects (e.g., hay bales, mowing traces, machinery)
YOLO-compatible format for object detection models
Suitable for training and evaluation of deep learning models (YOLOv11, Faster R-CNN, etc.)
Repository structure
├── images/
│   ├── train/
│   ├── val/
├── labels/
│   ├── train/
│   ├── val/
├── metadata/
│   ├── classes.txt
│   ├── LICENSE
│   ├── README.md
└── scripts/
    ├── visualize_annotations.py
    ├── prepare_yolo_format.py

Citation

If you use this dataset, please cite:

Grassland Management from Aerial Imagery (GMAI), [Your Name], 2025.

License

This dataset is released under the CC BY 4.0 License unless otherwise stated.

Contact

For questions or collaborations, please contact: [your.email@domain.com]
