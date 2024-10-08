![[Pasted image 20241008124055.png]] 
>[!quote] The most fundamental challenge in multimodal learning is obtaining a compact and modalityinvariant representation that integrates different modalities without label information, which we call a shared representation

- Different modalities contain very different information about an object, in terms of structure and the quantity of useful data. So we must consider the relationship between modalities.
- A "Good Representation" is one which can be used for multiple tasks, and fulfill the following two criteria:
	- 1. The shared representation must be such that similarity in the representation space implies similarity of the corresponding “concepts”. 
	- 2. The shared representation must be easy to obtain even in the absence of some modalities.

## Joint Models vs Coordinated Models:
### Joint Models:

- **Overview**: Joint models aim to model all modalities together within a single shared latent space. In this approach, the model learns a joint distribution over all input modalities, which allows it to generate or understand multiple modalities simultaneously.
    
- **Characteristics**:
    - The different modalities (e.g., text, image, audio) are **fused together** in a common representation space.
    - These models assume that the modalities are strongly correlated and that learning their joint distribution can capture the interactions between the modalities.
    - **Training**: During training, all modalities are presented together, and the model is trained to understand and generate these modalities in conjunction.
    - **Applications**: Suitable for tasks that inherently require tight integration between the modalities (e.g., generating an image from a text description or vice versa).
- **Advantages**:
    - Direct modeling of the interactions between modalities can lead to richer and more semantically meaningful shared representations.
    - The unified latent space enables cross-modal generation (e.g., generating one modality from another).
- **Challenges**:
    - It can be difficult to model highly heterogeneous modalities together in a single space.
    - Requires all modalities to be present during training, which can be a limitation in some scenarios where data for all modalities isn’t available.

### Coordinated Models:

- **Overview**: Coordinated models, in contrast, model each modality separately but encourage coordination between them. Each modality has its own latent representation, but these representations are linked in some way to ensure that they are semantically aligned.
    
- **Characteristics**:
    - Rather than fusing the modalities into a single latent space, these models **maintain separate latent spaces** for each modality.
    - The model learns to align these modality-specific representations through certain coordination mechanisms (e.g., a shared loss function or regularization techniques that ensure the separate spaces are correlated).
    - **Training**: Each modality can be trained independently, with some mechanism (e.g., contrastive learning, shared priors) ensuring alignment across modalities.
- **Advantages**:
    - Offers flexibility in handling missing modalities since each modality is modeled separately.
    - Easier to handle situations where modalities differ significantly (e.g., audio vs. image).
- **Challenges**:
    - Maintaining alignment between different modality-specific representations can be tricky and may require complex loss functions or regularization techniques.
    - The coordination mechanism must be strong enough to ensure that the separate latent spaces capture the relationships between the modalities.

### Summary of Differences:
- **Representation**: Joint models use a shared latent space for all modalities, while coordinated models use separate latent spaces with alignment mechanisms.
- **Interaction**: Joint models capture modality interactions explicitly within the same representation, while coordinated models focus on ensuring that different modalities are semantically aligned but independent in terms of representation.
- **Training**: Joint models require all modalities to be available for training, while coordinated models allow for more flexibility, including missing modalities during training.



# Takeaways:
- Will likely need to be a joint model if i end up using shared representations, as the temporal aspect is super important.
- 