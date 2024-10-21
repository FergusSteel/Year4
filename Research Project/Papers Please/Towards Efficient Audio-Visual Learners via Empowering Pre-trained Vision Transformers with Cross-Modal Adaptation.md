Proposes the use of pre-trained ViTs for Audio-visual domain. A Spatio-Temporal-Global Cross-Modal Adapataion to equip frozen ViTs with capability for learning Audio-Visual Represnetaitons.

> [!quote] Our STGCMA presents a meaningful finding that only leveraging the shared pre-trained image model with inserted lightweight adapters is enough for spatial-temporal modeling and feature interaction of audio-visual modality

Audio-visual learning emerges as a flourishing field to simultaneously learn from both visual and auditory modalities, enabling the intelligent systems to imitate human perception for hearing and seeing the surrounding environment [50]. Deep audio-visual learning: A survey

Uses Parameter efficient transfer learnig (PETL) that updates newly inserted parameters while keeping pre-trained models frozen

Lin et al. [25] proposed LAVISH to adapt the frozen pre-trained ViTs into audio-visual tasks, where the inserted adapters only perform the interaction between audio and visual features while neglecting the spatial-temporal adaptation of modality-specific signals
```
Yan-Bo Lin, Yi-Lin Sung, Jie Lei, Mohit Bansal, and Gedas Bertasius. Vision transformers are parameter-efficient audiovisual learners. In Proceedings of the IEEE/CVF Conference
```
READ ^^^

However this is different as STG-CMA directly adapts the frozen ViTs parameters to do the spatial temporal reasoning across both modalities (while reducing the tunable parameters)

"The audio-visual adapter (AV-Adapter) is proposed to achieve the interaction between audio and visual modalities, which consists of two parallelly connected vanilla adapters and the cross-attention interaction module (CAIM) in between" see fig 1 of paper for more detail

I think this paper is great, it is a way to utilise pretrained ViTs in the audio-visual domain, and is likely something I want to leverage in my project depending on the complexity, I dont understand the inner complexities yet but can learn more through reading other papers of this kind.