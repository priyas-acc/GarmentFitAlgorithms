# GarmentFitAlgorithms
Waist visualization, data sanitization, and best‑fit garment search

## Contents
- **Question 1: Waist Circumference Visualization**
  - Notebook: `Question 1.ipynb`
  - Implements a function (`calculate_circumference`) that:
    - Intersects a 3D mesh at a given Z‑height
    - Collects intersection points and builds a convex hull
    - Calculates the loop circumference from hull edges
  - Includes a visualization function (`visualize_mesh_with_slice`) that overlays the slice on the 3D mesh
  - Demonstrates outputs at multiple Z‑levels and prints circumference values
  - Final output: Waist circumference at a chosen height with a plotted slice (`waist_slice.png`)

- **Question 2: Data Sanitizer Engine**
  - Notebook: `Question 2.ipynb`
  - Defines a `DataSanitizer` class with three main methods:
    - **normalize_units()** → Converts measurements to centimeters (values ≤ 100 assumed inches, multiplied by 2.54; larger values treated as already in cm)
    - **validate_proportions()** → Checks logical consistency of measurements (e.g., waist not larger than height, chest ≥ 30% of height, hip within 40–70% of height)
    - **estimate_missing()** → Fills missing values based on height (e.g., ArmLength = 35% of height, LegLength = 50% of height)
  - Demonstrates usage with a sample dataset (`user_data`) and prints:
    - Normalized values
    - Validation issues
    - Final dataset with estimated missing values
      
- **Question 3: Best-Fit Multi-Constraint Search Algorithm**
  - Notebook: `Question 3.ipynb`
  - Creates a synthetic garment database (`garments_db`) with random Chest, Waist, and Hip values
  - Defines:
    - **penalty()** → Returns ∞ if garment is smaller than user measurement (unwearable), otherwise difference
    - **fit_score()** → Combines penalties with weighted scoring (Chest penalty ×2, Waist ×1, Hip ×1) and outputs a confidence score
  - Performs a linear scan across garments, calculates scores, and selects the **Top 3 best fits**
  - Prints garment IDs and fit confidence values

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
