# Droste Effect

Interactive web app for applying the [Droste effect](https://en.wikipedia.org/wiki/Droste_effect) to any image.

**[Try it live →](https://quasarbright.github.io/droste)**

## What it does

Upload an image, drag a quadrilateral over it, and the app recursively renders the full image inside the quad — which contains the quad, which contains the image, which contains the quad...

The effect is computed in real time on the GPU via a WebGL fragment shader that iterates the inverse homography for each pixel.

## Controls

- **Drag corners** to reshape the quad
- **Drag inside the quad** to move it
- **Recursion depth** slider controls how many levels deep the recursion goes
- **Mode selector** — Rectangle, Square, or Free quad
- **Reset Quad** — snaps back to the default centered position
- **Save Image** — downloads the current frame as a PNG

## Corner colors

Each corner of the quad is color-coded, and the corresponding corner of the source image is marked with the same color so you can see how the mapping works.

| Color | Corner |
|-------|--------|
| 🔴 Red | Top-left |
| 🟢 Green | Top-right |
| 🔵 Blue | Bottom-right |
| 🟡 Yellow | Bottom-left |

## How it works

The quad defines a projective mapping (homography) from the full image onto the quad region. The WebGL fragment shader iterates the inverse homography: for any pixel inside the quad, it maps the coordinate back to image space and repeats — up to the chosen recursion depth. The result is the Droste effect with correct perspective for arbitrary quadrilaterals.

No dependencies. Single HTML file.
