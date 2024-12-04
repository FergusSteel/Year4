
### Project Plan: Cross-Modal Translation of Visual and Audio Domains for Music Synthesis

#### **1. Project Overview**
This project will investigate how visual transformers can embed and translate features from the visual domain into the audio domain. The goal is to create a cross-modal model that allows for dual-stream translation of embeddings from videos of musical performances to synthesised audio of said performance and vice-versa.

#### **2. Research Questions**
- **Primary Question**: Can visual transformers be used effectively in a two-stream cross-modal model to embed and translate visual features into the audio domain to synthesize realistic music and vice versa with the use of priors?
#### **3. Key Objectives**
1. **Develop a Cross-Modal Translation Model**: 
   - Use visual transformers (e.g., ViVit) along with optical flow fields to extract features from musical performance videos and condition audio synthesis models (e.g., diffusion models) to generate expressive music
2. **Evaluate Synthesis Effectiveness**:
   - Set up experiments to quantitatively and qualitatively assess the synthesized audio compared to the ground truth in terms of accuracy and emotional expression.

#### **4. Project Justification**
This project advances the field of multimodal learning by exploring how visual transformers can be used to express musical nuances through audio synthesis. The research has implications for music performance analysis by potentially offering new tools for analyzing musical performance or through reconstructing musical performances from audio, through utilising cross-modal translation.


#### **5. Methodology**
##### **5.1. Data Preparation**
- **Dataset**: URMP Dataset (as identified earlier) + Solos dataset.
- **Preprocessing**: Extract visual features from videos (optical flow fields, performer body movements, etc.) and audio features (spectrograms, waveforms or Musical Embeddings).
##### **5.2. Model Architecture**
- **Visual Transformer (ViVit)**: For visual feature extraction.
- **Audio Synthesis Network**: Use diffusion models (Google's spectrogram diffusion model or Meta's MusicGen) for audio generation.
- **Cross-Modal Learning**: Train the model to map visual embeddings to audio embeddings.

- **Quantitative Evaluation**:
   - Measure accuracy by comparing synthesized audio to the ground truth.
   - Use metrics like signal-to-noise ratio (SNR) or perceptual evaluation of speech quality (PESQ) to quantify differences.
- **Qualitative Evaluation**:
   - Conduct a human subject study where participants judge the emotive quality and semantic coherence of synthesized music compared to the ground truth.
- **Additional Experiments**
   - Demonstratin the dual-stream nature of cross-modal model.

##### **5.4. Synthesis Pipeline**
1. **Step 1**: Train visual transformers on the URMP dataset to extract temporal and spatial features of musical performances.
2. **Step 2**: Use spectrogram diffusion models to generate audio based on these visual embeddings.
3. **Step 3**: Optionally, test reverse-direction audio-to-video synthesis by inputting audio and generating a performance video.
#### **6. Key Milestones & Timeline *Starting October 21st*
- **Phase 1: Literature Review and Data Preparation (Weeks 1-4)**
   - Finalize research question and review existing literature on cross-modal learning and music generation.
   - Gather and preprocess the dataset (URMP).
   - Finalize choice of models (e.g., ViVit, diffusion models).
- **Phase 2: Model Design and Initial Prototype (Weeks 5-8)**
   - Set up model architecture for visual transformers and audio synthesis.
   - Develop a prototype that generates audio from visual input.
- **Phase 3: Model Training and Tuning (Weeks 9-12)**
   - Train the model on URMP data, adjusting hyperparameters.
   - Run initial tests to evaluate synthesized music.
- **Phase 4: Evaluation and Analysis (Weeks 13-16)**
   - Conduct quantitative and qualitative evaluations.
   - Refine the model based on feedback and results.
- **Phase 5: Final Testing and Report Preparation (Weeks 17-20)**
   - Conduct final tests, compile results, and write the project report.
#### **7. Tools and Resources**
- **Hardware**: Access to GPUs for model training - this is done
- **Software**: PyTorch (for model development), Hugging Face Transformers, Google’s Music Spectrogram Diffusion, Meta’s MusicGen if using music embeddings is feasible.
- **Data**: URMP dataset, potential additional datasets for cross-validation (Solos Dataset).
#### **9. Risks and Contingencies**
- **Risk 1**: Insufficient data for generative models.
   - *Mitigation*: Experiment with alternative model architectures, and extending visual features through employing optical flow fields
- **Risk 2**: Difficulty in quantitative evaluation.
   - *Mitigation*: Use multiple evaluation metrics and human subject tests to assess emotional expression and accuracy.
#### **10. Deliverables**
- Audio-to-Visual (Dual-Stream) Cross-Modal Translation Model**: A functional dual-stream model capable of synthesizing music from videos of musical performances and using those embeddings and a prior, synthesise performance videos from audio.
