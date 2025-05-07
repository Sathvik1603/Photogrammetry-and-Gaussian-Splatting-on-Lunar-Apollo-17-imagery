# Photogrammetry and Gaussian Splatting on Lunar Apollo 17 Imagery

**Student Name:** Sathvik Merugu  
**ASU ID:** 1235373752

---

## Abstract

- Integrated **photogrammetric modeling** and **Gaussian Splatting** to analyze Apollo 17 lunar imagery.
- **Part A**: Developed 3D textured mesh models from 15 original Apollo 17 photographs.
- Applied **Gaussian Splatting** to recover original views.
- Evaluated fidelity using **SSIM** and **PSNR**.
- **Part B**: Generated 10 novel views using Gaussian Splatting and added to photogrammetry dataset.
- Reprocessed augmented dataset to evaluate improvements.
- **Result**: Quantitative and qualitative analysis confirmed the effectiveness of Gaussian Splatting in enhancing photogrammetric reconstructions.

---

## Part A: Photogrammetry and Gaussian Splatting — Original Views

### Introduction

- **Photogrammetry**: Reconstructs 3D models from 2D images.
- Apollo 17 images offer high-resolution data for 3D modeling.
- **Gaussian Splatting**: Renders novel views and enhances scene understanding.

### Methodology

**Dataset**
- 15 high-resolution Apollo 17 images.
- Provided diverse viewpoints, overlap, and texture.

**Photogrammetry Processing (Agisoft Metashape)**
- **Image Import & Alignment**: Identified matching features, created sparse point cloud.
- **Dense Point Cloud Generation**: Built dense cloud; enabled point cloud confidence visualization.
- **Mesh Reconstruction**: Created 3D mesh of lunar surface geometry.
- **Texture Mapping**: Applied high-resolution textures for realism.

**Export for Gaussian Splatting**
- Exported images + camera parameters in **COLMAP** format for Nerfstudio compatibility.

**Gaussian Splatting (Nerfstudio)**
- Processed data using `ns-process-data colmap`.
- Trained Gaussian Splatting model: `ns-train gaussian-splatting`.
- Exported rendered images: `ns-export`.

**Similarity Metrics (SSIM & PSNR)**
- Used **Python** (`scikit-image` & `opencv-python`).
- Compared original images vs. slightly blurred versions.
- Established baseline SSIM & PSNR values.

### Results

- **SSIM**: 0.6 to 0.76 (**average 0.6503**).
- **PSNR**: 19.33 dB to 25.45 dB (**average 22.41 dB**).
- **Textured Mesh**: Accurate geometry & realistic textures.
- **Gaussian Splatting Views**: Closely matched original images.

---

## Part B: Photogrammetry Enhancement Using Gaussian Splatting-Derived Views

### Methodology

**Novel View Generation (Gaussian Splatting)**
- Chose **10 new camera poses** for underrepresented lunar areas.
- Rendered novel views using trained Gaussian Splatting model.

**Photogrammetry with Augmented Dataset**
- Combined **15 original + 10 splatted views** (**25 images total**).
- Re-imported into Agisoft Metashape.
- Repeated photogrammetry workflow:
  - Photo alignment.
  - Dense cloud generation.
  - Mesh reconstruction.
  - Texture mapping.

**Model Quality Evaluation**
- **Qualitative**: Visual inspection of original vs. augmented models.
- **Quantitative**: SSIM & PSNR metrics, mesh density, texture continuity.

### Results

**Qualitative Improvement**
- Augmented model had better surface coverage.
- All 25 images aligned without significant errors.
- Fewer gaps and improved texture mapping.
- Enhanced details in previously uncovered areas.

**Quantitative Metrics**
- **SSIM** increased from **0.6503 ➔ 0.858**.
- **PSNR** improved from **22.41 dB ➔ 26.52 dB**.

**Visual Comparison**
- Denser mesh structure.
- More uniform texture mapping.
- Clear improvement over the original model.

### Figures
These images show the 3D mesh and camera alignments for Part A photogrammetry using Apollo 17 images.

![Screenshot 2025-05-07 132013](https://github.com/user-attachments/assets/4a2c31aa-90b7-4f93-a68c-ca171cc2ac1e)
![Screenshot 2025-05-07 131959](https://github.com/user-attachments/assets/789e852d-3928-43f8-9e64-40a4f05e947f)
![Screenshot 2025-05-07 124813](https://github.com/user-attachments/assets/12259af2-d213-447e-8a6b-1eb96b2ff15f)
![Screenshot 2025-05-07 151231](https://github.com/user-attachments/assets/677fc4a5-7226-470e-8c45-f66c9654ce75)





