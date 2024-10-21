## URMP, 
I believe this is likely the best dataset for the job but its not large enough to train a full generative model, so either we would need to use a pretrained music generation tool and investigate the effect of adding the embeddings of videos into the generative process or get more data.

SUB URMP https://www.cs.rochester.edu/~cxu22/d/vagan/
## Solos
Again would need to be transcribed but fortunately categories match the URMP dataset and there is a lot more data. 
Labelled with skeleton tracking, likely not useful.
## Sound-of-Pixels (MUSIC dataset)
Unlabelled collection of musical performances that would need to be labelled and pre-processed in several ways. Including likely transcribed which is inevitably going to be noisy, however if we are just using MIDI as the audio modality input, this may be ok.