OIL SPILL IMAGE DATASET - CLEANED & PREPROCESSED
==================================================

Contents:
- train/oil_spill/  -> 11 cleaned, deduplicated, watermark-free oil spill images
                        (resized to 224x224, JPEG quality 95)

Preprocessing steps applied:
1. Validated all files (removed corrupt/unreadable images) - 0 removed
2. Removed exact duplicate files (MD5 hash check) - 0 removed
3. Removed near-duplicate images (perceptual hash, Hamming distance <=5) - 0 removed
4. Removed 3 images with social media watermarks/text overlays
   (to prevent the model learning watermark text as a false signal)
5. Resized all images to 224x224 (standard CNN input size)
6. Renamed sequentially: oil_spill_001.jpg to oil_spill_011.jpg

IMPORTANT - BEFORE YOU TRAIN:
- This folder only contains the "oil_spill" (positive) class.
  You MUST add a "normal" / "no_spill" class folder with clean ocean
  images, or your CNN will have nothing to compare against and will
  not learn to distinguish spill vs. no-spill.

- 11 images is very small for training a CNN from scratch. Recommended:
  a) Use transfer learning (MobileNetV2/ResNet50 pretrained on ImageNet)
     rather than training from scratch.
  b) Apply heavy data augmentation (rotation, flip, zoom, brightness)
     to multiply effective training samples.
  c) Collect more real images per class (aim for 100+ per class minimum
     for a usable hackathon demo, 1000+ for production).

Suggested folder structure to build next:
dataset/
  train/
    oil_spill/     <- (this dataset goes here)
    normal/        <- (add clean ocean images here)
  val/
    oil_spill/
    normal/
