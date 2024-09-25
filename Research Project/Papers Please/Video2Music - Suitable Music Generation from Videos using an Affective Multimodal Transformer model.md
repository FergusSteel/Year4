
**Note: from a glance this is exactly what I was planning to do, I'm ten months late. Identifying further work, gaps, or alternative directions from this paper is very important for reading this paper**

- Does not use performance videos
- Given a music video, they analyse it to create features. They also embed midi files and extract features (note density and loudness)
- This data they use an Affective Multimodal Transformer Model to generate music given a video.

> [!quote] **The musical quality, along with the quality of music-video matching is confirmed in a user study.**

## Introduction
- Basically justfies the research and why music is good for videos (when it matches). Also discusses copyright issues

>[!quote] *This framework uniquely uses video features as conditioning input to generate matching music using a Transformer architecture.*

>[!important] "There are very few studies that tackle the task of music generation for video. Some of the pioneering attempts include models like V2Meow [Su et al., [2023](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib57)] and Controllable Music Transformer (CMT) [Di et al., [2021](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib21)], but these are few and far between, underlining the vast potential that lies in this under-explored territory."

## Related Work
- Originally ResNets were used for music generation as they are suitable for non-transient structures
>[!quote] In recent years, the Transformer architecture, introduced by Vaswani, has emerged as a dominant force in temporal sequence processing, surpassing traditional Recurrent Neural Networks (RNNs) in various domains

- [[A history of transformers for music generation]]

These papers could be useful, although not an identical task:
 > [!note] A slightly different task, relates to reconstructing music from instrument performances that lack the accompanying audio [Gan et al., [2020](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib24), Koepke et al., [2020](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib38), Su et al., [2020a](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib58), [b](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib59)], such as generating piano music from a video of finger movements on the piano. Recently, related work has appeared that focuses on generating music for videos that feature dancing or human activities, emphasizing rhythmic relationships [Su et al., [2021](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib60), Zhu et al., [2022a](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib73), [b](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib74)]. These methods, however, necessitate additional motion annotations as input, limiting their applicability to specific videos and hindering their effectiveness for general videos encompassing diverse content.
 
  
  
### Video Features
- Uses CLIP to create the following embeddings: 
	 - Semantics of each frame (i.e. token embeddings of whats in the frame), 
	 - A probability for 6 predefined emotion classes (‘exciting,’ ‘fearful,’ ‘tense,’ ‘sad,’ ‘relaxing,’ and ’neutral’). To get a classification these are smoothed over the frames of the video
		 - "Essentially, this method helps reveal the broader patterns by averaging out the smaller, potentially noisy variations.".
	- Scene offset (what scene) not relevant to me, although potentially in multiple instruments videos we will want to detect that. 

