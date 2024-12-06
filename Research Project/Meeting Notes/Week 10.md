
![[Pasted image 20241204143255.png]]

- Corrections:
	- December 1-7 
		- Focus on Input Streams and Preprocessing of Data, loading and standardizing data
			- MusicGen Tokenizer bit is fine I do actually have to do it at some point lmao
	- December 8-14
		- Embedding validation, use a UNET to reconstruct Video and Audio from embedded representations to validate entropy
		- Optical Flow Decisions
	- December 15-21
		- Focus on temporal alignment
		- Try out cross-attention, or more simple temporal mechansims (need to do more reading on this stuff tbf)
	- December 22-31
		- Try get everything integrated (obviously not trained or anything, but you know have the two gen models take some combined/correlated cross-modal input)

---


![[Pasted image 20241204143153.png]]
- Corrections
	- Ok basiscally every "phase" and sub-phase is a lie

1. Finalise codebase for further development
2. Optimise and validate temporal Alignment (make this shorter)
3. NOW train latent space,
4. Then finetune generative models
5. Optimisation
6. Quantitative Evaluation
7. Qualitative Evaulations
8. Finalising thesis and submission

---

![[Pasted image 20241204143211.png]]

shes a beaut tbh

---

https://github.com/FergusSteel/Music-CMV2M/tree/main
 fuck me i got so much shit to od

---

For feature validation use UNET for input reconstruction to validate system has emebedde the relevant entropy of inputs - ifthis doesnt work somethings wrong.

Explcitly the actual rate of change in the signals is correlated to the change in the visual domain, we are learning this pattern/texture of audio features

Audio events are by definition correlated to video features more than the audio's changing frequencies. 

Consider LSTMs as a minimal fall back system

For next week show feature extraction + validation.