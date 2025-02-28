# FFCL-SAM

This repository contains the implementation of the FFCL-SAM model proposed in our work:

"SAM-incorporated Forward-Forward Contrastive Learning for Automatic Detection of Breast Cancer Lumpectomy Margin from Intraoperative Specimen Mammography," by Tyler Ward, Braxton McFarland, Md Atik Ahamed, Sahar Nozad, Talal Arshad, Hafsa Nebbache, Jin Chen, Xiaoquin Wang, and Abdullah Imran. In preparation, 2025.

We propose a pretraining strategy, namely Forward-Forward Contrastive Learning (FFCL) with both local and global-level contrastive learning, enabling high-accuracy patch-level classification of radiograph regions into positive and negative margins. The classification outputs were used to generate rough segmentation masks, which were subsequently refined by the Segment Anything Model 2(SAM 2) using prompt-based segmentation techniques.
