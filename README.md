# Deep AutoEncoder-Based Recommender System

## Overview

This project implements a Deep AutoEncoder-based recommender system using the MovieLens dataset. The system predicts user ratings for movies that have not been rated, facilitating movie recommendations tailored to user preferences. This repository outlines the implementation process, including data preparation, model architecture, training procedure, and insights derived from the results.

## Dataset

The project utilizes the MovieLens dataset, consisting of:
- 100,000 ratings from 943 users on 1,682 movies.
- Ratings range from 1 to 5, with 0 representing unrated movies.

The data was preprocessed to ensure that each user rated at least 20 movies.

### Files in the Dataset
- `ratings.csv`: User ratings for movies.
- `movies.csv`: Metadata for movies.

## Data Preparation

1. **Data Splitting**: The data was divided into training and validation sets based on the 98th percentile of timestamps.
2. **Data Cleaning**: 
   - Ensured users in the validation set were present in the training set.
   - Removed movies absent from the training set.

## Model Architecture

### AutoEncoder Structure
- **Encoder**:
  - Input Layer: 9559 nodes (dimensionality of the movie-user matrix)
  - Hidden Layers: 512, 512, and 1024 nodes with ReLU activation
- **Decoder**:
  - Hidden Layers: 1024, 512, and 512 nodes with ReLU activation
  - Output Layer: 9559 nodes

### Loss Function
- A custom Masked Mean Squared Error (MSE) loss function was employed, focusing only on non-zero ratings for error calculation.

## Training Procedure

- The model was trained over 40 epochs using the Adam optimizer with a learning rate of 0.001.
- Training loss consistently decreased, indicating effective learning and error minimization.

## Results

- **Initial Loss (Epoch 1)**: ~10.77
- **Final Loss (Epoch 40)**: ~0.61
- The model demonstrated a strong capability to minimize reconstruction error.

## Future Enhancements

- **Parameter Tuning**: Adjusting learning rates, hidden layers, and activation functions for potentially better performance.
- **Data Scaling**: Exploring normalization or different loss functions.
- **Model Complexity**: Adding depth or regularization for improved generalization.

## Usage

### Prerequisites
- Python 3.x
- PyTorch
- Pandas
- NumPy
- Matplotlib

### Running the Project

1. Clone this repository.
2. Prepare the data by executing the data preparation scripts in the provided notebook.
3. Train the model using the training script.
4. Evaluate the results using the provided evaluation code.

### Acknowledgments
- Special thanks to the MovieLens dataset providers for making the data publicly available.
