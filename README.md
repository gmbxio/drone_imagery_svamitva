Drone Imagery Segmentation for SVAMITVA
This repository contains a deep learning pipeline for the high-precision extraction of features (buildings, roads, water bodies, and utilities) from high-resolution drone imagery, specifically designed for the SVAMITVA (Survey of Villages Abadi and Mapping with Improvised Technology in Village Areas) scheme.

🚀 Key Features
Geospatial Engine:

Rasterio: Memory-efficient raster reading and window-based chunking to handle massive GeoTIFF files without crashing system memory.

GeoPandas & Shapely: Spatial bounding, intersection filtering, and precise vector-to-raster mask generation for ground truth preparation.

Architectural Excellence:

Multi-Model Approach: Implementations of U-Net++ and DeepLabV3+ architectures.

Encoders: Leverages segmentation-models-pytorch and timm for powerful backends like EfficientNet-B5.

Advanced Methodology:

Class Balancing: Addressing data imbalance by remapping sparse classes and applying custom weight tensors (weighting critical utility classes up to 15x heavier).

Optimization & Ensembling: Model outputs are ensembled via SLSQP (Sequential Least Squares Programming) optimization to achieve superior segmentation masks compared to single-model outputs.

Scheduling: Uses Cosine Annealing learning rate schedulers to navigate complex loss landscapes during training.

🛠️ Tech Stack
Language: Python

Deep Learning: PyTorch, segmentation-models-pytorch (SMP), timm

Geospatial: Rasterio, GeoPandas, Fiona, Shapely

Augmentation: Albumentations (Spatial transformations, rotations, and terrain-specific normalization)

📋 Pipeline Overview
Spatial Tiling: Extracting 256x256 tiles and labels from GeoTIFFs and Shapefiles using spatial intersections.

Preprocessing: Applying Albumentations for robust generalization across varied rural terrains.

Training: Simultaneous training using a Hybrid Dice + Cross-Entropy Loss to optimize both global overlap and local pixel accuracy.

Evaluation: Metrics calculated include IoU (Jaccard Index) and Dice Coefficient (F1-Score).

Inference: Large-scale windowed inference to reconstruct full-village segmentation maps from tiled predictions.

📊 Metrics & Evaluation
The model model_A_unetpp_b5.pth is evaluated based on its ability to handle complex rural structures. For evaluation, use the provided validation loop to check:

Mean IoU: Overlap accuracy.

Fscore: Harmonic mean of precision and recall.

Class-wise Accuracy: Essential for the 15x weighted utility/bridge classes.

🔗 Model Source 
To access the model from huggingface the link is given below:

https://huggingface.co/gmbxio/best_unetb5_accuracy

go to files and version and download the best_unetb5_accuracy.pth

📜 License
This project is licensed under the MIT License - see the LICENSE file for details
