# Photogrammetry and Gaussian Splatting on Lunar Apollo 17 Imagery
# Report

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

Photogrammetry enables the reconstruction of three-dimensional models from two-dimensional images, providing valuable tools for planetary science. The Apollo 17 mission produced high-resolution photographs suitable for 3D modeling. Recent advances, such as Gaussian Splatting, allow for the rendering of novel views and improved scene understanding. This section focuses on creating a 3D model from original imagery and evaluating view recovery quality.

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


**Interpretation**

The results from Part A demonstrate that the photogrammetric model reconstructed using the original 15 Apollo 17 images achieved a reasonable level of structural and visual fidelity. The average SSIM value of 0.6503 suggests a moderate to high degree of perceptual similarity between the original images and the reconstructed views, indicating that the overall structure of the lunar surface was preserved effectively during the modeling process. The PSNR value of 22.41 dB reflects acceptable pixel-level consistency, although minor discrepancies were expected due to variations in image alignment, lighting conditions, and texture mapping.

Visually, the textured mesh produced in Metashape displayed accurate geometric features and realistic textures, confirming the quality of the dense point cloud and mesh reconstruction processes. However, some areas of the model exhibited gaps or reduced detail, primarily in regions with limited image coverage or insufficient overlap between viewpoints. These limitations highlight the challenges of reconstructing complete and highly detailed 3D models from a limited set of images and provided the motivation for generating additional views using Gaussian Splatting in Part B.

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
![Screenshot 2025-05-07 151231](https://github.com/user-attachments/assets/7cc50f5e-5a9f-4eea-b55a-889731ddc129)



These images illustrate the augmented photogrammetric model developed in Part B, which includes the original 15 Apollo 17 images plus 10 novel views generated using Gaussian Splatting. The model shows improved surface coverage, fewer gaps, and enhanced texture mapping compared to the Part A results.
![WhatsApp Image 2025-05-07 at 2 26 45 PM (1)](https://github.com/user-attachments/assets/dfa827b2-8dad-4eb3-a349-7057d78f29f4)
![WhatsApp Image 2025-05-07 at 2 26 45 PM](https://github.com/user-attachments/assets/3ce72593-0c24-472e-9684-719e4029b412)







