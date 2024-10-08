## Project Justification and Extended Plan
- This is an extension of the [[Original Project Brief]], based on Alistair's template that will be forwarded to Paul before being added to.
- I want to keep accurate track of my time using [[Time Tracking]].
### Research Question
> Can visual transformers effectively embed and translate features from the visual domain into the audio domain, allowing for the synthesis of accurate and emotionally expressive music?

> ALT: Can we train a generative model to create music that matches the semantic embeddings of  videos of musical performances. I.e. if a violin solo is being played slowly and clearly emotively is this able to be captured and then translated into the audio domain (Not necessarily matching the ground truth note by note, but matching in terms of semantics and matching tempos)

This project aims to investigate the following:
1. Cross Modal Translation of Features in the Audio-Visual Domains
	 - i.e: how visual performance's can be used to generate accurate and emotive music through cross-modal translation between visual and auditory domains.
2.  Effective approaches for embedding of cross-modal features and audio synthesis:
	- i.e. Pretrained Visual Transformers vs Generative Adversarial Networks

Is is appropriate for this research to completed as it could possibly:
- Advance the field of multimodal learning and Audio-Visual translation
	- Visual transformers have not been used for this explicit purpose of expressing musical nuances in synthesised audio supported by the cross-modal translation from videos of musical performances.
	- This extends upon the advancing field of cross-modal translation using ViTs - [An Audio-Visual Generative Model](https://ar5iv.labs.arxiv.org/html/1704.08292) for generating performance videos from music. This paper in particular includes an Image-to-sound encoder, which takes a spectogram and image of performer to produce a video of performance (interesting to note that myself and Paul had discussed this as a possible inverse path through our proposed network).
- Enhance Music Performance Analysis
	- By understanding how visual elements of a musical performance can influence the emotional/musical aspects of the performance we can potentially support tools that can make musical education and musical performance analysis far more nuanced.
	- Hypothetically, through achieving this we can potentially decrease the barrier of entry into musical education.
	
The major gap lies in synthesising expressive audio that reflects both the technical and emotional dimensions of a musical performance that can be extracted from visual data. While cross-modal translation exists, the connection between a musical performance and emotionally rich audio synthesis is an area not well explored in the current literature, especially using visual transformers to capture nuanced, high-dimensional visual features (like body movements or intensity) and then using that latent space to influence music generation.

### Methodology
- Create a multi-modal visual transformer network that given a video of a musical performance (and potentially the score) along with an music generation network synthesise audio tracks that both match the ground truth sound and captures the emotive/sematnic elements of the musical performance
- Create an experimental environment such that we can evaluate the quantitative accuracy of synthesised audio (i.e. does it match the ground truth) & the networks ability to understand emotive elements of music, genre, mood, etc.
- Create an experimental environment where we evaluate the qualitative efficacy by using participants to evaluate the realism (i.e. can they distinguish ground truth audio and synthesised audio), and the networks ability to accurately convey the features of the music (e.g. does the synthesised audio capture similar themes when judged compared to the ground truth.)

## Synthesis Pipeline
- 2022 [Model from Google](https://colab.research.google.com/github/magenta/music-spectrogram-diffusion/blob/main/music_spectrogram_diffusion/colab/synthesize_midi.ipynb#scrollTo=pBIzsGBBmqLz) that uses diffusion models (i.e. denoising) to create spectograms from MIDI files.
- MusicGen from Meta using Semantic embeddings of videos - can we tailor this to musical performances?

## Literature Review
- Likely want to find and read 5 key papers for each category that get increasingly relevant/SOTA
- [ ] Cross Modal Embedding
- [ ] Audio-Visual Cross Modal Latent Spaces
- [ ] Audio Synthesis
- [ ] Visual Transformers
- [ ] GANs
- [ ] Computer Vision for Performance Analysis
- [ ] Computer Vision for Musical Performances

The current reading list can be found here [[Reading List]]