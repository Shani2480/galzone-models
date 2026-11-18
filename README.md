# Galzone models

Model files that the Galzone gallery app downloads on request, for features that run entirely on the phone. They are published here only so the app can fetch them; nothing in this repository is app code.

## SigLIP 2 image encoder, int8 (`models-siglip2-w8-v1`)

Used for on-device tag suggestions (topics such as pets, politics, food or funny, and learning the user's own tags from examples).

- **File:** `siglip2_w8.tflite` (94.5 MB, LiteRT / TFLite)
- **Source:** the image encoder of SigLIP 2 ViT-B/16 at 224 px by Google ([`timm/vit_base_patch16_siglip_224.v2_webli`](https://huggingface.co/timm/vit_base_patch16_siglip_224.v2_webli)), converted to LiteRT with the GPU-friendly rewrites published in [`litert-community/SigLIP2-base-patch16-224`](https://huggingface.co/litert-community/SigLIP2-base-patch16-224), then quantized to int8 weights (float compute).
- **Input:** `[1, 3, 224, 224]` float32, RGB scaled to [-1, 1], channels first. **Output:** `[1, 768]` L2-normalised image embedding.
- **Fidelity:** cosine 0.9994 on average against the original model; topic decisions agree 99.97 % of the time.
- **SHA-256:** `acfb7cd1ac791a06fc71c464df15bf9f143d9cc9cff4ec0cd50c289dc3c44d46`

## License

The model weights are © Google and released under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), which also covers this converted copy. See the [SigLIP 2 model card](https://huggingface.co/google/siglip2-base-patch16-224) and paper ([arXiv:2502.14786](https://arxiv.org/abs/2502.14786)) for details on training data and intended use.
