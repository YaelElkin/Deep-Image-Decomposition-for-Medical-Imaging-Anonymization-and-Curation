# Deep Image Decomposition for Medical Imaging Anonymization and Curation
Official implementation of the WACV 2026 paper **"Deep Image Decomposition for Medical Imaging Anonymization and Curation"**.


## 🩺 Overview
Medical scans often include patient identifiers and clinical annotations that must be removed prior to data sharing or use in downstream machine-learning pipelines. Reliable removal of these non-imaging artifacts is essential for preserving patient privacy, reducing bias, and improving data quality. However, this crucial curation step is frequently overlooked or handled heuristically.

This repository provides a deep learning framework that **automatically detects and removes overlaid text, markers, and other non-imaging elements** from clinical scans while restoring the underlying image content.


## 🔍 Method
Our approach consists of two main components:

### **1. Detection Module**
A dedicated network localizes non-imaging regions such as text, labels, and graphical markers.  
Explainable-AI (XAI) maps from this module are used to guide the artifact-removal stage.

### **2. Dual-Generator Image Decomposition**
We introduce a dual-generator, unsupervised decomposition architecture:
- **Image Generator** reconstructs clean imaging content.  
- **Non-Imaging Generator B** predicts the non-imaging components (overlays, text, markers).  

This architecture allows the model to separate imaging from non-imaging information **without requiring pixel-wise supervision**.

Unlike conventional inpainting methods, our model bypasses explicit segmentation by combining detection-guided masking with decomposition-based restoration.


## 📊 Results
We evaluate our method on **three datasets** (one MRI and two ultrasound) from both public and private sources.

Key findings include:
- High visual quality validated through a **Turing-test-style study**.  
- Strong quantitative results on SSIM, PSNR, and FID.  
- Downstream tasks (classification and segmentation) show substantial performance gains when trained on curated data.  

## 📜 Citation

If you use this code or dataset, please cite our paper:

```latex
@inproceedings{elkin2026deep,
  title={Deep Image Decomposition for Medical Imaging Anonymization and Curation},
  author={Elkin, Yael and Ben-Arie, Gal and Riklin-Raviv, Tammy},
  booktitle={Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
  year={2026}
}
```

## 📧 Contact
For questions or issues, please contact:
Tammy Riklin-Raviv – rrtammy@bgu.ac.il
