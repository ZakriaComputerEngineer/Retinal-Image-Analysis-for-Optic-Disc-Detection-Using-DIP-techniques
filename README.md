# Retinal-Image-Analysis-for-Optic-Disc-Detection-Using-DIP-techniques
This project focuses on the extraction and analysis of retinal fundus images to locate the optic disc, which plays a crucial role in diagnosing retinal diseases. The problem involves applying spatial enhancement, image filtering, and connected component analysis for effective detection.

![image](https://github.com/user-attachments/assets/a034ddee-0788-4d55-88dd-91cfc2e82297)

![image](https://github.com/user-attachments/assets/89addc82-b256-4c00-b06d-1392ff78e4d3)

Largest connected component: Label=1, Area=37262, Centroid=[ 721 1045]

---

## Problem Description  

Fundus images are digital representations of the human retina. Key features include the **optic disc**, **vessels**, and **fovea (macula)**. The task was to:  

1. **Extract bright regions** from the images, focusing on identifying the optic disc.  
2. **Identify and mark the optic disc location** while handling false positive regions caused by exudates in abnormal cases.  
3. **Calculate the error** between the actual and detected optic disc locations using **Euclidean distance**.  

---

## Dataset  

The dataset consists of 50 fundus images, each with:  
- Original colored images  
- Corresponding blood vessel maps  
- Ground truth optic disc coordinates  

Access the dataset [here](https://drive.google.com/drive/folders/1DxmL9I2772qTCYwlbMk1KpKPtJb85o-H?usp=sharing).

---

## Methodology  

1. **Preprocessing:**  
   - Applied spatial transformations to enhance bright regions in the images.  
   - Utilized image filtering for noise reduction.  

2. **Optic Disc Detection:**  
   - Identified bright regions using thresholding techniques.  
   - Filtered false positives by analyzing the blood vessel map, as vessels originate from the optic disc.  

3. **Error Calculation:**  
   - Computed the Euclidean distance between the ground truth and detected optic disc coordinates.  

---

## Results  

tables (csv files) given that contains the results in this form:

---

## **Running the Code**

1. **Clone the repository:**

   ```bash
   git clone <repo-url>
   cd <repo-name>
   ```

2. **Install Dependencies:**

   Ensure you have Python 3.x installed. Then, install the required libraries by running:

   ```bash
   pip install opencv-python numpy matplotlib tqdm
   ```

3. **Run the Code:**

   Open and run the code in a Jupyter notebook or directly in your Python environment.

   If you're using Jupyter, run:

   ```bash
   jupyter notebook Assignment-2.ipynb
   ```

   Alternatively, you can execute the Python script directly:

   ```bash
   python optic_disc_detection.py
   ```
---

### **Technique Overview**  

The technique involves a series of preprocessing and image analysis steps for detecting the optic disc in retinal fundus images. The flowchart illustrates a structured approach that includes spatial filtering, morphological operations, connected component analysis, and centroid extraction to compute errors against reference data.

![Flowchart](https://github.com/user-attachments/assets/059379eb-f614-463a-9554-a82c12450017)


1. **Start:**  
   The process begins with reading a directory of retinal fundus images and a CSV file containing ground truth coordinates for the optic disc.

2. **Input Fundus Folder Directory:**  
   The user provides a directory containing fundus images for processing.

3. **Image Read as Greyscale:**  
   Each fundus image is read in greyscale for efficient processing.

4. **Contrast Stretching:**  
   Enhances the contrast of the greyscale image to improve bright region detection.

5. **Input Kernel (5x5):**  
   A structuring element (kernel) of size 5x5 is used for morphological operations.

6. **Thresholding:**  
   Thresholding is applied to isolate bright regions from the background, which may include the optic disc.

7. **Erosion:**  
   Reduces noise by shrinking the bright regions.

8. **Dilation:**  
   Expands the remaining bright regions after erosion, enhancing the target features.

9. **8-Connectivity Connected Component Analysis (CCA):**  
   Identifies connected regions in the binary image using 8-connectivity to ensure all adjacent pixels are considered.

10. **Extract Largest Object by Stats Area:**  
   From the detected connected components, the largest object is selected, as it is most likely to represent the optic disc.

11. **Extract Centroids:**  
   The centroid coordinates of the largest detected region are computed.

12. **Input CSV File:**  
   A CSV file containing ground truth coordinates of the optic disc for each image is read.

13. **Calculate Errors:**  
   The Euclidean distance between the detected centroid and ground truth coordinates is computed for each image.

14. **Generate New CSV File with Results and Errors:**  
   The results, including detected centroids and computed errors, are saved in a new CSV file.

15. **Save CSV:**  
   The updated CSV file is saved for further analysis.

---
