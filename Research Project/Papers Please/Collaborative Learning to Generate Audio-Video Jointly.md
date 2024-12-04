GANs have been shown to be able to generate a modality conditioned on another

"However, so far, the task of multi-modal generation of data, specifically for audio and videos both, has not been sufficiently well-explored." - good quote should go in the generative section of lit review

"we are able to generate naturalistic samples of video and audio data by the joint correlated generation of audio and video modalities"

Discriminators that ensure the generated audio, video and joint output are indistinguishable from reality.

"In the real world, different modalities of the same data are highly correlated. " - bars

These methods consider the single modality generation problem either in the form of unconditional generation or conditional generation - Cross model generation focuses on the latter form of conditional generation where the generation of the missing modality is conditioned solely on the other modality.

"One of the major drawbacks of these methods is that they do not consider that audio and video streams of the same data are highly correlated and could be generated jointly both benefiting each other"

Recently, there have been a few works [1, 2] that aim to solve cross-modal generation but are only focus on images rather than sequences (videos)

Discusses GANs and other generative models (inc. wavenet)

Discusses laignment issues (well it doesnt it just references 9 papers)

Referenes Foley music.

**Method**
Consists of Audio Generation, Video Generation and A Joint Discriminator Module

Audio Generator - parameterised by model weights and generates audio from a noise vector.
Generator module uses 1-D convolutional layers (bit lame) Focuses a lot on frequency patterns present in music. Uses a GAN for this, focused on a discriminator and a generator you know

"Our video generation component takes inspiration from the idea of decomposing videos into a separate motion and content part [8]. Our video clips vn = [I1, . . . , In] are composed of N frames. The temporal relationship between the video frames is obtained by modeling the latent space vector Zn. The content of the video clips is encapsulated by introducing a context vector ZC and is combined with every motion vector. Each input to the video generator is a combination of the latent motion vector and the latent content vector"

The marginal distributions are represented for audio and video as p(a) and p(v). The joint distribution of audio and video is denoted by p(a, v). To jointly learn the audio-video generation, we use two joint discriminators, inspired by [32].

