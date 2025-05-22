# Scene Change Detection Using SVD and Pattern Matching

This project implements a video shot boundary detection system using a custom Singular Value Decomposition (SVD) implementation combined with Total Absolute Difference (TAD) and pattern matching, inspired by the method proposed by Lu and Shi (2013). The system detects significant scene transitions in videos by analyzing frame differences and verifying them with SVD-based features.

## Features
- **Frame Extraction**: Extracts video frames using OpenCV and converts them to grayscale for efficient processing.
- **Total Absolute Difference (TAD)**: Computes TAD between consecutive frames to identify potential scene transitions.
- **Custom SVD Implementation**: Uses the Jacobi method to decompose frame matrices and extract singular values as features.
- **Transition Verification**: Confirms candidate transitions by calculating the Euclidean distance between singular values of adjacent frames.
- **Visualization**: Generates plots (e.g., TAD over time, pixel difference heatmaps) and saves transition frames as images.
- **Output**: Logs detected transition frame numbers in a text file and saves TAD values in a CSV file for analysis.

## Methodology
The project follows these steps:
1. **Frame Extraction**: Videos are read frame-by-frame using OpenCV, and frames are converted to grayscale.
2. **TAD Computation**: Calculates the Total Absolute Difference (TAD) between consecutive frames using the formula:
   \[
   TAD(F_i, F_{i+1}) = \sum |F_i - F_{i+1}|
   \]
   High TAD values indicate potential scene transitions.
3. **Thresholding**: Applies a statistical threshold (\(\mu + 3\sigma\)) based on the mean (\(\mu\)) and standard deviation (\(\sigma\)) of TAD values to identify candidate transitions.
4. **SVD Decomposition**: Implements SVD manually using the Jacobi method to decompose each frame matrix \(A\) into \(A = U \Sigma V^T\). Top singular values are used as features.
5. **Transition Verification**: Computes the Euclidean distance between singular values of adjacent frames to confirm transitions.
6. **Output and Visualization**: Saves candidate transition frames as images, logs frame numbers in a text file, and generates plots like TAD over time and pixel difference heatmaps.

## Installation
To run this project, you need Python 3.7+ and the following dependencies:
- OpenCV (`opencv-python`)
- NumPy
- Matplotlib
- Pandas

Install the dependencies using pip:
```bash
pip install opencv-python numpy matplotlib pandas
```

## Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/scene-change-detection.git
   cd scene-change-detection
   ```
2. Place your input video file (e.g., `video1.mp4`) in the project directory.
3. Run the main script:
   ```bash
   python main.py --video video1.mp4
   ```
4. The script will:
   - Extract frames and compute TAD values.
   - Apply SVD to verify transitions.
   - Save transition frames as images in an `output/` directory.
   - Log transition frame numbers in `transitions.txt`.
   - Save TAD values in `tad_values.csv`.
   - Generate visualizations (e.g., TAD plot, heatmaps).

## Sample Results
The system was tested on two video samples, detecting transitions at frames 149, 299, 449, 621, and 747 for `video1.mp4`. Key outputs include:
- **TAD Plot**: Shows sharp jumps at transition points.
- **Transition Frames**: Saved as individual images (e.g., `frame_149.jpg`).
- **Heatmaps**: Visualizes pixel differences at transitions (e.g., for frame 621).
- **Text Log**: Lists detected transition frame numbers.
- **CSV File**: Contains TAD values for all frames.

## Dependencies
- Python 3.7+
- OpenCV (`opencv-python>=4.5.0`)
- NumPy (`numpy>=1.19.0`)
- Matplotlib (`matplotlib>=3.3.0`)
- Pandas (`pandas>=1.1.0`)

## Limitations
- The system excels at detecting abrupt scene cuts but may miss gradual transitions (e.g., fades or zoom-outs).
- High motion or noise (e.g., flashing lights) can lead to false positives.
- Future improvements could include adaptive thresholding for diverse video types.

## References
- Z.-M. Lu and Y. Shi, "Fast video shot boundary detection based on SVD and pattern matching," *IEEE Transactions on Image Processing*, vol. 22, no. 12, pp. 5136-5145, 2013.

## Contact
For questions or suggestions, contact Ahsen Beyza Özkul at [ozkula21@itu.edu.tr](mailto:ozkula21@itu.edu.tr).