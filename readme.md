# Face Animatable Avatar Generation Benchmark Dataset

A Comprehensive Benchmark for Face Animatable Avatar Generation

<p align="center">
  <br>
  <em>A Comprehensive Benchmark for Evaluating Face Animatable Avatar Generation</em>
  <br>
  <a href="#" target="_blank">GitHub</a> | 
  <a href="#" target="_blank">Paper</a> |
  <a href="#" target="_blank">Dataset</a>
</p>

## 📖 Introduction

The Face Animatable Avatar Generation Benchmark Dataset addresses a gap in evaluating face animatable avatar generation systems. Creating realistic, fully animatable face avatars from a single static expression remains challenging, as existing methods struggle to accurately capture:

* Subtle facial expressions
* Dynamic background changes
* Consistent identity preservation

Our benchmark is motivated by two primary needs:

1. Current metrics fail to adequately capture the complexity involved in generating face animatable avatars from a single image
2. A dedicated benchmark dataset can offer valuable insights to drive progress in high-quality face animatable avatar generation

The Face Animatable Avatar Generation Dataset is a fully open-source benchmark specifically designed for face animatable avatar generation. It provides comprehensive labels and a versatile evaluation framework to facilitate rigorous assessment of high-quality face animatable avatar generation.

## 🎬 Key Features

Our benchmark provides several compelling features:

* **Specialized Face Evaluation** : Focused metrics specifically designed for facial animation assessment
* **Detailed Multi-Modal Annotations** : Comprehensive labels that facilitate high-quality face animatable avatar generation by providing fine-grained facial guidance
* **Versatile Evaluation Framework** : Enables rigorous assessment of face animatable avatar quality across multiple dimensions
* **Specialized Metrics** : Both objective metrics (FID, E-FID, FVD, PSNR, SSIM, CSIM) and subjective metrics for holistic evaluation
* **Standardized Methodology** : Consistent testing protocol for fair comparison between different face animation methods

## 📊 Evaluation Framework

Our benchmark provides multiple specialized evaluation metrics:

### Objective Metrics

* **FID (Fréchet Inception Distance)** : Measures visual quality similarity
* **E-FID (Edge-FID)** : Evaluates structural consistency using edge maps
* **FVD (Fréchet Video Distance)** : Assesses temporal coherence in generated videos
* **PSNR (Peak Signal-to-Noise Ratio)** : Quantifies reconstruction accuracy
* **SSIM (Structural Similarity Index)** : Measures perceptual similarity
* **CSIM (Cosine Similarity)** : Evaluates feature-level similarity

### Subjective Consistency Metrics

Six dimensions of subjective evaluation:

* Subject Consistency
* Background Consistency
* Motion Smoothness
* Dynamic Degree
* Aesthetic Quality
* Imaging Quality

## 🚀 Getting Started

### Installation

This benchmark uses MMPose for facial keypoint detection. For detailed installation instructions, please refer to the [MMPose installation guide](https://mmpose.readthedocs.io/en/latest/installation.html).

We recommend following these steps to set up your environment:

#### Prerequisites

Our benchmark requires Python 3.7+, CUDA 9.2+ and PyTorch 1.8+.

**Step 0.** Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) from the official website.

**Step 1.** Create a conda environment and activate it:

```bash
conda create --name face-avatar python=3.8 -y
conda activate face-avatar
```

**Step 2.** Install PyTorch following official instructions:

For GPU platforms:

```bash
conda install pytorch torchvision -c pytorch
```

For CPU-only platforms:

```bash
conda install pytorch torchvision cpuonly -c pytorch
```

**Step 3.** Install MMEngine and MMCV using MIM:

```bash
pip install -U openmim
mim install mmengine
mim install "mmcv>=2.0.1"
```

**Step 4.** Install MMPose:

```bash
mim install "mmpose>=1.0.0"
```

**Step 5.** Clone the repository and install dependencies:

```bash
# Clone the repository
git clone https://github.com/yourusername/face-avatar-benchmark.git
cd face-avatar-benchmark
```

#### Alternative: Manual Installation from Source

If you prefer to install MMPose from source (recommended for development):

```bash
git clone https://github.com/open-mmlab/mmpose.git
cd mmpose
pip install -v -e .
# "-v" means verbose, and "-e" means installing in development mode
cd ..
```

#### Verify the Installation

To verify that MMPose and other dependencies are correctly installed:

```bash
# Enter Python interpreter
python

# Try importing key packages
>>> import torch
>>> import mmpose
>>> import mmcv
>>> import cv2
>>> print(torch.__version__)
>>> print(mmpose.__version__)
```

