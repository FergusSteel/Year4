---
Project Plan: Cross-Modal Translation of Visual and Audio Domains for Music Synthesis
---

<!-- Slide 1 -->
### Project Plan: Cross-Modal Translation of Visual and Audio Domains for Music Synthesis

---

#### **1. Project Overview**
This project will investigate how visual transformers can embed and translate features from the visual domain into the audio domain. The goal is to create a cross-modal model that allows for dual-stream translation of embeddings from videos of musical performances and vice-versa.

With the MVP/Fallback, focusing on ensuring one of those streams is feasible in the sense that I can write a dissertation about it.

---

<!-- Slide 2 -->
#### **2. Research Questions**
- **Primary Question**: Can visual transformers be used effectively in a two-stream cross-modal model to embed and translate visual features into the audio domain to synthesize realistic music and vice versa with the use of priors?

---

<!-- Slide 3 -->
#### **3. Key Objectives**
1. **Develop a Cross-Modal Translation Model**: 
   - Use visual transformers (e.g., ViVit) along with optical flow fields to extract features from musical performance videos and condition audio synthesis models (e.g., diffusion models) to generate expressive music via a shared latent space.
2. **Evaluate Synthesis Effectiveness**:
   - Set up experiments to quantitatively and qualitatively assess the synthesized audio compared to the ground truth in terms of accuracy and semantic accuracy (i.e., emotional expression).

---

<!-- Slide 4 -->
#### **4. Project Justification**
This project advances the field of multimodal learning by focusing on musical performances and exploring how visual transformers can be used to express musical nuances through audio synthesis. The research has implications for both music performance analysis and education by potentially offering new tools for analyzing musical performance through cross-modal embeddings. Additionally could potentially enable reconstruction of live performances.

---

<!-- Slide 5 -->
#### **5. Methodology**
##### **5.1. Data Preparation**
- **Dataset**: URMP Dataset (as identified earlier) + Solos dataset.
- **Preprocessing**: Extract visual features from videos (optical flow fields, performer body movements, etc.) and audio features (spectrograms, waveforms, or Musical Embeddings).

---

<!-- Slide 6 -->
##### **5.2. Model Architecture**
- **Visual Transformer (ViVit)**: For visual feature extraction.
- **Audio Synthesis Network**: Use diffusion models (Google's spectrogram diffusion model or Meta's MusicGen) for audio generation.
- **Cross-Modal Learning**: Train the model to map visual embeddings to audio embeddings.

---

- **Quantitative Evaluation**:
   - Measure accuracy by comparing synthesized audio to the ground truth.
   - Use metrics like signal-to-noise ratio (SNR) or perceptual evaluation of speech quality (PESQ) to quantify differences.
- **Qualitative Evaluation**:
   - Conduct a human subject study where participants judge the emotive quality and semantic coherence of synthesized music compared to the ground truth.
- **Additional Experiments**
   - Demonstrate the dual-stream nature of cross-modal model.

---

<!-- Slide 7 -->
##### **5.4. Synthesis Pipeline**
1. **Step 1**: Train visual transformers on the datasets to extract temporal and spatial features of musical performances and learn shared representations.
2. **Step 2**: Use one of the synthesis pipelines to generate audio based on these shared embeddings.
3. **Step 3**: Optionally, test reverse-direction audio-to-video synthesis by inputting audio and generating a performance video.

---

<!-- Slide 8 -->
#### **6. Key Milestones & Timeline *Starting October 21st***
- **Phase 1: Literature Review and Data Preparation (Weeks 1-4)**
   - Finish literature Review on cross-modal learning and music generation.
   - Gather and preprocess the dataset (URMP) - **mostly done**.
   - Finalize choice of models (e.g., ViVit, diffusion models), complete.
- **Phase 2: Model Design and Initial Prototype (Weeks 5-8)**
   - Set up model architecture for visual transformers and audio synthesis.
   - Develop a prototype that generates audio from visual input.

---

- **Phase 3: Model Training and Tuning (Weeks 9-12)**
   - Train the model on URMP data, adjusting hyperparameters.
   - Run initial tests to evaluate synthesized music.
- **Phase 4: Evaluation and Analysis (Weeks 13-16)**
   - Conduct quantitative and qualitative evaluations.
   - Refine the model based on feedback and results.
- **Phase 5: Final Testing and Report Preparation (Weeks 17-20)**
   - Conduct final tests, compile results, and write the project report.

---

<!-- Slide 9 -->
#### **7. Tools and Resources**
- **Hardware**: Access to GPU clusters for model training.
- **Software**: PyTorch (for model development), Hugging Face Transformers, Google’s Music Spectrogram Diffusion, Meta’s MusicGen if using music embeddings is feasible.
- **Data**: URMP dataset, Solos Dataset, potential additional datasets for cross-validation.

---

<!-- Slide 10 -->
#### **8. Risks / Roadblocks**
- **Risk 1**: Insufficient data for generative models.
   - *Mitigation*: Experiment with alternative model architectures and extend visual features through employing optical flow fields.
- **Risk 2**: Difficulty and time constraints in qualitative evaluation.
   - *Mitigation*: Focus on using broader qualitative evaluation metrics and human subject tests to assess emotional expression and accuracy.

---

<!-- Slide 11 -->
#### **9. What Have I Done?**
- Unfortunately, have been focused on getting the marks for the interim report:
   - This means papers, papers, papers.
   - I have started writing my literature review and would love a review of that. I can send it over if you have the time..
- **Implementation**:
   - Downloaded the datasets above, split into train and test.
   - Set up an environment where we can extract video and audio separately, and implemented feature extraction pipelines for the videos (currently a pre-trained ViVit + Optical Flow Fields or Skeleton Tracking for Solos Dataset).

---

<!-- Slide 12 -->
#### **What Next**
- **Model Decisions**:
   - First decision to make here is which synthesis pipeline makes the most sense, i.e., what representation are we trying to learn:
      - **Option A**: Visual -> Musical Embeddings (using Meta's new MusicBERT, how feasible is this?)
      - **Option B**: Visual -> Spectrogram Diffusion (simpler, allows for priors which could mitigate insufficient data risk).
- **Interim Report**:
   - Aim to finish an extended draft (approx. 4 pages) for PRRCS by the end of next week. Reviewed around 20 papers; need to reach 50 (3 per day).
- **Pilot Studies**:
   - Test the two synthesis pipelines and select the more promising one by the next meeting (keep code for potential detailed review).

---

Laimeng Tang - Deep Optical Flow Fields

Look into optical flow fields more

HAVE AN ER DIAGRAM FOR NEXT WEEK
OVERALL DIAGRAM
AND
ONE FOR...
	VISUAL FEATURE EXTRACTION PIPELINE + OPTICAL FLOW FIELD
	AUDIO FEATURE EXTRACTION
	AUDIO SYNTHESIS PIPELINE (MAYBE)