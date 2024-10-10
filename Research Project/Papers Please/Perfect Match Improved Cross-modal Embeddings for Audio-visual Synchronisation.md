
- Investigates self-supervised learning for synchronisation of audio and video features, therefore synchronising the audio-visual embeddings in the temporal domain
- SyncNet (CNNs) can be used for learning joint embeddings of speech video and speech audio. SyncNets features can be used to achieve dynamic temporal alignment


- Training Methodology of Baselines:
	- Baseline - SyncNet. 
		- The original SyncNet [4] is trained with a contrastive loss, which is designed to maximise the distance between features for non-matching pairs of inputs, and minimise the distance for matching pairs. The audio and the video for non-matching pairs are sampled from the same face track, but from different points in time. The method requires manual tuning of the margin hyper-parameter. 
	- Baseline - AVE-Net.
		- The Audio-Visual Embedding Network (AVE-Net) [6], designed for cross-modal retrieval, also takes the outputs from the audio and the video networks as inputs. The input vectors are L2 normalised, then the Euclidean distance between the two normalised embeddings are computed, before being passed through a fully-connected layer and a softmax layer. The fully-connected layer essentially learns the threshold on the distance above which the features are deemed not to correspond.

- The task is to determine the correct synchronisation within a ±15 frame window, and the synchronisation is determined to be correct if the predicted offset is within 1 video frame of the ground trut

How do we define the receptive field that the model is trying to match in audio visual translation - how many frames of video, how many seconds/frames of audio?