# Literature First Draft
- Completed
- Will need to be amended/redrafted before the interim report as implementation continues.

---

# Research Methods Coursework
- Project Poster + Abridged Literature Review completed.
- Helped to further plan out implementation.

---

# Implementation Report
## Data Pre-processing Pipeline
- Dataset downloaded (**Currently redownloading on desktop** as was testing on laptop).
- Standardized framerates to **25 fps**.
- Standardized file formats.
- Standardized audio sampling rate to **44.1 kHz** (MusicGen uses this sampling rate).
- Project skeleton completed.
- Dataset object created.

---

# Implementation Decisions
## MusicGen Model for Audio-Feature Extraction
- Allows for generation of music from tokens.
- Latent space representation of audio tokens will be created from video input.

---

## Temporal Alignment
- MusicGen creates **50 tokens per second of audio**.
- With **25 fps**, we have **2 tokens per frame**.
- Latent space will learn correspondence between **optical flow**, **semantic embeddings**, and tokens using attention mechanism.

---

## Video Diffusion Pipeline
- Generative model **conditioned on an input image** and a string of audio tokens.
- Produces video frames of musical performance (reverse process).

---

# Latent Space
## Cross-Modal Attention
- Audio tokens and video embeddings projected onto a **shared latent space**.
- Coordination achieved through attention mechanisms.

---

## Temporal Alignment
- Cross-attention with **positional encodings**.
- Explicit temporal information added to both:
  - Video embeddings.
  - Audio embeddings.
- Temporal positional encodings ensure attention mechanism understands order.

---

## Why does it work?
 - This is just what video transformers do but doing so across modalities is trivial given we have 50 tokens and 25 frames per second
- Temporal encoding ensures proper alignment across modalities.
