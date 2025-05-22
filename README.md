# Scene Change Detection Using SVD and Pattern Matching

This project implements a video shot boundary detection system using a custom Singular Value Decomposition (SVD) implementation combined with Total Absolute Difference (TAD) and pattern matching, inspired by the method proposed by Lu and Shi (2013). The system detects significant scene transitions in videos by analyzing frame differences and verifying them with SVD-based features.

## Features

- **Frame Extraction:** Extracts video frames using OpenCV and converts them to grayscale for efficient processing.
- **Total Absolute Difference (TAD):** Computes TAD between consecutive frames to identify potential scene transitions.
- **Custom SVD Implementation:** Uses the Jacobi method to decompose frame matrices and extract singular values as features.
- **Transition Verification:** Confirms candidate transitions by calculating the Euclidean distance between singular values of adjacent frames.
- **Visualization:** Generates plots (e.g., TAD over time, pixel difference heatmaps) and saves transition frames as images.
- **Output:** Logs detected transition frame numbers in a text file and saves TAD values in a CSV file for analysis.

## Methodology

The project follows these steps:

1. **Frame Extraction:**  
   Videos are read frame-by-frame using OpenCV, and frames are converted to grayscale.

2. **TAD Computation:**  
   Calculates the Total Absolute Difference (TAD) between consecutive frames using the formula:  
   \[
   \text{TAD}(F_i, F_{i+1}) = \sum |F_i - F_{i+1}|
   \]  
   High TAD values indicate potential scene transitions.

3. **Thresholding:**  
   Applies a statistical threshold \((\mu + 3\sigma)\) based on the mean \((\mu)\) and standard deviation \((\sigma)\) of TAD values to identify candidate transitions.

4. **SVD Decomposition:**  
   Implements SVD manually using the Jacobi method to decompose each frame matrix \(A\) into  
   \[
   A = U \Sigma V^T
   \]  
   Top singular values are used as features.

5. **Transition Verification:**  
   Computes the Euclidean distance between singular values of adjacent frames to confirm transitions.

6. **Output and Visualization:**  
   Saves candidate transition frames as images, logs frame numbers in a text file, and generates plots like TAD over time and pixel difference heatmaps.

## Installation

To run this project, you need **Python 3.7+** and the following dependencies:

- OpenCV (`opencv-python`)
- NumPy
- Matplotlib
- Pandas

Install the dependencies using pip:

```bash
pip install opencv-python numpy matplotlib pandas
# Clone the repository
git clone https://github.com/your-username/scene-change-detection.git
cd scene-change-detection

# Place your input video file (e.g., video1.mp4) in the project directory.

# Run the main script:
python main.py --video video1.mp4
