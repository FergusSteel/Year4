## Progress Report
- Literature First Draft Completed
	- Will need to be amended/redrafted before interim report as implementation continues
- Project Poster + Abridged Literature Review (Done for Research Methods coursework)
	- Helped me to further plan out implementation
- Implementation Report
	- Data Pre-processing Pipeline
		- Dataset downloaded (Currently Redownloading on Desktop as was testing on laptop)
		- Standardised Framerates (25)
		- Standardised File formats
		- Standardised Audio Sampling Rate to 44.1khz (musicGen uses this sampling rate)
		- Project Skeleton Completed
		- Dataset Object created
	- Implementation Decisions
		- MusicGen Model for Audio-Feature Extraction
			- Also allows for Generation of music from tokens
			- This means that given a video, a latent space representation of audio tokens will be created
		- Temporal Alignment:
			- MusicGen created 50 tokens per 1 second of audio,
			- Given 25 fps, we have 2 tokens per corresponding frame
			- Latent Space will therefore learn correspondence between Optical flow + Semantic Embeddings and the tokens with attention mechanism
		- Video Diffusion Pipeline
			- Will need to create a generative model **conditioned on an input image** and a string of audio tokens to produce video frames of musical performance.
			- i.e. the reverse process
		- Latent Space
			- Cross-Modal Attention of Audio Tokens and Video Embeddings:
				- This is a **coordinated representation** and both modalities are projected onto the latent space via attention mechanism
			- Temporal Alignment:
				- Cross-Attention with Positional Encodings
					- Explicitly encode temporal information to ensure proper alignment.
					- Add temporal positional encodings to both video and audio embeddings before cross-attention. 
						- this is just what video transformers do but doing so across modalities is trivial given we have 50 tokens and 25 frames per second
					- This helps the attention mechanism understand temporal order.

**Notes;**
**Deliverables for next week**:
Make a diagram that surmises architecture and communicates problem 1.5 hrs
Temporal Feature alignment dont invent it just use what works. 

Create a timeline for remainder of year and then one for up to april. 1 hr
Redraft PRRCS AE2 to be a real plan for current state of project. 1 hr

Update Diss Template with v1.2 0.5 ht
