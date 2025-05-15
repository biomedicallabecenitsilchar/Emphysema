# Classification of Emphysema Disease Using Stacking Classifier Through Computed Tomography Images

This repository provides Python code for classifying emphysema subtypes using High-Resolution Computed Tomography (HRCT) scans. It includes scripts for preprocessing, feature extraction, and a stacking classifier pipeline, designed to process HRCT images and classify emphysema subtypes efficiently.

## Project Overview

The project focuses on emphysema classification by processing HRCT scans through a pipeline that includes image preprocessing, feature extraction using Histogram of Oriented Gradients (HOG), dimensionality reduction with Principal Component Analysis (PCA), and classification using a stacking classifier. The code is optimized for CPU-based execution, making it suitable for environments with limited computational resources, such as clinical settings.

## Dataset

The code is designed to work with the public Online Computed Tomography Emphysema Database, which can be accessed here:

- **Online Computed Tomography Emphysema Database**: [https://lauge-soerensen.github.io/emphysema-database/](https://lauge-soerensen.github.io/emphysema-database/)

The HRCT images in this online dataset are in .tiff format and need to be converted to .png before processing. Users can download the dataset from the link above and convert the images accordingly.

Hospital datasets used in this project are not shared due to confidentiality constraints. These datasets were collected from medical institutions, but only the code and methodology are provided in this repository.

## Installation

To set up the project, follow these steps:

1. **Clone the Repository**:
   ```
   git clone https://github.com/biomedicallabecenitsilchar/Emphysema.git
   cd Emphysema
   ```

2. **Create a Virtual Environment** (recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   Install the required Python packages manually using pip:
   ```
   pip install opencv-python scikit-learn numpy matplotlib
   ```
   The required packages are:
   - `opencv-python` for image preprocessing
   - `scikit-learn` for PCA and stacking classifier
   - `numpy` for data handling
   - `matplotlib` for visualization (optional)

## Usage

### 1. Preprocessing
Download the Online Computed Tomography Emphysema Database, convert the .tiff images to .png, and place them in a local directory (e.g., `data/raw/`). Rename `Preprocessing.txt` to `preprocess.py` (or copy its contents into a new `preprocess.py` file), then run the preprocessing script:
```
python preprocess.py --input-dir data/raw/ --output-dir data/preprocessed/
```
This script applies steps such as Gaussian filtering, lung segmentation, HU mapping, and thresholding to prepare images for feature extraction. Perform data augmentation if required.

### 2. Feature Extraction
Rename `Feature extraction.txt` to `extract_features.py` (or copy its contents into a new `extract_features.py` file), then extract HOG features from the preprocessed images:
```
python extract_features.py --image-dir data/preprocessed/ --output data/features.csv
```
This generates HOG features for use in the classification pipeline.

### 3. Classification
Rename `Stacking pipeline.txt` to `classify.py` (or copy its contents into a new `classify.py` file), then train and evaluate the stacking classifier:
```
python classify.py --features data/features.csv --model models/stacking_model.pkl
```
This script applies PCA and trains the stacking classifier. To classify new images, use:
```
python classify.py --features data/new_features.csv --model models/stacking_model.pkl --predict
```

## File Structure

- `Preprocessing.txt`: Code for the preprocessing pipeline for HRCT images.
- `Feature extraction.txt`: Code for HOG feature extraction.
- `Stacking pipeline.txt`: Code for stacking classifier training and prediction.

## Contributing

Contributions are welcome! You can help improve the code or add new features. To contribute:
1. Fork the repository.
2. Make your changes.
3. Submit a pull request with a description of your changes.
For suggestions or issues, please open an issue on this repository.

## Contact

For questions or collaboration, please open an issue on this repository.