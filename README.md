# Earthquake Prediction Tool Documentation

## Overview
The Earthquake Prediction Pipeline is a comprehensive system that automates the collection, processing, and analysis of USGS earthquake data using three distinct models to predict and classify seismic activity:

1. **Global Regression Transformer**: Predicts the total number of earthquakes likely to occur in the next 24-hour period across all regions, learning from global seismic patterns.

2. **Regional Regression Transformer**: Provides region-specific earthquake count predictions for five key seismic zones (Pacific Northwest, California, Alaska, Hawaii, and Central US), accounting for local geological characteristics.

3. **Risk Level Classification Model**: A Multi-Layer Perceptron (MLP) classifier that categorizes earthquake events into risk levels (Low, Medium, High) based on magnitude, depth, and significance features.

Link to data feed: [Link Text](https://earthquake.usgs.gov/earthquakes/feed/)

## System Requirements

### Python 3.x Required Libraries:
- pandas - Data manipulation and analysis
- numpy - Numerical computing
- torch (PyTorch) - Deep learning framework and model creation
- requests - API data collection
- matplotlib/seaborn - Visualization
- scikit-learn - Risk classification and evaluation metrics
- scipy - Statistical computations

## Directory Structure

Copy
## Core Components

### 1. Data Collection and Processing
- USGS API Integration: Automated fetching of earthquake data
- Data Filtering: Configurable magnitude threshold (default: 2.5)
- Regional Assignment: Automatic categorization into defined seismic zones
- Feature Extraction: Geographic and seismic parameters
- Data Storage: Daily CSV files with comprehensive metadata

### 2. Model Architecture

#### A. Global Transformer
- Purpose: Global earthquake count prediction
- Components:
  - Input projection layer
  - Positional encoding
  - Multi-head attention layers
  - Feed-forward networks
  - Output projection layer
- Parameters:
  - Sequence Length: Configurable (default: 7 days)
  - Hidden Dimensions: 64
  - Number of Layers: 2
  - Attention Heads: 4

#### B. Regional Transformer
- Purpose: Region-specific count predictions
- Architecture: Similar to global transformer
- Key Difference: Separate model instances for each region
- Additional Features:
  - Region-specific parameter tuning
  - Local pattern recognition
  - Regional confidence intervals

#### C. Risk Classification Model
- Type: Multi-Layer Perceptron (MLP)
- Purpose: Earthquake risk level classification
- Architecture:
  - Input Layer: Processed features (magnitude, depth, significance)
  - Hidden Layers: (128, 64, 64) neurons
  - Output Layer: 3 classes (Low, Medium, High risk)
- Features:
  - Probability scoring for each risk level
  - Confidence threshold adjustments
  - Incremental learning capabilities

### 3. Training Pipeline

#### A. Baseline Training
- Data Processing:
  - Global and regional data separation
  - Feature dimensionality reduction
  - Sequence creation for transformers
  - Risk label generation for classifier

- Model Training:
  - Parallel training of all three models
  - Loss function: MSE for transformers, Cross-entropy for classifier
  - Optimizer: Adam
  - Validation-based checkpoint saving

- Evaluation:
  - Prediction accuracy metrics
  - Risk classification metrics
  - Regional performance comparison
  - Visualization generation

#### B. Continuous Monitoring
- Data Collection:
  - Configurable update interval
  - Real-time USGS data integration
  - Regional data sorting

- Prediction Generation:
  - Global earthquake count predictions
  - Regional count predictions
  - Risk level classification
  - Confidence interval calculations

- Model Optimization:
  - Performance evaluation
  - Incremental model updates
  - Automated checkpoint management
  - Regional model fine-tuning

### 4. Performance Metrics
- Count Prediction:
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - Regional prediction accuracy
  - Confidence interval coverage

- Risk Classification:
  - Accuracy, Precision, Recall
  - F1 Score
  - Confusion Matrix
  - ROC-AUC Score

- Visualization:
  - Global vs regional performance
  - Risk distribution analysis
  - Temporal trend analysis
  - Regional comparison plots

## Authors
- Stephen Moore
- Steven Wilhelm
- Lynn Yingling

## Version
5.0 (Last Updated: 24 November 2024)
