Huang et al. [[2018](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib34)] proposed a Music Transformer to generate Chorales as well as classical piano pieces, of length 2,000 tokens. To the best of our knowledge, it is the first Transformer-based model developed to generate music. Other models soon followed, for instance, Payne [[2019](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib49)] presented MuseNet, a GPT-2-based Sparse Transformer model, that can generate music pieces that are up to 4 minutes long with 10 different instruments and various styles. The Sparse Transformer does not use relative attention, but instead implements full attention over a total of 4,096 tokens. This makes it is better suited for capturing long-term structure. Both MuseNet and Music Transformer use decoder-only Transformers. In both of these models, the teacher-forcing algorithm during training. Both of these systems also use a cross-entropy loss, which is not a real measure of musical quality. Zhang [[2020](https://ar5iv.labs.arxiv.org/html/2311.00968#bib.bib72)] attempted to solve this issue by proposing an Adversarial Transformer that produces high quality classical guitar music. In the adversarial Transformer model, the self-attention architecture is combined with generative adversarial learning, whereby the generator is a decoder-only Transformer, and the discriminator is an encoder-only Transformer. In addition, adversarial objectives are used as a strong regularization for enforcing the Transformer to focus on learning the local and global structures.

From [[Video2Music - Suitable Music Generation from Videos using an Affective Multimodal Transformer model]]