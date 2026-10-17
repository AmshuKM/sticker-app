# Sticker Splitter

Turn any image into **print-and-cut sticker artwork**. It reduces the image to a few flat colours, traces each colour region into vector shapes, and exports artwork with cut lines, ready for a Cricut, Silhouette or print shop.

It's a single `index.html` file with no install and no build step. Processing runs in your browser. The only network request is the optional AI background removal, which downloads its model once from a CDN. Your image is never uploaded.

## Features

- **Colour reduction**: k-means clustering in CIE Lab colour space (2–16 colours), so similar-looking colours stay together and distinct ones stay apart.
- **Clean shapes**: a smoothing filter removes anti-aliasing specks, and tiny pieces below a pixel threshold merge into their neighbours.
- **Vector tracing**: each colour region becomes closed SVG paths.
- **Edit pieces**: click a piece in the preview to remove it (it takes on the surrounding colour), and toggle whole colours on or off. Undo/redo with `Ctrl+Z` / `Ctrl+Y`.
- **Exposure** slider and optional **AI background removal**.
- **Cut lines**: dotted, dashed or solid red lines, or a white border gap between pieces.
- **Export** to **SVG** (separate `Print` and `CutContour` layers), **PNG** (300 DPI on sheets) or **vector PDF**.
- **Sheet layout**: fit to the artwork, or centre it on A3/A4/A5/Letter with margins. It shows the real print size in cm.

## Usage

Open `index.html` in a modern browser, choose an image and adjust the controls. The preview updates live. `Ctrl+scroll` zooms.

## Example

Using the included [`sample.png`](sample.png):

![sample input](sample.png)

1. Click **Choose file** and select `sample.png`.
2. Set **Colors** to `4` and keep **Smoothing** at `2`. The swatch row lists each colour and how many pieces it produced.
3. If the background was detected as a flat colour, it is already unticked. Untick any other colour you don't want printed.
4. Click any stray small piece in the preview to remove it.
5. Pick **Cut lines → White border** at `8` px for a classic die-cut look.
6. Set **Sheet** to `A4`, **Margin** to `10` mm, and **Format** to `PDF`.
7. Click **Download** to get `stickers.pdf`, a vector file with colour fills plus cut contours, sized to print on A4.

Choose **SVG** instead to get a file with `Print` and `CutContour` layers that cutting software such as Silhouette Studio or Cricut Design Space can import directly.