For troubleshooting, please refer to the [MMPose installation guide](https://mmpose.readthedocs.io/en/latest/installation.html).

### Dataset Structure

```
face-avatar-benchmark/
├── gt_test/                  # Ground truth test videos
├── face_images/              # Extracted face image frames
├── face_videos/              # Face region videos
├── FIDres/                   # FID evaluation results
├── SCres/                    # Subjective Consistency results
└── evaluation/               # Evaluation scripts
```

### Running Evaluations

```bash
# Process face region extraction
python process_face_videos.py

# Calculate FID, E-FID, FVD, PSNR, SSIM metrics
python FID_calculate.py

# Calculate Subjective Consistency scores
python SC_calculate.py
```

## 📊 Benchmark Results

Performance comparison of various methods on our face animatable avatar benchmark:

| Method |   SC   |   BC   |   MS   |   DD   |   AQ   |   IQ   |  FID  |   FVD   | SSIM | PSNR | E-FID | CSIM |
| :-----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :-----: | :---: | :---: | :----: | :---: |
|  Step  | 65.06% | 74.04% | 63.12% | 14.91% | 28.18% | 39.40% | 300.98 | 1811.92 | 0.372 | 13.54 | 339.18 | 0.736 |
|   Hun   | 55.07% | 68.05% | 56.78% | 4.15% | 21.26% | 34.19% | 291.21 | 1351.71 | 0.322 | 14.47 | 347.24 | 0.787 |
|   Wan   | 66.51% | 72.26% | 63.40% | 25.12% | 25.09% | 33.68% | 254.03 | 1591.22 | 0.417 | 16.99 | 273.97 | 0.866 |
|  OpenS  | 52.34% | 63.55% | 49.74% | 7.69% | 19.76% | 30.90% | 275.50 | 1221.85 | 0.388 | 16.29 | 359.85 | 0.863 |
|  Ha3/w  | 14.92% | 15.73% | 14.66% | 7.21% | 5.79% | 6.98% | 425.82 | 2794.85 | 0.127 | 6.75 | 451.76 | 0.385 |
| Ha3/wo | 12.23% | 15.15% | 12.15% | 0.00% | 2.99% | 4.60% | 720.22 | 3255.19 | 0.010 | 0.89 | 492.67 | 0.065 |
| ecv2/w | 14.79% | 18.16% | 12.73% | 2.42% | 5.71% | 8.49% | 437.27 | 2651.92 | 0.139 | 6.88 | 439.92 | 0.401 |
| ecv2/wo | 8.29% | 9.27% | 8.16% | 0.21% | 5.69% | 6.29% | 801.27 | 3047.27 | 0.027 | 1.249 | 513.58 | 0.062 |

*Legend: SC: Subject Consistency, BC: Background Consistency, MS: Motion Smoothness, DD: Dynamic Degree, AQ: Aesthetic Quality, IQ: Imaging Quality, FID: Fréchet Inception Distance, FVD: Fréchet Video Distance, SSIM: Structural Similarity Index Measure, PSNR: Peak Signal-to-Noise Ratio, E-FID: Enhanced Fréchet Inception Distance, CSIM: Cosine Similarity. ↑ indicates higher is better, ↓ indicates lower is better.*

## 🔧 Technical Details

### FID_calculate.py

This script calculates objective metrics for face animation evaluation:

* Extracts frames from generated and ground truth face videos
* Computes FID using InceptionV3 features
* Calculates E-FID using edge maps for facial structure consistency
* Measures FVD using I3D network for temporal coherence
* Calculates PSNR, SSIM, and CSIM for face-specific quality assessment

### SC_calculate.py

This script processes subjective consistency scores for face animation:

* Filters out unmatched face videos
* Calculates average scores across facial animation dimensions
* Generates summary statistics for face animation quality

### process_face_videos.py

This script handles face region extraction and processing:

* Uses DWPose-onnx for facial keypoint detection
* Processes video frames and extracts facial landmarks
* Creates cropped face videos for specialized face animation evaluation
* Ensures consistent face region boundaries across frames

## 📝 Citation

If you find our work useful in your research, please consider citing.

## 🙏 Acknowledgements

We extend our gratitude to:

* [VBench](https://github.com/Vchitect/VBench) for their Comprehensive Benchmark Suite for Video Generative Models
* [DWPose-onnx](https://github.com/IDEA-Research/DWPose) for their facial keypoint detection framework
* Our research institution for providing computational resources
* Face animation research community contributors

## 📄 License

This project is licensed under the [MIT License](https://demo.fuclaude.com/chat/LICENSE).
