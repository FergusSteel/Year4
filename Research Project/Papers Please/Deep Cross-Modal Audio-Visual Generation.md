[Link to Original Paper](https://ar5iv.labs.arxiv.org/html/1704.08292)

- Uses a discriminative min-max GAN for both the Image to Sound and Sound to Image models i.e. for the generator, given an image and a sound encoding vector, and a random noise vector which it then generates a sound spectogram as close to the target distribution as possible which the discrimintaor then tries to idenitfy whether or not this comes from the original distribution or not (i.e outputs a probability)
	- Generator gets better at foolign discriminator over time and the discriminator gets better at predicting the correct distribution over time.
- The models are trained in mulltiple orientiations:
	- over multiple instruments
	- over different poses (i.e. more fine grained, instrument focused)