# Image Processing — Colour Conversion & Rotation

An image processing pipeline built in GNU Octave that performs RGB-to-grayscale conversion and 90-degree rotation on any input image. Demonstrates core Digital Signal Processing (DSP) concepts including colour channel separation, luminosity weighting, and 2D matrix transformation.

Built as an individual academic project during B.Sc. Electronics at Christ University (2023).

---

## What it does

| Step | Operation | Concept |
|---|---|---|
| 1 | Load and display original image | RGB colour model, 3D matrix representation |
| 2 | Convert RGB → Grayscale | Luminosity weighted average (ITU-R BT.601) |
| 3 | Rotate 90° clockwise | Matrix transposition + column reversal |
| 4 | Side-by-side comparison | Subplot visualisation |

---

## Output

Running the script opens four figure windows:

1. Original image in full colour (RGB)
2. Grayscale conversion
3. Grayscale image rotated 90° clockwise
4. All three side by side for comparison

---

## The science behind it

### RGB to Grayscale — Luminosity Method

A naive grayscale conversion would simply average the three colour channels equally. This produces a technically correct but visually flat result. The luminosity method uses weighted values that reflect how sensitive the human eye actually is to each colour:

```
Gray = 0.299 × Red  +  0.587 × Green  +  0.114 × Blue
```

Green carries the most weight (~59%) because human eyes have more green-sensitive cone cells. This is the ITU-R BT.601 standard used in broadcast television and most digital image processing systems.

### 90° Rotation — Matrix Transformation

A 90-degree clockwise rotation is mathematically equivalent to two operations on the pixel matrix:

```
Step 1: Transpose  — rows become columns  →  pixel at (r, c) moves to (c, r)
Step 2: Flip LR    — reverse column order →  pixel at (c, r) moves to (c, rows - r + 1)
```

This is a fundamental 2D linear algebra operation with applications in computer vision, medical imaging (CT/MRI reorientation), and facial recognition pre-processing pipelines.

---

## How to run it

### Requirements

- [GNU Octave](https://octave.org/download) (free) — or MATLAB
- Octave Image package
- Octave Signal package

### Install packages (Octave only — one time)

```octave
pkg install -forge image
pkg install -forge signal
```

### Run the script

1. Place `image_processing.m` and your image file in the same folder
2. Open GNU Octave and navigate to that folder
3. Change the filename on line 30 to match your image:
   ```octave
   img = imread("your_image.png");
   ```
4. Run the script:
   ```octave
   run image_processing.m
   ```

Four figure windows will open showing each stage of the pipeline.

---

## Code improvements over original

The original script used `new = new'` for rotation — a raw matrix transpose which only performs half of the rotation (transpose only, no column flip). This has been corrected to use `rot90(gray_img, -1)` which performs a proper 90-degree clockwise rotation.

Additional improvements:
- Added luminosity weighting explanation in comments
- Added image dimension reporting to console
- Added a fourth subplot showing all stages side by side
- Added the mathematical basis of each transformation

---

## Applications of these techniques

- **Computer vision** — image pre-processing before feature extraction
- **Biometric security** — face and fingerprint recognition pipelines
- **Medical imaging** — CT and MRI scan orientation correction
- **Satellite imaging** — terrain and land-use analysis
- **Document scanning** — automatic orientation correction

---

## Project context

Individual project completed during B.Sc. Physics, Mathematics & Electronics at Christ University. Focused on applying Digital Signal Processing theory to real image data — specifically the relationship between colour models, matrix representation of images, and 2D spatial transformations.

---

## Skills demonstrated

`GNU Octave` `Digital Signal Processing` `Image Processing` `Matrix Operations` `RGB Colour Model` `Linear Algebra` `Signal Processing` `Computer Vision Fundamentals`
