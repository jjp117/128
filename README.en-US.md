<h4 align="left">
  <span style="margin:0 10px;color:#24292f">English</span>
  <a href="./README.md">简体中文</a>
</h4>
<p align="center">
<img src="https://aino.pages.dev/preview.png" width="300"/>
</p>
<h1 align="center">JJP｜Adversarial Image Perturbation Generator</h1>
<p align="center">
Static web implementation. All computations execute within the browser's local sandbox. User images are never uploaded to any remote server.
</p>
<p align="center">
<a href="https://github.com/jjp117/128/releases">
<img src="https://img.shields.io/github/v/release/jjp117/128?style=flat-square&logo=github" alt="Release">
</a>
<a href="https://github.com/jjp117/128/stargazers">
<img src="https://img.shields.io/github/stars/jjp117/128?style=flat-square&logo=github" alt="Stars">
</a>
<a href="https://github.com/jjp117/128/blob/main/LICENSE">
<img src="https://img.shields.io/github/license/jjp117/128?style=flat-square&logo=github" alt="License">
</a>
</p>
<br>
<p align="center">
<a href="https://aino.pages.dev/" target="_blank">
<img src="https://img.shields.io/badge/🔗Access Now‑AI Camouflage-2563eb?style=for-the-badge&logo=https://aino.pages.dev/&logoColor=white" width="320" alt="Open AI Camouflage">
</a>
&nbsp;&nbsp;
<a href="https://github.com/jjp117/128/releases" target="_blank">
<img src="https://img.shields.io/badge/📥Download Source-red?style=for-the-badge&logo=github&logoColor=white" width="320" alt="Download Source">
</a>
</p>

# JJP AI Camouflage
## What is this
JJP AI Camouflage is a mathematical image preprocessing tool. By injecting structured noise and geometric distortions at the pixel level, it disrupts low-order visual features (edges, textures, color correlations), aiming to raise the recognition cost for automated OCR tools and lightweight computer vision models.

## Design Goal
Provide non-professional users with a simple, direct copyright protection aid. Users need no deep learning knowledge, model training, or GPU computing power; browser-based processing suffices for "anti-scraping" treatment of artworks, document screenshots, etc.

## Execution Mode
All perturbation calculations are based on Canvas ImageData API and native JavaScript math libraries, independent of any backend services or AI inference interfaces.

## Algorithm Principles
Employs a hybrid perturbation strategy:
1. **Sub-pixel Geometric Distortion**: Applies minor sinusoidal displacement to Sobel gradient field (amplitude ≤1.5px), breaking edge continuity for Canny/Sobel operators.
2. **Channel Phase Decoupling**: Independently applies out-of-phase pseudo-random offsets to R/G/B channels, disrupting natural image color-space correlation.
3. **Structured Moiré Overlay**: Composites low-frequency checkerboard texture (Opacity 5-15%), confusing LBP/GLCM local binary pattern feature extraction.

## Intensity Levels
Offers three presets plus free slider:
- **Human First (0-30%)**: Quality priority. Noise nearly invisible to naked eye, weaker defense, suitable for daily sharing.
- **Balanced (30-70%)**: Balanced mode. Slight graininess, effectively interferes with traditional OCR engines, recommended default.
- **Machine Blind (70-100%)**: Defense priority. Obvious noise and blur, significant blocking effect against most automated scrapers, sacrificing aesthetics.

## Usage
Open the web version to start. Drag image into page, adjust intensity slider to preview; confirm and click export to generate PNG file with adversarial perturbation. Note: Must export as PNG; JPG compression smooths out high-frequency protective noise causing failure.
> Web Version: https://aino.pages.dev/

## ⚠️ Browser Compatibility Notice
Depends on high-performance Canvas pixel operations. Processing 4K+ resolution images may cause brief lag. Recommended on devices with SSD and ≥8GB RAM. Older mobile browsers may crash due to memory overflow.

## Security & Limitation Statement
- **Not Invisible Cloak**: Noise is visible to human eye at medium-high intensity. This is explicit deterrence, not perfect stealth.
- **Defense Ceiling**: Primarily targets traditional engines like Tesseract/EasyOCR and lightweight CNNs. Against multimodal LLMs like GPT-4V/Claude 3, which possess strong contextual understanding, this tool only increases computational burden, not guaranteeing 100% non-recognition.
- **Artistic Damage**: Processed images are not original lossless state; use cautiously where ultimate quality is paramount.

## Known Limitations
- Does not support direct editing of vector graphics (SVG); rasterization required first.
- Cannot defend against targeted denoising algorithm attacks.
- Single processing time grows linearly with resolution.