## Framework!
![Alt Text](https://ar5iv.labs.arxiv.org/html/2311.00968/assets/framework.png)

In order for the model to attend to the order of the sequence of music and video features, we add positional encodings to both the music and video embedding vectors, before feeding it to the encoder and decoder, respectively.

Finally, a post-processing step uses a regression model based on bi-directional Gated Recurrent Units (biGRU) to estimate the note density and loudness based on the video features. This way, the resulting MIDI file dynamically adjusts the rendering of the generated chords, introducing variations in rhythm and volume for a more expressive musical output that better matches the video.


## AMT (Affective Multimodal Transformer)
- AMT comprises of two key components: 
	- a Transformer encoder responsible for capturing video features extracted from the video, 
	- a Transformer decoder that generates chord sequences by intelligently leveraging the context of preceding chords as well as employing a cross-attention mechanism that fuses information from both the musical and visual modalities
- An effective input representation is essential for seamlessly integrating musical and visual information into the Transformer mode
	- For audio, after extracting the chords at every second of the audio tracks, we disassemble them into two essential components: the chord root (e.g., C, D) and the chord type (e.g., minor, major, diminished) (encoded as a one-hot vector)
		- These embeddings are then summed, producing a comprehensive chord embedding vector that encapsulates both the chord root and chord type information.
		- Also there is a key embedding involved here but if this somehow is relevant later in the project see Section 3.1.3 of the paper
		- Embedding of music is the:
			- Positional embedding of the chords embedding which is the concatenation of the key vector, and the summation of the embeddings of the chord root and type.
	- For Video similiar process where video embedding at time t represents the input video vector at a given time t, and $V_{scene}t$, $V_{motion}t$, $V_{emo}t$, and $V_{sem}t$ represent the scene offset vector, motion vector, emotion vector, and semantic vector respectively at a given time t. Finally, we take the positional embedding of the output of a fully connected layer that maps the concatenated video feature vector into a 512-dimensional space.

- In our proposed Affective Multimodel Transformer (AMT) architecture, the total loss is calculated as the weighted sum of the loss related to chords, Lchord, and the loss related to the emotion of the resulting chords, Lemo,
	- First, the Lchord can be calculated as the cross-entropy between the soft targets of the model estimated by the softmax function, and the ground-truth labels
	- For Lemo, see the paper, I think its the cross entropy loss of the emotion embeddings of a video frame and the chord
	- For video frame encodings:
		- The choice of these five emotions (exciting, fearful, tense, sad, relaxing) for mapping to corresponding chords is grounded in the MVED dataset as discussed 3.12 Then, we take the emotion with the highest probability, and use Table [1](https://ar5iv.labs.arxiv.org/html/2311.00968#S4.T1 "Table 1 ‣ 4.1.4 Emotion matching Loss Function ‣ 4.1 Affective Multimodal Transformer ‣ 4 Proposed Video2Music framework ‣ Video2Music: Suitable Music Generation from Videos using an Affective Multimodal Transformer model") to find the matching chord attributes. If an emotion has multiple chord attributes, this vector can be multiple-hot. For instance, if the highest predicted emotion from the video is ‘sad’, the elements in ye​m​o that correspond to the attributes ‘min7’, ‘min’ and ‘sus2’ are set to 1.

- The paper then goes into detail on how the post-processing step creates MIDI files!
	- trained regression models used to jointly predict the extracted loudness and note density from the original audio
		-  These predicted values are subsequently used to select chord arpeggiation patterns and perform MIDI velocity adjustments. This results in music that boasts nuanced rhythmic variations and dynamic intensities, synchronized with the video’s mood and tempo
		- Settled on using Bidirectional gated recurrent units as they performed better than LSTMs, FCNs and some other regression models.

## Evaluation:
 - Metrics for Objective Evaluation
	- To measure the inference accuracy, we adopt H​i​t​s​@​k. This metric allows us to evaluate the generated chord progressions by calculating the ratio of the reference chord presence among the top k candidate chords predicted by the model, where k = 1, 3, and 5. In our case, the reference chord is the ground truth chord from chord progression estimated by chord transcription model on our original audio data. H​i​t​s​@​k is a widely used metric for evaluating rank-based methods and is also employed in music generation to assess the quality of generated results.
		- I.e. in this paper hits@k measures how often the music generated by the model for a video clip appears among the top k best possible matches, reflecting the model's ability to prioritize suitable musical sequences.
-  Metrics for Subjective Evaluation
	- conducted a comprehensive Listening test in which participants were asked to rate 20 music videos in which the music was generated by our system. They were asked to rate a number of questions on a 7-point Likert scale (1 being extremely poor and 7 representing excellent). These questions are aimed to offer insights into the musical quality as well as the music-video alignment:
		- 1. Overall Music Quality (OMQ): How high is the overall quality of the generated music (independently of the video content)?
		- 2. Music-Video Correspondence (MVC): How well are the video and music matched overall?
		- 3. Harmonic Matching (HM): How well does the harmony match the video?
		- 4. Rhythmic Matching (RM): How well does the tempo match the video?
		- 5. Loudness Matching (LM): How well does loudness match the video?

## Further work
> [!important] Secondly, exploring the utilization of music in the waveform presents an intriguing area for future research. By further analyzing the audio waveform itself, we can extract and leverage additional musical attributes, such as timbre, to further enhance the generated music’s fidelity and expressiveness