# Jewelry Design

## Design Objectives

- **Shape**: Generate a variety of creative jewelry silhouettes or 3D forms.
- **Pattern**: Overlay those shapes with rich surface materials—metal finishes, gemstone patterns, filigree, organic motifs, etc.—to add visual depth.

## Image Dataset for Texture Design

1. **Scrape Texture Images from Pinterest**
   - Source: <https://www.pinterest.com/>
   - Notebook: `Pinterest_Scraping.ipynb`
   - Output Folder: `Pinterest_dataset`
2. **Generate Additional Textures via OpenAI API**
   - Notebook: `openAI_api.ipynb`
3. **Generate Complex Pattern Images**
   - Output Folder: `texture`
   - Notebook: `analyse_round1.ipynb`

## Model Dataset for Shape Design

1. **Scrape 3D Models from Sketchfab**
   - Source: <https://sketchfab.com/>
   - Notebook: `gltf-stl.ipynb`
2. **3D DCGAN Training**
   - Notebook: `DCGAN_generate.ipynb`
   - *Note: Performance is unsatisfactory and computationally intensive.*

## Image Dataset for Shape Design

1. **Scrape Jewelry Images from Unsplash**
   - Source: <https://unsplash.com/>
   - Notebook: `Unsplash_scraping.ipynb`
   - Output Folders: `bracelet`, `earrings`, `jewelry`, `ring`, `necklace`
2. **Clean Images (Background Removal)**
   - Tool: `rembg.remove` (U²-Net)
   - Notebook: `background_removing.ipynb`
   - Output Folders: `bracelet_filter`, `earrings_filter`, `jewelry_filter`, `ring_filter`, `necklace_filter`
3. **Filter Out Images with Human Body Parts**
   - Method: OpenCV
   - Notebook: `filter1.ipynb`
   - Output Folders: `bracelet_filter_keep`, `earrings_filter_keep`, `jewelry_filter_keep`, `ring_filter_keep`, `necklace_filter_keep`
   - Combined Folder: `image`
4. **Cluster Images (KMeans)**
   - Output Folder: `clusters`
   - Notebook: `scrape-generate_compare.ipynb`
5. **Generate Jewelry Variations via OpenAI API**
   - Notebook: `picture_generation.ipynb`
   - Output Folder: `generated`
6. **Generate 3D Models via OpenAI Shap-E**
   - Method: `ShapEImg2ImgPipeline` from Hugging Face diffusers
   - Notebook: `jewelry_generate.ipynb`
   - Output Files: `jewelry.glb`, `jewelry.ply`
7. **Overlay Patterns on 3D Models**
   - Notebook: `jewelry_sphmapped.ipynb`
   - Output File: `jewelry_sphmapped.glb`

## Issues & Alternative Approach

- **Shap-E Limitations**: Models are often incomplete and cubic due to diffusion starting from a cube.
- **Alternative via Polycam AI**:
  1. Generate 3D Models
     - Tool: Polycam 3D Model Generator (<https://poly.cam/tools/3d-model-generator>)
     - Output Files: `jewelry_1.glb` ... `jewelry_6.glb`
  2. Overlay Patterns
     - Notebook: `jewelry_sphmapped.ipynb`
     - Output Files: `jewelry_1_sphmapped.glb`, ..., `jewelry_6_sphmapped.glb`
