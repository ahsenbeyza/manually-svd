# Manually-SVD: Scene Change Detection

This project implements a video shot boundary detection system using a custom Singular Value Decomposition (SVD) and Total Absolute Difference (TAD), based on Lu and Shi (2013). It detects scene transitions in videos by analyzing frame differences and verifying them with SVD features.

## Features
- Frame extraction with OpenCV and grayscale conversion.
- TAD computation to identify potential transitions.
- Custom SVD implementation using the Jacobi method.
- Transition verification via Euclidean distance of singular values.
- Outputs: Transition frames, `transitions.txt`, `tad_values.csv`, TAD plots, and heatmaps.

## Installation
```bash
pip install opencv-python numpy matplotlib pandas
