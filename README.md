# DINOv3: Trading Local Sharpness for Global Coherence

This notebook-driven mini-project documents how DINOv3 dense features differ from DINOv2, with
one clear objective: explain why DINOv3 produces globally coherent maps when you visualize patch
embeddings. 

✨ Smooth PCA maps, and cosine-similarity diagnostics.  
📸 Every image was captured by me in the wild. 


---

## Quickstart 

```bash
# Clone the repository
git clone https://github.com/theaudaudiffret/Dino_V3_improvements_visualized.git
cd Dino_V3_improvements_visualized

# Create a virtual environment
python3 -m venv venv

# Activate the virtual environment
# On Linux / macOS:
source venv/bin/activate
# On Windows:
# venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
markdown
Copier le code
```
---

## Project aim

- Show, with side-by-side visual evidence, how DINOv3 trades local sharpness from DINOv2 for
  globally structured patch representations.
- Connect those visual differences to model design choices, especially DINOv3's Gram regularization of patch features.


---

## Concepts that matter

- DINOv3 vs DINOv2 for global coherence: PCA maps from DINOv3 are smoother, with fewer
  high-frequency artifacts, which clarifies object versus background regions.
- Gram anchoring: Regularising the pairwise structure of patch embeddings stabilises dense maps and drives the smoother PCA projections we observe.

---

## Workflow inside the notebook

1. Extract patch embeddings from DINOv2 and DINOv3 at the desired resolution.
2. Run PCA to identify the patches that are the most responsible for the variance of the embeddings. 
3. Visualise component scores on the patch grid to obtain pseudo-colour maps.


---

## Cosine-based diagnostics

- Smoothness: Average cosine similarity with the four nearest neighbours captures local
  smoothness.
- Reference-patch maps: Pick a patch and inspect how similarity propagates across the image for a
  figure-three style visual.
- Image retrieval: Mean-pool embeddings, compute cosine scores, and see retrieval improve once
  background directions are suppressed.
