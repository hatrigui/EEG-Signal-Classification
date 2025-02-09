# EEG-Based Seizure Detection

## Project Description

This project focuses on classifying EEG signals to detect epileptic seizures using machine learning and signal processing techniques. We utilized the **Bonn University EEG Dataset**, consisting of 5 classes (3 non-seizure and 2 seizure-related). The dataset was preprocessed to remove noise, normalize, and segment the signals into 1-second chunks. For feature extraction, we employed **Discrete Wavelet Transform (DWT)** using Haar, Daubechies (db4), and Symlet (Sym8) wavelets. We then applied **Principal Component Analysis (PCA)** to reduce the dimensionality while retaining 95% of the variance.

For classification, **Support Vector Machine (SVM)** with both **RBF** and **polynomial kernels** were used, with hyperparameters tuned via grid search. The model performance was evaluated using **accuracy**, **precision**, **recall**, and **F1-score**.

## Methodology

### Dataset
- **Bonn University EEG Dataset** with 5 classes:
  - **Non-seizure**: A (healthy eyes open), B (healthy eyes closed), C-D (epileptic interictal)
  - **Seizure**: E (epileptic ictal)
- Each sample contains 178 data points (1-second EEG segment).
- Balanced dataset with 12,000 samples: 9,600 non-seizure, 2,400 seizure.

### Preprocessing
- Noise removal using **filtering**, **Independent Component Analysis (ICA)**, and **wavelet denoising**.
- Data normalization and segmentation into 1-second chunks.
- Dataset balanced to address class imbalance.

### Feature Extraction
- **Discrete Wavelet Transform (DWT)** using Haar, Daubechies (db4), and Symlet (Sym8) wavelets.
- Frequency band decomposition to capture seizure-related patterns.

### Dimensionality Reduction
- **Principal Component Analysis (PCA)**: Retained 95% of variance, using 10 or 50 components.

### Classification
- **Support Vector Machine (SVM)** with **RBF** and **polynomial kernels**.
- Hyperparameters tuned via grid search (C, gamma).

### Evaluation Metrics
- **Accuracy**, **Precision**, **Recall**, and **F1-score**.

## Key Results

- **Wavelet and Kernel Performance**:
  - **RBF Kernel** outperformed the polynomial kernel across all wavelet types.
  - **Daubechies (db4)** with 50 PCA components achieved the highest scores:
    - **Accuracy**: ~95%
    - **Precision**: ~94%
    - **Recall**: ~93%
    - **F1-Score**: ~93%

- **Impact of PCA**: Using 50 components (vs. 10) improved model performance by retaining more discriminative features.

- **Wavelet Comparison**:
  - **Haar** and **db4** wavelets were most effective.
  - **Symlet (Sym8)** showed lower performance due to mismatched signal characteristics.

- **Class Balance**: Balanced dataset ensured no bias and reliable metrics.

## Conclusion

The combination of **DWT (db4)**, **PCA (50 components)**, and **SVM (RBF kernel)** provided an optimal solution for EEG-based seizure detection, achieving high accuracy (~95%). This method demonstrates the effectiveness of wavelet-based features and SVM in handling non-linear EEG patterns. Future work may explore deep learning architectures (e.g., CNNs, LSTMs) for enhanced performance and real-time deployment.

## Impact

This approach provides a robust framework for automated seizure detection, aiding clinicians in timely diagnosis and improving patient outcomes.
