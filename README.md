# Fashion Recommender System

A deep learning-based fashion recommendation project built with TensorFlow, ResNet50, and Streamlit.

## Overview

This repository contains a simple image-based fashion recommender system. It extracts visual features from clothing images using a pretrained ResNet50 backbone, stores those features, and then finds visually similar items using nearest neighbor search.

## Features

- Feature extraction with ResNet50 pretrained on ImageNet
- Embedding generation for a local image catalog
- Similar item recommendation using Euclidean nearest neighbors
- Streamlit web UI for image upload and recommendation display

## Repository Structure

- `app.py` - generates feature embeddings from images stored in the `images/` folder and saves them as `embeddings.pkl` and `filenames.pkl`
- `main.py` - Streamlit application for uploading a query image and showing top fashion recommendations
- `test.py` - local test script that uses a sample image to verify recommendations from precomputed embeddings
- `README.md` - project documentation

## Requirements

The project uses Python and the following libraries:

- tensorflow
- numpy
- tqdm
- pillow
- scikit-learn
- streamlit
- opencv-python

## Setup

1. Create a Python virtual environment (recommended):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install tensorflow numpy tqdm pillow scikit-learn streamlit opencv-python
```

3. Prepare your dataset:

- Create an `images/` directory in the project root
- Add fashion product images into `images/`
- Create an `uploads/` directory to store user uploads

## Precompute Embeddings

Run `app.py` to build the embeddings database from the images in `images/`:

```powershell
python app.py
```

This generates:

- `embeddings.pkl`
- `filenames.pkl`

## Run the Streamlit App

Start the recommendation UI with:

```powershell
streamlit run main.py
```

Then open the URL shown in the terminal to upload a fashion image and view recommendations.

## Test the Recommendation Flow

Use `test.py` to run a local similarity query against a sample image:

```powershell
python test.py
```

This script loads `sample/shirt.jpg`, extracts features, and shows the nearest neighbors from the precomputed embeddings.

## Notes

- The system uses `ResNet50` with `include_top=False` and a `GlobalMaxPooling2D` layer for feature extraction.
- The recommendation engine uses `NearestNeighbors` with Euclidean distance.
- `app.py` and `main.py` both rely on `embeddings.pkl` and `filenames.pkl` being present.

## Improvements

Potential enhancements include:

- adding a larger and more diverse fashion image dataset
- fine-tuning the model for fashion-specific features
- adding category filtering and metadata-based ranking
- improving the UI with descriptions, ratings, and product links

