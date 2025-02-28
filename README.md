# FFCL-SAM

This repository contains the implementation of the FFCL-SAM model proposed in our work:

"SAM-incorporated Forward-Forward Contrastive Learning for Automatic Detection of Breast Cancer Lumpectomy Margin from Intraoperative Specimen Mammography," by Tyler Ward, Braxton McFarland, Md Atik Ahamed, Sahar Nozad, Talal Arshad, Hafsa Nebbache, Jin Chen, Xiaoquin Wang, and Abdullah Imran. In preparation, 2025.

We propose a pretraining strategy, namely Forward-Forward Contrastive Learning (FFCL) with both local and global-level contrastive learning, enabling high-accuracy patch-level classification of radiograph regions into positive and negative margins. The classification outputs were used to generate rough segmentation masks, which were subsequently refined by the Segment Anything Model 2(SAM 2) using prompt-based segmentation techniques.

# Model
![Figure](https://github.com/tbwa233/FFCL-SAM/blob/main/ffcl.png?raw=true)

FFCL training involves multiple stages: first, a backbone architecture is selected as the target model. FFCL then trains the target model with local contrastive learning at each layer (Forward-Forward part) followed by global contrastive learning at the whole network (regular contrastive learning). Finally, the pre-trained model is used to perform the downstream classification task (positive/negative margins) using backpropagation.

![Figure](https://github.com/tbwa233/FFCL-SAM/blob/main/ffcl-sam_new3.png?raw=true)

Patient radiographs is annotated with pixel-level positive and negative tumors. Patches extracted from the segmented regions, are used to train the FFCL-pretrained model to detect positive margins. A rough binary mask is then reconstructed leveraging the class label predictions. Two prompts, p1, which is a bounding box encompassing the coarse mask data, and p2, which is the coarse mask itself, are generated from the coarse mask and used as input to the SAM 2 model. p1 is used to produce the first mask prediction, m1, and p2 is used to refine the mask into the final segmentation mask, m2.
