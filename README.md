
# FDS-HM1 – Image Filtering & Object Identification

This repository contains my group solutions for **Homework #1** of the course  
**“Fundamentals of Data Science and Laboratory” – Sapienza University of Rome**.

The homework is implemented in a single Jupyter notebook:

> `HW1_v3(completed).ipynb`

and covers four main blocks:

1. **1D & 2D image filtering**
2. **Edge detection & gradient-based features**
3. **Object identification via color & gradient histograms**
4. **Performance evaluation of a binary classifier**

---

## Repository Structure

- `HW1_v3(completed).ipynb` – main notebook with all code, plots, and written answers.
- `assets/` – auxiliary data (e.g. tabular dataset) used for the performance-evaluation section.
- `images/` – reference images used for filtering and edge-detection experiments.
- `model/` – “model” images for the object-identification task.
- `query/` – “query” images to be matched against the model set.

*(Folders and file names follow the original homework template provided by the course staff.)*

---

## 1. Image Filtering (Question 1)

**Goal:** understand convolution and filtering in 1D and 2D.

Main steps:

- Implement 1D moving-average filters from scratch and analyze:
  - effect of **filter size** on noise reduction vs detail preservation;
  - denoising performance on synthetic noisy signals.
- Implement 2D filters for images:
  - construction of **Gaussian kernels** with different sizes and σ;
  - comparison between **separable** and **non-separable** filters;
  - visual analysis of smoothing strength and information loss.

Technologies: `numpy`, `scipy.ndimage`, `matplotlib`.

---

## 2. Gradients & Edge Detection (Question 2)

**Goal:** extract edges and local structure using derivative filters.

Main steps:

- Implement first-order derivative filters (e.g. Sobel-like `dx` and `dy`).
- Compute:
  - gradient **magnitude** and **orientation**;
  - edge maps on grayscale images.
- Implement and analyze the **Laplacian of Gaussian (LoG)** filter:
  - discussion of separability;
  - comparison between LoG and Gaussian smoothing + derivatives;
  - qualitative evaluation of edge localization vs noise sensitivity.

Technologies: `numpy`, `scipy.signal`, `scikit-image`, `matplotlib`.

---

## 3. Object Identification with Histograms (Question 3)

**Goal:** recognize which model image corresponds to each query image using hand-crafted features.

Main steps:

- Implement from scratch a 3D **joint RGB color histogram** (re-implementing `numpy.histogramdd`).
- Construct **gradient-based histograms** over `(dx, dy)` to capture edge-orientation statistics.
- Compare **distance metrics** between histograms:
  - intersection
  - \(L_2\)
  - \(\chi^2\)
- Use these distances to match query images to model images and discuss:
  - robustness of color vs gradient histograms to **illumination changes**;
  - strengths/weaknesses of each distance metric.

Technologies: `numpy`, `opencv-python`, `Pillow`, `matplotlib`.

---

## 4. Performance Evaluation (Question 4)

**Goal:** evaluate a binary classifier using different thresholds and metrics.

Main steps:

- Train a **logistic regression** model on a provided dataset.
- For thresholds in \([0, 1]\):
  - convert predicted probabilities into class labels;
  - compute accuracy, precision, recall, F1-score, specificity, etc.
- Analyze how metrics change as the threshold varies:
  - trade-off between precision and recall;
  - impact on model behaviour in imbalanced-class settings.
- Visualize the results and discuss which thresholds are preferable under different application requirements.

Technologies: `pandas`, `scikit-learn`, `matplotlib`.

---

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/robertomagno1/FDS-HM1.git
   cd FDS-HM1
````

2. **Create and activate a Python environment** (optional but recommended)

   ```bash
   python -m venv .venv
   source .venv/bin/activate     # on Windows: .venv\Scripts\activate
  ```

3. **Install dependencies**

   ```bash
   pip install numpy pandas matplotlib scipy scikit-image scikit-learn opencv-python pillow
   ```

4. **Launch Jupyter**

   ```bash
   pip install notebook
   jupyter notebook
   ```

   Then open `HW1_v3(completed).ipynb` and run the cells from top to bottom.

The notebook is self-contained: each section includes markdown explanations, code, and visualizations of the results.

---

## Acknowledgements

The assignment and base notebook were provided as part of the
**Fundamentals of Data Science and Laboratory** course at *Sapienza University of Rome*.
All implementations and written answers in this repository are my own (unless otherwise stated).

