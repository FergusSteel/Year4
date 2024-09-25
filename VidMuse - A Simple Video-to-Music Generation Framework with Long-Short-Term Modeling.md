## https://arxiv.org/pdf/2406.04321v1

Contributions include the:
- A large scale video-to-music dataset
- Simple but effective method VidMuse for video to music generation
	- The proposed method integrates both local and global cues in the video, enabling the generation of high-fidelity music tracks that are not only musically coherent but also semantically aligned with the video content
- Benchmark several state-of-the-art works against our method on V2M-bench with a series of subjective and objective metrics for thorough evaluation

In my research I would likely want to achieve similar end goals, a dataset, a music generation pipelines pre-conditioned only on the performance of a piece of music.


Ok I have a plan, as a jumping off point, im going to recreate this network, but train and then precondition the generation of music only on performance videos (using SOLOs dataset)

Could also try using the tracked skeleton data as another modality? So we have semantic embeddings and physical movements. (https://arxiv.org/abs/2012.03478 been done, but not with the semantic embeddings from video data)

What I did this morning
Read 1 paper from list
Email Paul
Start time 9:30am

- Papers i found today:
	- META MusicGen [Simple and Controllable Music Generation](https://arxiv.org/pdf/2306.05284)
	- Kun Su - the goat? [Google Scholar](https://scholar.google.com/citations?user=y52GkywAAAAJ&hl=en&oi=sra)
		- MNet [Unsupervised Generation of Music from Body Movements](https://arxiv.org/pdf/2012.03478)
		- Reconstructing Audio from Silent Piano Performance Videos [Link](https://proceedings.neurips.cc/paper_files/paper/2020/hash/227f6afd3b7f89b96c4bb91f95d50f6d-Abstract.html)
		- [[VidMuse - A Simple Video-to-Music Generation Framework with Long-Short-Term Modeling]] !!!!!!!!

Potentially new research question - focusing more on the semantic matching of audio rather than focusing on emotion of music (although this could also be a part of it)?

Write SAS presentation script
Create Example Network Diagram
	From this diagram come up with 2 ways to evaluate it against baseline