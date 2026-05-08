# GarmentFitAlgorithms
Waist visualization, data sanitization, and best‑fit garment search

# Contents
 # Question 1: Waist Circumference Visualization #

This project computes waist circumference from a 3D human body mesh using mesh slicing techniques.

## Features

- Loads a 3D `.obj` human mesh
- Slices the mesh at a selected waist height
- Extracts contour loops from the mesh intersection
- Computes waist circumference
- Visualizes the waist slice on the 3D body mesh
- Saves the final visualization as a PNG image (`waist_slice.png`)

## Technologies

- Python
- Trimesh
- NumPy
- Matplotlib

## Output

- Waist circumference value
- 3D visualization with highlighted waist contour
- Output image file: `waist_slice.png`

# Question 2: Measurement Normalization & Outlier Detection Engine

This project implements a data sanitization system for user body measurements.

## Features

- Converts measurements to centimeters
- Detects unrealistic body proportions
- Flags possible outliers
- Estimates missing measurements using body ratio constants

## Technologies

- Python
- Object-Oriented Programming (OOP)

## Example Output

- Normalized measurements
- Validation issues
- Estimated missing values
      
# Question 3: Best-Fit Multi-Constraint Search Algorithm
  This project implements a garment recommendation system that identifies the Top 3 best-fitting garments based on user body measurements.

## Features

- Creates a synthetic garment database with Chest, Waist, and Hip measurements
- Applies asymmetric penalty logic for garment fitting
- Uses weighted scoring for measurement importance
- Computes fit confidence scores
- Returns the Top 3 best-fitting garments

## Technologies

- Python
- NumPy

## Output

- Top 3 garment recommendations
- Garment IDs
- Fit confidence scores

### Scaling Strategy for Large Databases
The prototype uses a linear scan, which is efficient for ~100 garments but not for millions.  
For scaling to 1M+ garments, the algorithm can be optimized using:

- **KD‑Tree / Ball‑Tree** → Index garments as vectors (Chest, Waist, Hip) for fast nearest‑neighbor queries  
- **Spatial Index (R‑Tree)** → Efficient for range queries on measurements  
- **Vector Database (e.g., FAISS, Pinecone)** → Store garment specs as embeddings and perform sub‑linear similarity search  

These methods reduce search time from O(n) linear scans to sub‑linear queries, making large‑scale garment fit search practical.

## How to Run
- Open each `.ipynb` notebook in Google Colab
- Run cells step by step
- Outputs include validation checks, fit scores, and visualizations
