# 🏠 Rooftop Segmentation for Solar Potential Estimation

This notebook demonstrates how to build a deep learning pipeline using **PyTorch** to segment rooftops from satellite imagery. The segmented areas can be used to estimate solar panel installation potential and inform clean energy decisions.

---

## 📌 Project Objectives

- Segment rooftop areas from RGB satellite imagery using a **UNet model**
- Overlay predictions on original images with an **orange radiance effect**
- Prepare data for use in solar energy potential calculators
- Save the model for reuse with **pickle (.pkl)**

---

## 🧠 Model Overview

- Architecture: `UNet` (from `segmentation-models-pytorch`)
- Backbone: ResNet34 pretrained on ImageNet
- Input: 256x256 RGB images
- Output: Binary mask of rooftop areas

---

## 🗂️ Dataset Structure

```
📁 dataset/
├── images/          # RGB satellite images
└── labels/          # Binary rooftop masks (.tif)
```

Each image has a corresponding mask file with the same base name.

---

## 🔧 Installation

Install required packages:

```bash
pip install torch torchvision segmentation-models-pytorch matplotlib
```

---

## 🚀 How to Run

1. Update the `image_dir` and `mask_dir` paths in the notebook.
2. Run all cells to:
   - Train the UNet model
   - Visualize predicted rooftop overlays
   - Save the model as a `.pkl` file for future use

---

## 🧪 Example Prediction

Once trained, you can predict on a single image or batch of images:

```python
from PIL import Image
image = Image.open("your_image.jpg").convert("RGB")
input_tensor = transform(image).unsqueeze(0).to(device)

# Get overlay result from model
model.eval()
with torch.no_grad():
    overlay_image = model(input_tensor, overlay=True)[0]

plt.imshow(overlay_image)
```

---

## 💾 Saving the Model

Save the trained model weights using pickle:

```python
import pickle
with open("rooftop_model.pkl", "wb") as f:
    pickle.dump(model.state_dict(), f)
```

To load later:

```python
with open("rooftop_model.pkl", "rb") as f:
    model.load_state_dict(pickle.load(f))
model.eval()
```

---

## 📚 Dependencies

- Python 3.8+
- PyTorch
- torchvision
- segmentation-models-pytorch
- matplotlib
- PIL (Pillow)

---

## ✨ Author

Developed by **Manthan Surjuse** as part of a solar panel potential calculator project.

---

## 📝 License

MIT License – use it freely for academic or personal purposes.
