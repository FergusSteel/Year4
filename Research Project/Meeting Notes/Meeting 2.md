In person 06/10/24

## Agenda
Discuss Model Architecture:
1. **Audio Features**:
    - **Input**: Audio data from performance is transformed into spectrograms, which represent the frequency content of the audio over time.
    - **Purpose**: These spectrograms act as the model's target or output during training. In the final application, the model will generate spectrograms that can be converted back into audio.
2. **Visual Features**:
    - **Input**: Visual frames extracted from video sequences are fed into a pre-trained visual transformer or CNN. The output of this network is a set of embeddings that encode high-level visual information and can learn correlation between that and spectograms.
    - **Purpose**: These embeddings capture the static features of the video and form a core input channel for the cross-modal translation model. Important for understanding the semantic 
3. **Optical Flow Fields**:
    - **Input**: Optical flow is computed from video frames to capture the motion in the scene. This feature represents the dynamic component of the video, indicating the direction and speed of movement between frames.
    - **Purpose**: The optical flow fields provide temporal motion cues that are useful for understanding the dynamics of the scene. These can correlate with changes in tempo, rhythm, or emotional expression in the audio domain.

Motivation:
So from a video you could generate music, then from music and maybe a prior image, we could generate the optical flow fields and reconstruct the performance.

## Then what?
- How can we combine optical flow fields, into a cross modal translation model and leverage their temporal modelling in reconstructing the audio of a video. And then the other way, can we learn likely optical flow fields from audio

COSE Helpdesk for computer access
One page of the structure of the project
Two way model ideas, REMEMBER THE using images as priors!

That marketable idea, is the two-way translation of reconstructing the music, and also giving the model a prior image and generating a visualisation