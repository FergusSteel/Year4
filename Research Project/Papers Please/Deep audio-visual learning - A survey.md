**Audio-visual generation** tries to synthesize the other modality based on one of them, which is different from the above two tasks leveraging both audio and visual modalities as inputs. Thats me thats me.

Due to the difference between audio and visual modalities, the potential correlation between them is nonetheless difficult for machines to discover. Generating sound from a visual signal or vice versa, therefore, becomes a challenging task. bollocks

Zhou et al. [81] designed an end-to-end model. It was structured as a video encoder and a sound generator to learn the mapping from video frames to sounds. Afterwards, the network leveraged a hierarchical RNN [83] for sound generation - this seems outdated.. Although - They demonstrated that this model could learn the correlation between sound and visual input for various scenes and object interactions

Audio-to-Video harder as temporal consistency is required between generated frames.

Hao et al. [86] combined the respective networks into one network by considering a cross-modality cyclic generative adversarial network (CMCGAN) for the cross-modality visual-audio mutual generation task... **In reference to [[Deep Cross-Modal Audio-Visual Generation]]** **should read**


Alemi et al. [89] proposed a real-time GrooveNet based on conditional restricted Boltzmann machines and recurrent neural networks to generate dance movements from music. READ "*O. Alemi, J. Franc¸oise, and P. Pasquier, “Groovenet: Realtime music-driven dance movement generation using artificial neural networks,” networks, vol. 8, no. 17, p. 26, 2017.*"


SHITE Shlizerman et al. [91] "The latter was further used as agents to generate body dynamics. The key idea was to create an animation from the audio that was similar to the action of a pianist or a violinist. In summary, the entire process generated a video of artists’ performance corresponding to input audio."

E. Shlizerman, L. Dery, H. Schoen, and I. KemelmacherShlizerman, “Audio to body dynamics,” in Proc. CVPR, 2018.

Zhou et al. need to look at this guy? if its the same guy his name pops up a lot.

Most recently, to discover the high-level correlation between audio and video, Zhu et al. [73] proposed a mutual information approximation to approximate mutual information between modalities READ

"Additionally, the quality of data representation usually determines the success of machine learning algorithms"

Discusses task of AVC (audio-visual coherence) most simular visual area to current audio.

In contrast to previous AVC task-based solutions, Korbar et al. [13] introduced another proxy task called audio-visual time synchronization (AVTS) that further considered whether a given audio sample and video clip were “synchronized” or “not synchronized.”

https://www.cs.rochester.edu/~cxu22/d/vagan/

"Audio-visual learning (AVL) is a foundation of the multimodality problem that integrates the two most important perceptions of our daily life."

![[Pasted image 20241021191206.png]]