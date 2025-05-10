# **AI-assisted Character Animation Project**

## **1. Project Overview**

This project explores the integration of **generative AI models** (e.g., ChatGPT, Midjourney, DALL·E) with **traditional computer graphics pipelines** to automatically create **2D character animations**. By combining **image generation**, **skeleton estimation**, **mesh generation**, and **as-rigid-as-possible deformation**, we demonstrate a mixed-reality workflow that turns static drawings into dynamic animations.

## **2. Assets and Data**

* **Character Images**: Generated via **DALL·E** prompts or provided by users.
* **Pretrained Models**: Used for **segmentation mask** prediction and **joint estimation** in the Animated Drawings pipeline.

## **3. Methodology and Pipeline**

The animation pipeline consists of the following stages:

1. **Image Generation & Preprocessing**

   * Use **DALL·E** (or Midjourney) to produce character artwork.
   * Obtain a **segmentation mask** and **joint positions** via a pretrained Animated Drawings model.

2. **Mesh Construction**

   * Sample boundary points with **Poisson Disk Sampling**.
   * Perform **Delaunay triangulation** to generate a 2D mesh.

3. **Texture Mapping**

   * Project the original character artwork onto the mesh as a **texture layer**.

4. **Deformation & Animation**

   * Apply **As-Rigid-As-Possible (ARAP)** deformation to the mesh for smooth transformations.
   * Use the **characterMotion** object to update joint-driven deformations across frames.

5. **Video Assembly**

   * Render each deformed frame into an image sequence.
   * Combine frames into a final animation using **FFmpeg**.

## **4. Implementation and Dependencies**

All code is provided in the **`W6_track2-animatedDrawings.ipynb`** notebook. Install the required Python packages via:

```bash
pip install -r requirements.txt
```

## **5. Usage**

1. **Prepare Input**: Place your character image in the `assets/` directory or generate one with DALL·E.
2. **Notebook Execution**: Open `W6_track2-animatedDrawings.ipynb` and run all cells.
3. **Adjust Parameters**: Modify sampling density, ARAP weight, or playback speed as needed.
4. **Export Video**: The final animation is saved as `output/animation.mp4`.

## **6. Results and Discussion**

* Successfully animated static 2D characters with **plausible joint movements** and **smooth mesh deformations**.
* **Texture overlays** sometimes exhibit minor distortion near joints; future work can address improved UV mapping.
* Demonstrates the power of combining **AI-generated assets** with **classical graphics algorithms**.

## **7. Improvements and Future Work**

* Enhance **texture stability** by refining **UV parameterization**.
* Integrate **real-time camera-based skeleton tracking** to drive animations interactively.
* Extend the pipeline to **3D character meshes** for richer animations.

## **8. Team Members**

* **Weizhao Wang**
* **Fulin Jiang**
* **Kunwei Song**

## **9. References**

1. Smith, H. J., et al. "A Method for Automatically Animating Children's Drawings of the Human Figure." *arXiv preprint arXiv:2303.12741* (2023).
2. Turja, S. D., et al. "Shapes2Toon: Generating Cartoon Characters from Simple Geometric Shapes." *AICCSA 2022*.
3. Huang, Q., et al. "Arapreg: An as-rigid-as-possible regularization loss for learning deformable shape generators." *CVPR 2021*.
4. ETH Zürich. "As-Rigid-As-Possible Surface Modeling." [IGL Project](https://igl.ethz.ch/projects/ARAP/)

## **10. Acknowledgments**

* Generative AI support from **ChatGPT**, **Midjourney**, and **DALL·E**.
* Inspired by the **Animated Drawings** framework and ARAP deformation techniques.
