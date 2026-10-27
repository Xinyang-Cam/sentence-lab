# Meaning Lab

A playful, single-file language science exhibit for exploring sentence meaning, sentence embeddings, and cosine similarity.

**Site:** https://xinyang-cam.github.io/sentence-lab/

## Try it

Enter two English sentences, optionally choose an example, and select **Calculate similarity**. The website downloads a quantized ONNX model on first use and computes two 384-dimensional sentence embeddings entirely in the browser. The displayed cosine score (−1 to +1), vector angle, and pixel heatmaps come from these embeddings. No scores are hardcoded.

## How it works

- Original model: [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
- Browser model: [Xenova/all-MiniLM-L6-v2](https://huggingface.co/Xenova/all-MiniLM-L6-v2), ONNX q8
- Runtime: Transformers.js v3, WASM, `pooling: 'mean'`, `normalize: true`
- Cosine: dot product divided by the product of the vector magnitudes
- User text is encoded in the browser and is not sent to a server-side inference endpoint. Model/library files are downloaded from third-party hosts.

This is an educational tool. Cosine similarity is **not** a percentage or probability of equivalent meaning. The geometric diagram reconstructs the angle implied by the 384-dimensional cosine; it is not a two-dimensional embedding projection. Labels for score bands are informal, not validated thresholds.

## Development and publishing

`index.html` is self-contained except for its externally downloaded font, JavaScript inference runtime, and model files. No build step or API key is required.

To preview, run `python -m http.server 8000` in the repository and open http://localhost:8000.

GitHub Pages can serve this file from the `main` branch at `/(root)`. The in-page share dialog encodes the canonical public URL in its QR image without any user-entered sentences or tracking parameters.

**Note:** A complete first-run end-to-end model download should be tested on an actual phone and connection after deployment.

## Credit

Created by Xinyang Feng — [xf263@cam.ac.uk](mailto:xf263@cam.ac.uk). The page contains expandable APA 7 references and links to the original model and browser conversion.
